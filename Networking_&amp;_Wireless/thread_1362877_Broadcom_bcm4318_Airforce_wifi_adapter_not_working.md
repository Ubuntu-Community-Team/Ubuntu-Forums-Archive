---
title: "Broadcom bcm4318 Airforce wifi adapter not working"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by matbence on 2009-12-23
This post is for any other linux amateurs out there trying to get started with ubuntu, but having problems setting up wifi.

When first  trying to install ubuntu 9.10 on my HP pavilion zd8303ea (like a zd8000), I couldn't get the wireless adapter (Bcm4318 airforce) to work using native drivers or ndiswrapper.

Initially when I first installed ubuntu under system->Administration->Hardware Drivers, B43 drivers needed to be installed, when I clicked on this it prompted me for a password, but did not install and enable the driver. **(I needed an internet connection, but it did not tell me).**

After this I tried using ndiswrapper with the windows drivers. When I installed the bcmwl5.inf file I got an 'unable to see if hardware is present' error.

As far as I could tell the hardware was working (I dual boot XP), but the wifi light on my computer did not light up. [This page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") helped me - apparently there is some firmware that needs to be downloaded when ubuntu first tells you there are some proprietary drivers to install. I only received these prompts after the operating system had first been installed. I think I lost these prompts after I had been fiddling for a while.

To solve the problem I had to first reinstall ubuntu to reverse any changes that I made (I had no idea how to reverse the changes without re-installing). Next I connected my computer by ethernet cable to my router so I could download the firmware when prompted. I think the link above also gives instructions for if you can't connect to the internet via ethernet cable.

*On another note, when I received the  'unable to see if hardware is present' when trying to get wifi working on another laptop (using ndiswrapper), again the driver was not at fault here (I didn't even need to use ndiswrapper) - my wifi adapter had been turned off inadvertently with a keyboard shortcut.

---

