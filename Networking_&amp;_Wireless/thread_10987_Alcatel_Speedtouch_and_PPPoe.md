---
title: "Alcatel Speedtouch and PPPoe"
date: 2005-01-13
forum: Networking &amp; Wireless
---

### Post by Q00 on 2005-01-13
Hiya!

Im new to ubuntu and have been having a bit of trouble getting this setup and i wonder if you guys could help.

I followed the guide through that i found on this website. I installed the speedtouch suite and the firmware for the modem. It seemed as though this had all worked correctly (i followed the guide to the letter) , however, i could not find the built in pppoe dialer - and thought that i needed to download one.

During which i found another guide online and followed that one through (sorry could not find the link - but i remember it is one where you need to gedit the modem_run) I was unable to gedit the modem_run file and wasnt able to finish the guide or but my ISP details into the config files. (i could put them in PAP and CHAP config files though)

Then i found the pppoe dialer in ubuntu - i put my ISP details in and selected ETH0 (i had nothing else to choose from in the drop down box) and dialed - but the dialer just said "establishing connection" and did nothing else. I left it for a while and still no result.

Then i thought it may have been becuase of the second guide i followed may have installed conflicting files or changed some of the details. So i went through and manually deleted what i had made (also if anyone knows a good way to add / remove programmes in ubuntu it would be really really helpful as this is one of my main stumbling blocks) - and tried to dial again. Still getting establishing a connection but no action. I am getting to solid greenlights on the modem which is encouraging as when i have tried this before on RH9 i didnt even get that.

Sorry for the round about explanation i was typing it as i remember it.
I was wondering if anybody knows what i may be doing wrong or maybe you have had this problem yourself, any help would be greatly appreciated cos int he meantime im sharing an internet connection with XP and getting an impressive 2.5kbs!!! Also im in the UK if that makes any differance for the number to dial (0,38). Also can anybody suggest another good way of getting BT Broadband to work on ubuntu.

Many thanks!

---

### Post by sputnik on 2005-01-13
I set up alcatel USB on a debian sarge box with freeserve.
Relevant links were 

[http://sourceforge.net/projects/speedtouch](http://sourceforge.net/projects/speedtouch)
[http://speedtouchconf.sourceforge.net/](http://speedtouchconf.sourceforge.net/)
[http://speedtouch.sourceforge.net/index.php?/download.en.html](http://speedtouch.sourceforge.net/index.php?/download.en.html)
[http://www.steve-parker.org/articles/opensource.shtml](http://www.steve-parker.org/articles/opensource.shtml)

the last one actual was the most useful with a link to an install script.  I think I used Google to check the relevant country code numbers.  Can't quite remeber all the details because I am using an ethernet card and external modem and router now.  (It just works without any further configuration)

---

### Post by Q00 on 2005-01-13
Thanks for the links - i followed the guide through, at the moment everytime i run:
#  ./speedtouchconf.sh

i get the following ...

************************************************

If you have any problems with this script, mail me
(steve at steve-parker dot org) with the files
/tmp/speedtouch.txt and /var/log/messages for diagnosis.
Using speedtouch-1.3-sgp
microcode is KQD6_R204.zip
  PPP version 2.4.2 okay.
  Linux kernel version 2.6.8 okay.
ls: /dev/ppp: No such file or directory
ls: /dev/ppp: No such file or directory
/dev/ppp cannot be created, or is not device 108
Not ready to install the software at this time. - code 32
root@Bastion:/home/u001/speedtouchconf-10-Nov-2004 # ./speedtouchconf.sh

Can anyone help me make sense of this? All i can think of is that i need to install some additional ppp software (?) I also tried googling device 108 but didnt get anywhere is it usb (?)

on a previous attempt (the first couple of times) the script did run and i had to enter all my details, but when it ran it said that the lights on the modem would blink for 20 seconds - whereas mine stayed static.

could any one help point me in the right direction? 



Many thanks

---

### Post by sputnik on 2005-01-14
are you running in a root terminal, or at least sudo when you try this?  I know i forget sometimes and things don't work as they should. :oops:

---

### Post by Q00 on 2005-01-16
Yup - logged in as root and using the PPPoE dialer from the apps > panel

Also have tried using the sudo PPPoE dialer - same result

I did mange to get close, where it asked me to insert the necessatry details, but it was showing two files in the firmware version (the zip and the .gz). So i removed one and this is what im getting now.

Also at the moment in order to get internet on my ubuntu box im connection sharing with an XP laptop as a gateway through a X-over cable. Problem is im only getting 2.5kbs! Does anybody know what could be causing this problem - would it be faster if i used a hub or are there any settings i can change on Xp and Ubuntu to speed this up?

Thanks

---

### Post by sztosz on 2005-01-16
Hi, I have similar problem with getting my Speed Touch Modem run. 

I got the same message using Steve's sctript, and I managed to find out that it's some problem with usb_ohci module (maybe lack of it).

I Managed to make a progress. All is in the this: [http://www.ubuntuforums.org/showthread.php?t=11303](http://www.ubuntuforums.org/showthread.php?t=11303)

---

