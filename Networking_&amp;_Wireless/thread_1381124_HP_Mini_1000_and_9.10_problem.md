---
title: "HP Mini 1000 and 9.10 problem"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by mullinsn2000 on 2010-01-14
Ok, I have searched the forum for this problem and found it. I tried everything in the threads and nothing worked.
 
I have an HP Mini 1120NR with the BCM4312 wireless network chip. I have successfully installed Ubuntu 9.10, but I am unable to connect to the internet. I have checked System>Administration>Hardware Drivers and there are absolutely no drivers in there.
 
The HP Mini has no RJ-45 port so the only way I can connect to the internet is wirelessly. I do have another computer with Windows Vista and an 8GB flash drive (which I installed 9.10 from).
 
I need someone to explain to me how to get my wireless card working. I need the dumbed down version as I am using Linux for the very first time.
 
Thanks for all the help that I hope to get!

---

### Post by bkratz on 2010-01-14
This seems to work for most people

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by mullinsn2000 on 2010-01-14
I guess I missed that thread.  I will give that a try.  Thanks!.  I now have to make the flash drive bootable again.  I formatted it to clear everything off to try to install the original Mie OS, but that did not work.  It had XP on it when I got it but I wanted to try Linux and figured since Mie is a variant of Ubuntu that I would not have troubles, little did I know, lol.

---

### Post by mullinsn2000 on 2010-01-14
so I tried the steps in the link.  Not all of them worked but I did get the driver to show up in the Hardware Drivers.  I click on activate but it does not activate it.  It says it is installing but does not actually activate.

---

### Post by Genkakuzai on 2010-01-14
Do you have any ethernet connections you can use? If so, make sure you're connected to the internet somehow and then click activate, that should do it. 

I have an HP Mini 110-1030NR and I had to do the same thing. I had the same problem with OpenSuse as well. Mandriva Linux had the driver installed out of the box but I'm sticking with Ubuntu for now. 

Anyways, to get mine working I just connected my HP Mini to the internet through ethernet, ran Update Manager to get the OS up-to-date. Then after that I clicked on Hardware Drivers, it gave me two options but I chose to activate Broadcom STA Wireless Driver. It did so, and now I'm running smooth. 

Hope my post contributed in some way, if not have a nice day!

---

### Post by mullinsn2000 on 2010-01-14
Wireless is the only network card installed on the HP Mini 1120NR.

---

### Post by bkratz on 2010-01-14
Here is  the original step by step thread that has worked for many people, the other thread was based on it but this may be easier to follow and describe where the failure occurs.

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by mullinsn2000 on 2010-01-14
> **bkratz said:**
> Here is the original step by step thread that has worked for many people, the other thread was based on it but this may be easier to follow and describe where the failure occurs.
 
[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)
 
 
That is for use with the Live CD.  My netbook is using a USB flash drive.  I tried what it said an nothing happened that helped.

---

### Post by newTron on 2010-01-28
Sorry, have to make a quick comment.  Are you sure your 1120nr doesn't have an ethernet port.  I have an 1120nr and the ethernet port is hidden behind a little rubber cover on the right of the headphone jack on the left hand side of the machine.

Did you get the wireless working yet?

---

### Post by mullinsn2000 on 2010-02-05
> **newTron said:**
> Sorry, have to make a quick comment.  Are you sure your 1120nr doesn't have an ethernet port.  I have an 1120nr and the ethernet port is hidden behind a little rubber cover on the right of the headphone jack on the left hand side of the machine.

Did you get the wireless working yet?
HaHa, maybe I should have tried looking in a brightly lit room.  Yes there is a port next to the headphone jack, lol.  It was too dark in the room I was in to even see it.

Did I get it working?  Yes and no.  No I did not get it working with 9.10, but I did get it to work with 8.04.  Now I can connect at home no problem, but at school I can not connect.  The networks shows up, shows strong signal, it is an unsecured network but it tries to connect and does not connect.

---

