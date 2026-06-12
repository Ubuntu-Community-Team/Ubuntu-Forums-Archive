---
title: "dont read unless you will answer (wireless woes)"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by gfunkera on 2009-05-28
in an effort to save my mother a bunch of money on a new laptop, i recently installed intrepid ibex (ubuntu 8.1) on her dell laptop... it doesnt have a built in wireless card so i have two options: an atheros card (D-Link AirPro DWL-AB650) and a card that gets recognized as a wlan0 (Dell TrueMobile 1300)... okay ready for the hard part? bear with me here...
 
okay so i went through a few days of non stop "trying to get the damn internet to work" on this laptop.. i tried ALOT of stuff i even ended up buying (and returning) three different linksys cards from best buy!! 
 
along the way i ended up changing alot of stuff (so if you can help me, please keep that in mind) like adding and removing drivers (and windows drivers)...
 
the hardest part about all this is that the laptop that im trying to get internet working on with these cards doesnt have the internet!! it makes it very frustrating!!
 
anyway, so i kinda got a feel for ndiswrapper but cant really figure it out cause all the darn threads i find on this matter have broken ndiswrapper links (even the links on the ubuntu wireless support)...
 
im not even sure if buying a wireless adapter like an orinoco will work now because ive changed so much stuff...
 
i managed to get the truemobile 1300 card working for a a very brief time and then it completely stopped working and even when it was working it was connecting at VERY slow speeds to my wireless router... but ever since it STOPPED working, it doesnt even show up in the list when i type the iwconfig command in the...
 
as far as that atheros card (the dlink dwl-ab650), when i plug it in the two 'activity' and 'power' lights are alternating on and off.. and sometimes they sync and blink together, i dont know what it means..
 
I NEED THE INTERNET TO WORK!!! PLEASE HELP!!! WHAT DO I DO!????

---

### Post by lavinog on 2009-05-28
Your title is interesting. How am I to know that I will answer unleass I read?

Do you know the model number of the laptop, or what are the specs (does it have usb2.0 or usb1.1? Does it have a pcmcia slot or pci express?)

My first recomendation would be to use the latest version of ubuntu (9.04). Wireless support tends to improve with each release.

Since you changed so much stuff, you may want to consider a clean install.
if the wireless card doesn't work after a clean install, go to system>administration>hardware drivers and see if the network driver is listed there...if so enable it.

---

### Post by t0mppa on 2009-05-28
> **lavinog said:**
> My first recomendation would be to use the latest version of ubuntu (9.04). Wireless support tends to improve with each release.

Someone's been living underground for the past month. :) Jaunty caused tons of wireless issues for folks. For some cases it's a step forward from 8.10, for some it's a step back.

@gfunkera: The Dell card (Truemobile) likely has a broadcom chip, should have 2-3 working solutions to pick from. Just need to know what chip it has though. And same applies for the Atheros one actually.

So, just pick either one to try first, plug the card in and run **lshw -C network** and **lspci** if it's a pci card or **lsusb** if it's a usb stick. Knowing the chips your cards have will help pick the correct drivers.

---

### Post by gfunkera on 2009-05-28
lavinog: yes the title was deliberately titled to intrigue you. the dell has a model number on the bottom listed as: **PP08S** im having trouble finding the specs but i think it has usb 2.0 and im pretty sure its a pcmcia slot...

t0mppa: the TrueMobile card is bcm4306 (the lspci says **02:00.0 Network Controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)**... i figured that out by going through this whole escapade this last few days.. i just dont know how and where to find the drivers (ive been looking!) and how to make them work!

---

### Post by t0mppa on 2009-05-29
Ok, I don't like NDISWrapper, because it wouldn't let my wireless card connect to encrypted networks (only open) and it started causing computer freezes later whenever I put wireless on.

So, try [this]("http://linuxwireless.org/en/users/Drivers/b43") for starters, it's a pretty simple set up and you can do the wgets (downloads) on another computer and just move the files to the one you're trying to fix through removable media for instance. 4306 should work with b43legacy, in case you're wondering which one to pick.

However, since you did a lot of configuring earlier, you have to make sure the b43 or related modules aren't blacklisted (NDISWrapper set ups usually do this). So, crawl through the files on /etc/modprobe.d/ and comment out (add a # in the beginning of the line) or delete lines like the following```
blacklist b43
blacklist b43legacy
blacklist ssb
```

---

### Post by 73ckn797 on 2009-05-29
I have found a good solution with a wireless card that I have. It would work but show a very weak signal even though it was 10 feet from the router.

I used "ndisgtk" from the repositories. It is a GUI tool to install wireless drivers with. You would have to install ndisgtk then look on the driver disk that comes with the card. Likely you would have to copy the contents of the folder for Windows XP driver to your computer. Start up ndisgtk found under System/Administration at the bottom of the list. From there select the "inf" file and let it do it's thing. 

This has worked for me on several situations so it may be worth a try.

---

### Post by t0mppa on 2009-05-29
Ndisgtk is just the graphical front end for NDISWrapper. Better to just try one thing at a time, instead of mixing them all in, which probably means none will end up working. So, if OP wants to use that instead, feel free to guide him through to a working installation.

---

### Post by 73ckn797 on 2009-05-29
> **t0mppa said:**
> Ndisgtk is just the graphical front end for NDISWrapper. Better to just try one thing at a time, instead of mixing them all in, which probably means none will end up working. So, if OP wants to use that instead, feel free to guide him through to a working installation.

I did state that it was a GUI tool and gave them the simple directions. The options are theirs to choose.

---

### Post by t0mppa on 2009-05-29
Yes, I know and didn't mean to sound so offensive. Point was that OP did mention trying ndiswrapper earlier and didn't get it working, so it either wasn't all that simple or there were some other issues.

So, what I was trying to say was that if you're offering a solution, be sure to stick around to troubleshoot it, if something goes wrong. I just hate drive-by-posting, where someone drops in a thread, offers some magical solution and is never heard from again, when it doesn't work. And then depending on the tech savviness of the person being helped, it takes either 5 minutes or 3 days to get all the problems caused by that single comment fixed.

Thus apologies for the grumpy comment and like agreed, let the person with the problem choose.

---

### Post by 73ckn797 on 2009-05-29
> **t0mppa said:**
> Yes, I know and didn't mean to sound so offensive. Point was that OP did mention trying ndiswrapper earlier and didn't get it working, so it either wasn't all that simple or there were some other issues.

So, what I was trying to say was that if you're offering a solution, be sure to stick around to troubleshoot it, if something goes wrong. I just hate drive-by-posting, where someone drops in a thread, offers some magical solution and is never heard from again, when it doesn't work. And then depending on the tech savviness of the person being helped, it takes either 5 minutes or 3 days to get all the problems caused by that single comment fixed.

Thus apologies for the grumpy comment and like agreed, let the person with the problem choose.

No offense taken my friend.

---

