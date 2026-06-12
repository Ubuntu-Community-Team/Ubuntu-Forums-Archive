---
title: "Wireless troubles on Ubuntu 10.10"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by rohan_m on 2010-10-24
Hello! I just installed Ubuntu 10.10 on my system using Wubi and Windows 7. However, after installing, I went to Ubuntu and then saw that my wireless is not working. The wireless icon in the top bar has a red icon on it and when I click on it, it says “Wireless Connection: Device not ready (firmware missing).” I used Google, but soon got lost in all of the Ubuntu-talk about something called ndiswrapper. My card is:

02:01.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

If someone could point me in the right direction in to finding the correct firmware so I can get my wireless working that would be great. My wireless still works fine on the Windows side of things. However, I do not have internet access on Ubuntu as I do not have access to a direct line. Thanks in advance for your help.

---

### Post by William Anderson on 2010-10-24
Hi,

Check out [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) for instructions covering the Broadcom wireless card drivers.

I think that you simply need to go to System-Administration->Additional Drivers and select one of the Broadcom closed source, binary drivers. from the card chipset that you provided, and the description of which cards each of the drivers support, you need the B43 driver. 

Hope that this helps, 

William

---

### Post by Sef on 2010-10-24
> Check out [https://help.ubuntu.com/community/Wi...Driver/bcm43xx](https://help.ubuntu.com/community/Wi...Driver/bcm43xx) for instructions covering the Broadcom wireless card drivers.

I think that you simply need to go to System-Administration->Additional Drivers and select one of the Broadcom closed source, binary drivers. from the card chipset that you provided, and the description of which cards each of the drivers support, you need the B43 driver. 

Hope that this helps, 

William

Actually the wrong firmware has been installed by default for the Broadcom 43xx. A solution is in this [sticky]("http://ubuntuforums.org/showthread.php?t=1604868"). It worked for me on my Broadcom 4312 card.

---

### Post by McGuffin on 2010-10-25
Hi - it seems I'm having the same problem, and I'm still new to this so pardon my ignorance if this seems like a stupid question, but:

Does the Synaptic package manager require an internet connection to install the driver?  Because I can't seem to get the solution in that link to work, and I can't connect to the internet without my wireless adapter... I seem to be stuck in a catch-22 here.

Is there a way to get the wireless card to work without being able to connect to the internets?  For the record, I'm posting this using Windows, which works fine (I have a dual-boot).  I thought about copying the drivers from windows across to ubuntu, but I don't know how to install them.  Would that even work?

Thanks for any help,

McG

---

### Post by kermittoad on 2010-10-25
> **McGuffin said:**
> Is there a way to get the wireless card to work without being able to connect to the internets?
 
Remove the wireless card, and connect with a wired connection using an ethernet cable direct to the router while you sort out the problem.  Sometimes, you can leave the card plugged in while you use the wired connection.

---

