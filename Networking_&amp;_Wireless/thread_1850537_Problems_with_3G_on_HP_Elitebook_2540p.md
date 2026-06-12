---
title: "Problems with 3G on HP Elitebook 2540p"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by kirby_82 on 2011-09-26
Hello! 
First of all I would like to say that I have searched the forums, googled the problem and also apologize for a possible duplucate post. If its a duplicate please just point me to the other thread. 

So, I recently bought a HP Elitebook 2540p and installed 11.04 (x64) on it. Everything went fine but when trying to access the 3G modem I ran into some problems.  After some research I noticed apperently the modem needed some additional firmware. 
I found a guide: [https://nowhere.dk/articles/ubuntu-natty-making-a-gobi-2000-wireless-modem-work](https://nowhere.dk/articles/ubuntu-natty-making-a-gobi-2000-wireless-modem-work) and followed it but for some reason the card wont appear when running a lsusb.  

$lsusb Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 001 Device 005: ID 04f2:b163 Chicony Electronics Co., Ltd  
Bus 001 Device 004: ID 138a:0007 DigitalPersona, Inc  
Bus 001 Device 003: ID 03f0:231d Hewlett-Packard  
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

Then I rebooted into Windows to turn this thing on. Opened up HP Connections Manager and activated the 3G connection, even connected it to the internet and made sure it worked. Rebooted again (Start -> Restart) and went into Ubuntu. Still no sign of the modem.  

I have added qcserial to /etc/modules and  dmesg doesnt really show anything of interest: 
[    5.674336] usbcore: registered new interface driver usbserial 
[ 5.674351] USB Serial support registered for generic 
[    5.674427] usbcore: registered new interface driver usbserial_generic 
[    5.674429] usbserial: USB Serial Driver core 
[    5.687562] USB Serial support registered for Qualcomm USB modem 
[    5.687627] usbcore: registered new interface driver qcserial 

Thats as far as I've got... As far as I understand this the problem lies within the problem to see the modem using lsusb, am I correct? I
s there another way to force the modem to activate cause what it seems to me is that the modem gets a power reset when I'm rebooting from Windows to Ubuntu.  

Please advice.  

Regards,  

Kirby

---

### Post by pdc on 2011-09-26
oh dear; the famous gobi 2000;

there has been a recent thread on opensuse

[http://forums.opensuse.org/english/get-technical-help-here/wireless/464915-gobi2000-does-not-answer.html](http://forums.opensuse.org/english/get-technical-help-here/wireless/464915-gobi2000-does-not-answer.html)

and quite an experienced user finally felt he made progress by using this page

[http://www.thinkwiki.org/wiki/Qualcomm_Gobi_2000](http://www.thinkwiki.org/wiki/Qualcomm_Gobi_2000)

tell us if you have already seen and done this; this link points to firmware that seems to be a lynchpin for this device

you can subscribe to a thread; so email tells you when there is a reply; you might find that helpful

I don't know if there is a linux, gobi 2000, helpers group !!

---

### Post by kirby_82 on 2011-09-28
Thanks for the reply. Yeah, I did notice that it where alot of struggling to get this 3G modem to work but I'm not ready to give up just yet.
Last night I followed the previously mentioned guide (nowhere.dk) once more and restarted udev instead of the rebooting. Suddenly the hardware is now visible again and its bound to ttyUSB0 according to dmesg.
The hardware also shows up after a reboot :)
Still doesnt show up in network manager tho and I'm thinking about to see if I can communicate with the device at all. So is there a way to verify that the ttyUSB0 is working correctly?
Just to confirm that the device have been correctly bound?
Thanks in advance.

Regards

---

### Post by pdc on 2011-09-29
when you say 

"doesn't show up in Network Manager'.....................

......... have you edited Network Manager to create a profile of a provider you want to dial to ............

eg I have appended a trial setup for AT&T

if you get ttyUSB0 you should be good to go .......

and the lsusb ID should have changed too.......from what the posts say......

---

### Post by kirby_82 on 2011-10-08
Thanks for the reply. Yes, I did try create a generic connection like the one you mentioned (apart from I tried 3 in sweden instead) and even marked it auto connect without any established connection (as far as I know network manager never recognised the tty as a modem).

However, it seems I'm back to squared one cause now the device isnt showing at all again in lsusb. I've tried alot of different options and guides but still stuck. Of course I didnt think of writing the vendor id and such down so I'm now blind again of where to find it...

Any suggestions?

---

