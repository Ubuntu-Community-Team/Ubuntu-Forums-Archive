---
title: "Wireless Works Until Reboot"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by bman214 on 2011-08-07
Hey
I have a Dell Inspiron 600m that is currently running only Ubuntu 11.04 Natty Narwhal. I have my network drivers properly installed, and I can get a wireless connection with the help of a few packages found by searching for "bcm", but when I turn off and turn on my computer (restart, shutdown and turn on, etc), the wireless stops working and it goes back to how it was before I installed the three bcm packages. Each time, to get wireless connection, I have to uninstall the packages, reboot, and reinstall them. Then it works until the computer is shut off. Does anyone have anything that could help?

Here are the "bcm" packages I have for my 4318 card:
bcmwl-kernel-source
firmware-b43-installer
b43-fwcutter

Also, my network card is a Broadcom 440x Gigabit Integrated Controller. Can someone please help?

Thanks in advance,
Bman214

---

### Post by westie457 on 2011-08-07
> **bman214 said:**
> Hey
I have a Dell Inspiron 600m that is currently running only Ubuntu 11.04 Natty Narwhal. I have my network drivers properly installed, and I can get a wireless connection with the help of a few packages found by searching for "bcm", but when I turn off and turn on my computer (restart, shutdown and turn on, etc), the wireless stops working and it goes back to how it was before I installed the three bcm packages. Each time, to get wireless connection, I have to uninstall the packages, reboot, and reinstall them. Then it works until the computer is shut off. Does anyone have anything that could help?

Here are the "bcm" packages I have for my 4318 card:
[COLOR="Red"]bcmwl-kernel-source[/COLOR]
firmware-b43-installer
b43-fwcutter

Also, my network card is a Broadcom 440x Gigabit Integrated Controller. Can someone please help?

Thanks in advance,
Bman214

Remove or de-activate the high lighted package, remove the cable and reboot the pc. Click on Network Manager icon to see a list of available networks. If you cannot see yours click on Connect to Hidden Wireless Network .... Enter a few details and away you go.

---

### Post by bman214 on 2011-08-07
> **westie457 said:**
> Remove or de-activate the high lighted package, remove the cable and reboot the pc. Click on Network Manager icon to see a list of available networks. If you cannot see yours click on Connect to Hidden Wireless Network .... Enter a few details and away you go.

THANK YOU SO MUCH! This worked! I never would've guessed it haha. I'm glad I can now permanently use wireless internet. =D

---

### Post by bman214 on 2012-01-26
Hey! I'm now trying out Debian and I have the same problem, except I don't even detect wireless networks yet.

I forgot if I uninstall the highlighted package before or after rebooting.
(example, install all 3 packages, *reboot?*, uninstall that one, reboot)

EDIT: None of the packages can be found. I tried synaptic, aptitude, and apt-get.
Looks like I'm headed to Debian's support forums...

EDIT2: Fixed on the Debian forums.

---

