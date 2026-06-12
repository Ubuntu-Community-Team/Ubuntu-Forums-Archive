---
title: "wireless for my laptop"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by chips24 on 2010-08-02
i just recently installed Ubuntu on my laptop under wubi and i cant find what kind of wireless driver i have because it didnt install when it was the system was installing. I've used vista for years and i knew the os inside and out. but windowsXP is terrible and i dont know it that well. also i cant get my computer to boot from my flash disk. otherwise windows xp would be gone by now.

yes, i would prefer to use dell instead of acer crap.

---

### Post by marc.verwerft on 2010-08-02
What's your question?

Use log files to see/learn what's going on in your system: [http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)

Maybe you can use this for a starter: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) if you have trouble with your wifi ?

---

### Post by chips24 on 2010-08-02
my question is; where can i find the driver for my wireless card on ubuntu?

ubuntu is kind-of useless right now if i dont have internet to get all my applications. I could use source code, but that would take way too long switching between operating systems. Is it possible that i might not be able to use the windows drivers if im booting it on bootstrap? i couldnt get the usb drive to boot so i could install Ubuntu and replace XP, so i had to use wubi. I would have used a DVD, but I dont have a dvd drive yet. For more information, i installed ubuntu 10.04 on an acer, 1.6 GHz Intel Atom,1GB RAM. network drivers-  atheros ar8132 pci-e fast ethernet controller, and broadcom 802.11g network adapter.

---

### Post by chips24 on 2010-08-03
i think its been 24 hours, im bumping this thread.

i can no longer boot Ubuntu, how do i install it through USB?

---

### Post by marc.verwerft on 2010-08-04
About your wireless device: is it detected by at all by linux - if yes then it should show a message in /var/log/messages. If not, then make sure that your device is supported in the linux kernel you use.

Installing Ubuntu is from USB is simple.
- you create a USB stick with Ubuntu on it
- put it in your laptop
- select boot from USB
- after it has booted there is a special link on your desktop that says 'install'
That's it.

If you have a look in the official Ubuntu documentation you'll find this doc:
[https://help.ubuntu.com/10.04/installation-guide/i386/index.html](https://help.ubuntu.com/10.04/installation-guide/i386/index.html)
That might help also ...

Regards,

Marc

---

