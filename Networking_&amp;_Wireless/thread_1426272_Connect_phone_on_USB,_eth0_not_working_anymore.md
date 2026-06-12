---
title: "Connect phone on USB, eth0 not working anymore"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by drzipp on 2010-03-10
Gents,

I have a wired connection (eth0) on my working PC. Yesterday I did connect my wife's Samsung i8000 phone to one of my USB ports to pull some photos from her mobile. All of a sudden a popup showing me eth0 is connected? Since then eth0 is not working anymore.
Did this million times with my BlackBerry without any issues. How come eth0 is stressed out now? /etc/network/interfaces is showing the right settings. ifconfig -a as well.

dmesg is showing a lot of times;

usb 1-9 : reset high speed USB device using ehci-hcd and address 4

Not sure if this is related to my problem.

any thoughts?

Dr.Zipp

---

### Post by drzipp on 2010-03-10
Found out that /etc/resolv.conf was emptied.
Entered the right settings manually, now network is working. Networkmanager still messed up, doesn't show anything. When I key in eth0 manually in the networkmanager gui, it is not possible to save the settings. They are gone immediately when hitting OK button.
Arrrg, what is the problem here :-(

---

### Post by Soulcage on 2010-03-10
Does restarting do anything?

---

