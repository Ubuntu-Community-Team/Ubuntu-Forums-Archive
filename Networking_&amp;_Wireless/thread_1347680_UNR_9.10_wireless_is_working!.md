---
title: "UNR 9.10 wireless is working!"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by pjsmetana on 2009-12-06
This is for HP Mini 110 1030nr running Ubuntu-Netbook-Remix 9.10 on kernel 2.6.31-16-generic

In console:

$ uname -r
(this just shows your kernel)

$ sudo apt-get update
(downloads the hit/ign list)

$ sudo apt-get upgrade
(let all of these download)

Then go to the HP website and look for drivers.
For this particular netbook, I downloaded the windows driver for the Broadcom BCM4312 802.11b/g (rev 01) wireless lan, called sp45515.exe

Now, system>admin>windows wireless drivers (if thats not there, get ndiswrapper through synaptic)

You see when you open that it asks for a .inf file. 

Download Wine in synaptic.

run the sp45515.exe in wine.

open the files and search for bcmwl.inf

now go back to windows wireless drivers and select this .inf

even if it tells you that it cannot detect, it still works, as long as there isnt a giant red X over it. If there is, then restart and try to open that .inf in there again. 

after about 2 minutes, you will have wireless options again!



Now... if I can only reenable my internal mic :D

---

### Post by cerberez on 2010-03-29
OMG thank you thank you thank you! I have been working on this for days and every other seeming solution somehow didn't manage to work, so I only succeeded when I found your fix for the exact same model of netbook I use.

---

