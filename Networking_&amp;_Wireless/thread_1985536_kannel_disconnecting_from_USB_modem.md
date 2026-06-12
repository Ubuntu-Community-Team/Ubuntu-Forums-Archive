---
title: "kannel disconnecting from USB modem"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by pakporume on 2012-05-23
Hi
I am trying to set up an sms gateway using kannel and a GSM  modem I have installed kannel and tested it. it works with the fake SMSC but when I try modem it gives me the following code(NOTE: i am using ubuntu 12.4)
____________________________________________________________________________________
  peter@peter:~$ sudo /usr/sbin/bearerbox -v 1 /etc/kannel/modem.conf
[sudo] password for peter: 
2012-05-23 14:12:09 [3946] [0] INFO: Debug_lvl = 1, log_file = <none>, log_lvl = 0
2012-05-23 14:12:09 [3946] [0] WARNING: DLR: using default 'internal' for storage type.
2012-05-23 14:12:09 [3946] [0] INFO: DLR using storage type: internal
2012-05-23 14:12:09 [3946] [0] INFO: Added logfile `/tmp/kannel.log' with level `0'.
2012-05-23 14:12:09 [3946] [0] INFO: Started access logfile `/tmp/access.log'.
2012-05-23 14:12:09 [3946] [0] WARNING: 'store-file' option deprecated, please use 'store-location' and 'store-type' instead.
2012-05-23 14:12:09 [3946] [0] INFO: HTTP: Opening server at port 2072.
2012-05-23 14:12:09 [3946] [0] ERROR: bind failed
2012-05-23 14:12:09 [3946] [0] ERROR: System error 98: Address already in use
2012-05-23 14:12:09 [3946] [0] INFO: BOXC: 'smsbox-max-pending' not set, using default (100).
2012-05-23 14:12:09 [3946] [0] INFO: Set SMS resend frequency to 60 seconds.
2012-05-23 14:12:09 [3946] [0] INFO: SMS resend retry set to unlimited.
2012-05-23 14:12:09 [3946] [0] INFO: DLR rerouting for smsc id <(null)> disabled.
2012-05-23 14:12:09 [3946] [0] INFO: AT2[/dev/ttyUSB0]: configuration doesn't show modemtype. will autodetect
2012-05-23 14:12:09 [3946] [0] INFO: ----------------------------------------
2012-05-23 14:12:09 [3946] [0] INFO: Kannel bearerbox II version 1.4.3 starting
2012-05-23 14:12:09 [3946] [0] INFO: Loading store file `kannel.store'
2012-05-23 14:12:09 [3946] [0] INFO: Store-file size 1215, starting to unpack
2012-05-23 14:12:09 [3946] [0] INFO: Retrieved 5 messages, non-acknowledged messages: 5
2012-05-23 14:12:09 [3946] [0] INFO: MAIN: Start-up done, entering mainloop
2012-05-23 14:12:09 [3946] [4] INFO: AT2[/dev/ttyUSB0]: opening device
2012-05-23 14:12:09 [3946] [4] ERROR: AT2[/dev/ttyUSB0]: open failed! ERRNO=2
2012-05-23 14:12:09 [3946] [4] ERROR: System error 2: No such file or directory
2012-05-23 14:12:09 [3946] [4] INFO: AT2[/dev/ttyUSB0]: opening device
2012-05-23 14:12:09 [3946] [4] ERROR: AT2[/dev/ttyUSB0]: open failed! ERRNO=2
2012-05-23 14:12:09 [3946] [4] ERROR: System error 2: No such file or directory
2012-05-23 14:12:09 [3946] [4] INFO: AT2[/dev/ttyUSB0]: opening device
2012-05-23 14:12:09 [3946] [4] ERROR: AT2[/dev/ttyUSB0]: open failed! ERRNO=2
2012-05-23 14:12:09 [3946] [4] ERROR: System error 2: No such file or directory
2012-05-23 14:12:09 [3946] [4] INFO: AT2[/dev/ttyUSB0]: opening device
2012-05-23 14:12:09 [3946] [4] ERROR: AT2[/dev/ttyUSB0]: open failed! ERRNO=2
2012-05-23 14:12:09 [3946] [4] ERROR: System error 2: No such file or directory
2012-05-23 14:12:09 [3946] [4] INFO: AT2[/dev/ttyUSB0]: opening device
2012-05-23 14:12:09 [3946] [4] ERROR: AT2[/dev/ttyUSB0]: open failed! ERRNO=2
2012-05-23 14:12:09 [3946] [4] ERROR: System error 2: No such file or directory
2012-05-23 14:12:09 [3946] [4] INFO: AT2[/dev/ttyUSB0]: cannot detect speed
2012-05-23 14:12:09 [3946] [4] ERROR: AT2[/dev/ttyUSB0]: Couldn't connect (retrying in 10 seconds).
2012-05-23 14:12:09 [3946] [4] INFO: AT2[/dev/ttyUSB0]: opening device
2012-05-23 14:12:09 [3946] [4] ERROR: AT2[/dev/ttyUSB0]: open failed! ERRNO=2
2012-05-23 14:12:09 [3946] [4] ERROR: System error 2: No such file or directory
2012-05-23 14:12:09 [3946] [4] INFO: AT2[/dev/ttyUSB0]: opening device
2012-05-23 14:12:09 [3946] [4] ERROR: AT2[/dev/ttyUSB0]: open failed! ERRNO=2
2012-05-23 14:12:09 [3946] [4] ERROR: System error 2: No such file or directory
2012-05-23 14:12:09 [3946] [4] INFO: AT2[/dev/ttyUSB0]: opening device
2012-05-23 14:12:09 [3946] [4] ERROR: AT2[/dev/ttyUSB0]: open failed! ERRNO=2
2012-05-23 14:12:09 [3946] [4] ERROR: System error 2: No such file or directory
2012-05-23 14:12:09 [3946] [4] INFO: AT2[/dev/ttyUSB0]: opening device
2012-05-23 14:12:09 [3946] [4] ERROR: AT2[/dev/ttyUSB0]: open failed! ERRNO=2
2012-05-23 14:12:09 [3946] [4] ERROR: System error 2: No such file or directory
2012-05-23 14:12:09 [3946] [4] INFO: AT2[/dev/ttyUSB0]: opening device
2012-05-23 14:12:09 [3946] [4] ERROR: AT2[/dev/ttyUSB0]: open failed! ERRNO=2
2012-05-23 14:12:09 [3946] [4] ERROR: System error 2: No such file or directory
2012-05-23 14:12:09 [3946] [4] INFO: AT2[/dev/ttyUSB0]: cannot detect speed
2012-05-23 14:12:09 [3946] [4] ERROR: AT2[/dev/ttyUSB0]: Couldn't connect (retrying in 10 seconds).
2012-05-23 14:12:09 [3946] [3] ERROR: bind failed
2012-05-23 14:12:09 [3946] [3] ERROR: System error 98: Address already in use
2012-05-23 14:12:09 [3946] [3] PANIC: Could not open smsbox port 2073
2012-05-23 14:12:09 [3946] [3] PANIC: /usr/sbin/bearerbox(gw_panic+0x17b) [0x47fdab]
2012-05-23 14:12:09 [3946] [3] PANIC: /usr/sbin/bearerbox() [0x410e28]
2012-05-23 14:12:09 [3946] [3] PANIC: /usr/sbin/bearerbox() [0x4779be]
2012-05-23 14:12:09 [3946] [3] PANIC: /lib/x86_64-linux-gnu/libpthread.so.0(+0x7e9a) [0x7f98ed6dfe9a]
2012-05-23 14:12:09 [3946] [3] PANIC: /lib/x86_64-linux-gnu/libc.so.6(clone+0x6d) [0x7f98ec2a24bd]
peter@peter-HP-Pavilion-dv4-Notebook-PC:~$ sudo /usr/sbin/bearerbox -v 1 /etc/kannel/modem.conf
2012-05-23 14:12:48 [4013] [0] INFO: Debug_lvl = 1, log_file = <none>, log_lvl = 0
2012-05-23 14:12:48 [4013] [0] WARNING: DLR: using default 'internal' for storage type.
2012-05-23 14:12:48 [4013] [0] INFO: DLR using storage type: internal
2012-05-23 14:12:48 [4013] [0] INFO: Added logfile `/tmp/kannel.log' with level `0'.
2012-05-23 14:12:48 [4013] [0] INFO: Started access logfile `/tmp/access.log'.
2012-05-23 14:12:48 [4013] [0] WARNING: 'store-file' option deprecated, please use 'store-location' and 'store-type' instead.
2012-05-23 14:12:48 [4013] [0] INFO: HTTP: Opening server at port 2072.
2012-05-23 14:12:48 [4013] [0] INFO: BOXC: 'smsbox-max-pending' not set, using default (100).
2012-05-23 14:12:48 [4013] [0] INFO: Set SMS resend frequency to 60 seconds.
2012-05-23 14:12:48 [4013] [0] INFO: SMS resend retry set to unlimited.
2012-05-23 14:12:48 [4013] [0] INFO: DLR rerouting for smsc id <(null)> disabled.
2012-05-23 14:12:48 [4013] [0] INFO: AT2[/dev/ttyUSB0]: configuration doesn't show modemtype. will autodetect
2012-05-23 14:12:48 [4013] [0] INFO: ----------------------------------------
2012-05-23 14:12:48 [4013] [0] INFO: Kannel bearerbox II version 1.4.3 starting
2012-05-23 14:12:48 [4013] [0] INFO: Loading store file `kannel.store'
2012-05-23 14:12:48 [4013] [0] INFO: Store-file size 1215, starting to unpack
2012-05-23 14:12:48 [4013] [0] INFO: Retrieved 5 messages, non-acknowledged messages: 5
2012-05-23 14:12:48 [4013] [0] INFO: MAIN: Start-up done, entering mainloop
2012-05-23 14:12:48 [4013] [6] INFO: AT2[/dev/ttyUSB0]: opening device
2012-05-23 14:12:49 [4013] [6] INFO: AT2[/dev/ttyUSB0]: speed set to 115200
2012-05-23 14:12:57 [4013] [6] INFO: AT2[/dev/ttyUSB0]: Closing device
2012-05-23 14:12:57 [4013] [6] INFO: AT2[/dev/ttyUSB0]: detect speed is 115200
2012-05-23 14:12:57 [4013] [6] INFO: AT2[/dev/ttyUSB0]: opening device
2012-05-23 14:12:58 [4013] [6] INFO: AT2[/dev/ttyUSB0]: speed set to 115200
2012-05-23 14:13:04 [4013] [6] ERROR: AT2[/dev/ttyUSB0]: Couldn't connect (retrying in 10 seconds).

This is the modem.conf file
_______________________________________________________________________________
group = core
admin-port = 2072
smsbox-port = 2073
admin-password = 'shilo'
#status-password = foo
#admin-deny-ip = ""
#admin-allow-ip = ""
log-file = "/tmp/kannel.log"
log-level = 0
box-deny-ip = "*.*.*.*"
box-allow-ip = "*.*.*.*"
#unified-prefix = "+358,00358,0;+,00"
access-log = "/tmp/access.log"
store-file = "kannel.store"
#ssl-server-cert-file = "cert.pem"
#ssl-server-key-file = "key.pem"
#ssl-certkey-file = "mycertandprivkeyfile.pem"

group = smsc
smsc = at
modemtype = auto
device = /dev/ttyUSB0
speed = 0
sms-center = 00234803000000
my-number = 002348168155769

group = smsbox
bearerbox-host = 127.0.0.1 
sendsms-port = 9003
global-sender = 9003
#sendsms-chars = "0123456789 +-"
log-file = "/tmp/smsbox.log"
log-level = 0
access-log = "/tmp/access.log"

group = sendsms-user
username = shilo
password = shilo
#user-deny-ip = ""
#user-allow-ip = ""



group = sms-service
keyword = nop
text = "You asked nothing and I did it!"

group = sms-service
keyword = default
text = "No service specified"
______________________________________________________________________

The modem /dev/ttyUSB0 is set correctly. I just call the bearer box with this command  "sudo /usr/sbin/bearerbox -v 1 /etc/kannel/modem.conf ".
Please help.
Could it be the PPP dialer if so how do I fix it? Thanks

---

