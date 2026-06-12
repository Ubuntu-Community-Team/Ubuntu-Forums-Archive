---
title: "Please help me get my LinkSys Wireless Card Working"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by CLEE25 on 2009-01-12
Hi All, 

Total Linux newbie here looking for help. 

I have installed Ubuntu (ver 8.10 Intrepid Ibis) on my old laptop which uses a Linksys Wireless Card (WPC54g) 

The wireless card is Broadcom BCM4306 (rev 02) 

I read on this post that the drivers for this card do not install when you install Ubuntu:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WMP54G](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WMP54G)

And that you can 
clicking System > Administration > Hardware Drivers, then activate the Broadcom B43 Wireless driver. 

**However I do not have a working ethernet card (wired connection) on this laptop. **

So, can anyone give me a step by step on how I might be able to download a driver from somewhere, save it to a flash drive, and move it over to this laptop and install it?

I have found some tutorials online but they all are terminal commands with get [http://.](http://.)... (etc) and since I can not connect to the net they don't help. So I am not sure if this is even possible.

Again, thank you for your time--and if you do answer, keep in mind that I am completely new at linux and Ubuntu.

---

### Post by tdelp on 2009-02-20
I too am a newbie.  However after many, many hours, I got my card to work with Intepred Ibex, 8.10 without using terminal commands which I am struggling to learn.  Since I am a newbie, please forgive any transgressions in nomenclature, descriptions, spelling, etc., as I was so excited to get this Wpc54g v1 wireless card to work I had to share my experiences.

Linksys.com support-download link gave me the correct driver file but make sure it is the right version, mine was v1.  I could not test to see if this works with other versions. 

The last step in my learning was to rename the .inf, .cat and .sys files I got from Linksys site with small letters as they came in caps from Linksys.  Apparently Linux treats caps and small letters differently while windows mostly does not.  I copied those files to a thumb drive and put them in the linksys folder I created in the Home folder on the ubuntu Dell C640 Laptop.  (like I said, I am a newbie and I really don't know what files were really needed so I took what I thought was important).

There was a hardware driver that installed with the intrepid update that I unsuccessfully tried.  It had fwcutter... in the descriptive text but I un-activated it (if you did not activate it, you may want to try it) in System>Administration>Hardware Drivers. It actually worked but at very slow speed which varied from 1 to 6 Mb/s.

I installed the ndiswrapper package using Synaptic Package Manager (I chose ndisgtk, so search for that.  It seemed to install 2 others parts as well).  I think it is the graphical interface for ndiswrapper which I dearly needed.

I then went to System>Administration>Windows Wireless Drivers and chose to + Install New Driver and after finding the .inf file in the linksys folder I had created, clicked install.

That was it!  I cannot remember if I restarted or not but the wireless card now worked at 54Mb/s.

If you have any questions, I probably cannot help because I am a such new newbie, but I might try.

---

