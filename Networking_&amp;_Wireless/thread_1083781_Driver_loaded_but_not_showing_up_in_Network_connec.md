---
title: "Driver loaded but not showing up in Network connections."
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by runebinder on 2009-03-01
Hi, installed Ubuntu 8.10, pretty new to Linux, had a play with Kubuntu a year or so ago but then didn't carry it on. Have been reading around as I can't get my wireless to work, however in a case of the more I read the more conufsed I'm getting atm and not sure what stuff is relevant to my hardware.

When opening up Terminal and running some commands I've come across I get:

sudo lshw

 *-network:0 DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: (deleted by me) 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 

iwconfig

wlan0     IEEE 802.11bg  ESSID:""   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=0 dBm    
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B    
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

lspci

05:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 

Now from here it looks like the driver is loaded but disabled? If it was Windows it'd be a simple case of opening Dev Man and enabling it, haven't got a clue with Ubuntu how to go about that though. The card's certainly been detected and installed, can't figure out why it won't view any wireless networks and the box for wireless in Network connections is blank.

I really like the idea of open source and want to become less reliant on MS, however internet connection is a must, if someone can help me out on this it'd be most appreciated.

Ian.

---

### Post by theDaveTheRave on 2009-03-01
runebinder


Wireless connectivity is seemingly a ongoing problem with various linux flavours!

Anyway it seems as though you are almost there, as the card is definately supported, I've seen various threads with solutions, and your questions are probably best to be targeted on one of those.

However, by way of getting you started....

When you "played" with kubuntu last year did your wireless work? if so there may have been a regression in the functionality (I had this myself just recently, my wireless suddenly just stopped working, and it took a fair while to get it back again!).

Anyway, the other question is.... did you try the live CD? and did the wireless work there but not on your final install? 

In both of these cases it would suggest that a change / update in the kernel may be the cause, and you need to find the correct modules that control the card and then re-install them into the kernel.

To check to see what kernel are loaded into your system you need to do the following...

```

lsmod

```

you'll have to have a look around for a module that relates to your card

A quick hunt threw up this forum with a reply from Kevdog (he helped sort out my problems in fact, here is the link [http://ubuntuforums.org/showpost.php?p=6772825&postcount=2]("http://ubuntuforums.org/showpost.php?p=6772825&postcount=2").

I can heartily recomend that if you have problems Kevdog will be the one to help you out.

Good luck with this and if you get the card working put a note in this thread pointing to the solution.

David

---

### Post by runebinder on 2009-03-01
Thanks for the reply Dave, wasn't working in the Live CD either. However  managed to get it fixed. Set my girlfriend's computer's wireless connection to shared and ran an Ethernet cable from hers to mine (love modern technology used a patch cable, was half expecting it not to work but thankfully did), and ran updates. Driver message came up and gave me an option for the Broadcom wireless driver, activated it, restarted and hey presto am typing this connected via the wireless. 

Nice to know the simple solutions will work :D Thanks for taking the time to help though. 

Ian.

---

