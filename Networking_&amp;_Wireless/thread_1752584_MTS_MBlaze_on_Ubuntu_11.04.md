---
title: "MTS MBlaze on Ubuntu 11.04"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by reachpritam on 2011-05-08
Hi,

I have installed the new Ubuntu 11.04 (32 bit ) on my asus betbook.

I have followed the steps 

1. Created a wvdial.conf file as below[INDENT][Dialer cdma]
Stupid Mode = 1
Inherits = Modem0
Password = mts
Username = [EMAIL="internet@internet.mtsindia.in"]internet@internet.mtsindia.in[/EMAIL]
Phone = #777
 [Modem0]
Init1 = ATZ
SetVolume = 0
Modem = /dev/**ttyUSB0**
Baud = 115200
FlowControl = Hardware (CRTSCTS)
Dial Command = ATDT


[/INDENT]2. In Network connections created a new setup for mobile Broadband for MTS with user and pwd as mentioned in step 1 and the PPP configure methods as PAP and CHAP.


3. Donwloaded and installed  the packages - usb-modeswitch-data and usb-modeswitch.


4. Now when I connect my modem and use the command 

sudo wvdial cdma ... i get the below error message


--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)



The man pppd says that exit status 19 is for "The init script failed"




Please help urgently to resolve this issue


Cheers
Pritam

---

