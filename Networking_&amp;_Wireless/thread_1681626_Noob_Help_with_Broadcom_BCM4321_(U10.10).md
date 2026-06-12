---
title: "Noob: Help with Broadcom BCM4321? (U10.10)"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by Shadowhawk109 on 2011-02-04
Hey all,

Getting a bit frustrated with experimenting on my own, so I figured I'd finally try posting here.

Running a ASUS EEEPC 1000HA with a MACBOOK PRO's Broadcom 94321MC inside it (replaced the original).

$lspci -vvnn | grep 14e4

>01:00.0 Network controller [0280]: Broadcom Corporation BCM4321 >802.11a/b/g/n [14e4:4328] (rev 05)

So basically, a BCM4321.

Installed STA out of box, and the wireless works, but FREQUENTLY disconnects/reconnects/asks for password & certificate (I'd say at least every minute), and not just to my University's internet (WPA2Enterprise w/ PEAP) but with ANY network, with or without encryption. Apparently this is a known/priorly discovered problem, but no one is really clear on the answer.

Tried: 

**1)** [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1598893&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1598893&page=2) specifically

$sudo apt-get install linux-backports-modules-compat-wireless-2.6.36-2.6.35-23-generic

and that didn't make any difference; since then I removed it through Ubuntu Software Center because I didn't want it messing anything up as I went further into trying to fix this.

**2)** [http://ubuntuforums.org/showthread.php?t=1593717](http://ubuntuforums.org/showthread.php?t=1593717)
specifically

$sudo apt-get --purge remove firmware-b43-installer
$sudo apt-get --purge remove dkms
$sudo apt-get --purge remove bcmwl-kernel-source
$sudo apt-get install bcmwl-kernel-source
$sudo reboot

and that let me uninstall the STA (initially couldn't due to a  "error msg: SystemError: installArchives() failed"), at which point I tried to install the B43 but the 4321 doesn't seem to be the target of the B43 and I don't really understand what to do with the firmware cutter, I'm hesitant to do anything because I'm not sure it's the right path and I don't know what I'm doing let alone how to undo it.

**Long story short**, I need advice on how to get a consistently working connection with my Broadcom 4321; there's talk of
"Solution: System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > Close" for the B43 being the way to get stuff working, or using NDISWrapper, but I just don't know what I'm doing.

I have a bit of Linux experience, but for all intents and purposes, please assume I'm an idiot, so I actually understand what you tell me to do and learn from it.

Thanks!

---

### Post by chmegr on 2011-04-26
I am having the same problem. :( I have a Dell Precision M6300 with a BCM4321 803.11a/b/g/n and I cannot get it to work properly.

---

