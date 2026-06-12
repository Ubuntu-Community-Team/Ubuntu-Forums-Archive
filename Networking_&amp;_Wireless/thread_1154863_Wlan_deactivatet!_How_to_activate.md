---
title: "Wlan deactivatet! How to activate?"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by ronnys on 2009-05-10
Hi!
Im a completely new user of Ubuntu. I bought an Acer Aspire One A150 that comes with XP Home, but i really dont want to use XP on such computer.
I want to try out the latest Ubuntu 9.04 Remix since it support this model out of box.

I installed it from an USB-memory and after the latest upgrades, then it works perfect; Wlan, Graphic, Sound and Webcam.

Then after two days i did a reboot because i try to run Screamer Radio i Wine and it crash completely the computer. I manage to CTRL-ALT-DEL and Reboot. Now during boot i think i hit the Wlan-button and disable it. Now my wlan is gone. If i in terminal execute: lspci, i can see the Atheros card deteted. I know there is a command to enable/disable wlan-cards.

Anyone know how to enable the Atheros-card on Acer One A150 in Ubuntu 9.04 Remix?

Thanks!

---

### Post by ronnys on 2009-05-10
I forgot to tell that the Wlan-button on the Acer One doesnt activate wlan. If i click on Network-Manager the wlan is gone. Only LAN-connection show up.

How do i get the wlan-button work on Acer A1?

---

### Post by chili555 on 2009-05-10
I saw this: [http://wiki.archlinux.org/index.php/Acer_Aspire_One](http://wiki.archlinux.org/index.php/Acer_Aspire_One)

I was especially interested in this part:>  Additional function keys

For the wifi kill switch add these keycodes in /etc/rc.local:

 /usr/bin/setkeycodes e055 159
 /usr/bin/setkeycodes e056 158

Note that if the wifi kill switch is on (wifi is off), you will need to reboot to re-enable wifi once you disable the kill switch. Arch Linux is a bit different from Ubuntu, however *setkeycodes* should be the same. Please post back and let us know.

---

### Post by ronnys on 2009-05-11
Sorry! No result!
I put it in rc.local but i also execute it in terminal.

Isn't there a command i can send to the Atheros-driver to trigger activation. I know this is possible to Intel wlan-devices.
It seems like the wlan-button only disable the wlan-device, but does not activate.

RS


> **chili555 said:**
> I saw this: [http://wiki.archlinux.org/index.php/Acer_Aspire_One](http://wiki.archlinux.org/index.php/Acer_Aspire_One)

I was especially interested in this part:Arch Linux is a bit different from Ubuntu, however *setkeycodes* should be the same. Please post back and let us know.

---

### Post by ronnys on 2009-05-12
First i start to belive the whle wlan-card has become defect, since i reinstall Ubuntu Remix and experience the same problem.
I was about to install WinXP to see if the wlan is working in WinXP.

Then i go into the Harware Drivers and deactivatet the proprietary Atheros driver and rebooted. Now the wlan suddenly work again.

First time i installed Ubuntu Remix the open wlan-driver worked. After doing the required upgrades, then it supendly stop working. I activatet the proprietary driver and wlan work again. It was working for 2days and then it stopped working.

Now it seems that the open driver is working again and not the propiatary.

I wish i knew what driver is most stable!

---

