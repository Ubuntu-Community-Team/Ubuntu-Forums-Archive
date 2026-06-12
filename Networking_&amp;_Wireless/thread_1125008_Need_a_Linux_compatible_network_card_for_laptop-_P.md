---
title: "Need a Linux compatible network card for laptop- Please help a new user"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by planegenius on 2009-04-13
After saying bye bye to windows XP, and installing Ubuntu 8.10, everything, to my surprise, works really well, except for one thing, my wireless internet.  However, this was not a surprise.  I ran Ubuntu on a disk image and it didn't work there.  I thought I found a solution, and backed up my data and deleted windows and installed Ubuntu.  Unfortunately, those fixes didn't work.  I think the best thing to do now is buy a new network adapter card for my laptop, but I have absolutely no idea where to look for one that is compatible with the Linux OS.  Instead of having to utilize the windows drivers, is it possible to get one that will just automatically work with Linux (My understanding is that Linux doesn't use drivers, it just needs the kernel).

Can anyone offer any advice/suggestions on this matter? I need a laptop network adapter card for a wireless G network.  Is it possible to find one at an electronics store?

Thanks so much for your help!

---

### Post by inobe on 2009-04-14
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

that is a list.

for the card you are interested in' click the link to the device and you will get more information, look for a card that works out of the box.

---

### Post by Procuro on 2009-04-14
Have you tried connecting to the internet in ubuntu using a wired connection? You can install all the available updates and odds are that it'll find your wireless device and offer a restricted driver for you to install. That's the easiest way to get most wireless cards working in 8.10.

If that doesn't work or is impossible for your situation, did you try installing ndiswrapper off the ubuntu cd and attempt to get the appropriate driver working? 

more info:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Hope that helps. I really doubt you need a new wireless card. Many simply don't work "out of the box" but just about all of them will work one way or another.

---

### Post by dwouters on 2009-04-14
> **planegenius said:**
> After saying bye bye to windows XP, and installing Ubuntu 8.10, everything, to my surprise, works really well, except for one thing, my wireless internet.  However, this was not a surprise.  I ran Ubuntu on a disk image and it didn't work there.  I thought I found a solution, and backed up my data and deleted windows and installed Ubuntu.  Unfortunately, those fixes didn't work.  I think the best thing to do now is buy a new network adapter card for my laptop, but I have absolutely no idea where to look for one that is compatible with the Linux OS.  Instead of having to utilize the windows drivers, is it possible to get one that will just automatically work with Linux (My understanding is that Linux doesn't use drivers, it just needs the kernel).

Can anyone offer any advice/suggestions on this matter? I need a laptop network adapter card for a wireless G network.  Is it possible to find one at an electronics store?

Thanks so much for your help!

Planegenius,

Laptop specs please?

Dennis

---

### Post by planegenius on 2009-04-14
Thanks Everybody!

I did try ndiswrapper with no luck.  I can wire to my router and will try to connect and get updates.

The system specs of my laptop are attached.


The original problem is described in this post-
[http://ubuntuforums.org/showthread.php?t=1124451](http://ubuntuforums.org/showthread.php?t=1124451)

More help is appreciated! It seems that this is a known problem with this card, and it needs some tinkering done, but I have no idea how to do it.

Thanks!

---

### Post by planegenius on 2009-04-14
I installed all the updates, and even a proprietary driver for a 'software modem'.  Still having the same problem though.

At this point I am looking at purchasing a Linksys - 802.11g Wireless Notebook Card (WPC54G).  Not expensive, and some versions of it seem to work a according to this-

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCMCIA](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCMCIA)

However, I have no idea what version of the hardware I would get if I bought this from the store.  7.1 says it will work out of the box, but at the same time other versions don't work.  I have no idea how to tell in the store what version of the hardware I'm buying.  Will the latest version, hopefully 7.1 be the one on the shelf?

Any advice, or another suggestion?

Is this  good choice?

---

### Post by dwouters on 2009-04-14
Linksys is a widely supported card throughout most Linux distros. I believe that would be a safe bet. Let us know how things work out. Anyone is welcome to correct me if I am wrong on this one.

---

### Post by planegenius on 2009-04-14
Well right now I am trying to make sure that I get version 7.1.  That should work out of the box.  The thing is,  don't know how to tell what version I'm buying.  I talked with Linksys and they said 7.1 is the latest, and i assume that they would put the latest version on the shelf, but you know what they say about assuming....

They also said that the salesperson at Best Buy should know, which i really hope they do.

Does anyone here know how I can tell what version it is?

---

### Post by inobe on 2009-04-14
i would do a search on google or this forums with keyword "wireless" then you would want to avoid purchasing those cards found from searching.

you don't want a card that requires any extra effort getting it to work.

quite honestly' i refuse to support hardware vendors that do not release linux drivers.

---

### Post by planegenius on 2009-04-14
:KS

[SIZE="5"][FONT="Arial Black"]IT WORKS!![/FONT][/SIZE]

Thank you all so much.  I went to Best Buy and bought the version 3.1, but they said I could simply download the driver from the linsys support site and fix it.  Guess who was wrong?! I tried using ndiskwrapper, with no luck.  Then I found this- [https://help.ubuntu.com/community/WifiDocs/Device/LinksysWPC54GS-UK](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWPC54GS-UK)

I followed these instructions, and I am now wireless.  I am so very happy that I switched from XP!

**One last question-**  Still new to Ubuntu.  Is it okay to upgrade to other versions and updates of ubuntu?  I know 9.04 is coming soon.  Will I risk losing wireless capabilities with this device if I do, or will I be ok?

Thanks Again to everyone!! :guitar:

---

### Post by dwouters on 2009-04-15
Cngratulations!!! Negative, you should not lose your wireless capability. When you upgrade, you will be prompted if you want to relace any custom files, such as your modified /etc/resolve.conf and your custom blacklist. If you select "keep" when prompted, you should be fine.

Enjoy the full benefits of Open Source, most specifically Ubuntu. I am really fond of this OS and I do not believe that I will ever go back to Windblows.

---

### Post by planegenius on 2009-04-15
I am very happy I moved away from Windows.  If I didn't have so many windows games on my desktop, I'd take windows off in a heartbeat and install Ubuntu.

Thanks for your help!

---

