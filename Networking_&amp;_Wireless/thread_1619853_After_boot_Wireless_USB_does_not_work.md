---
title: "After boot Wireless USB does not work"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by Scallyph on 2010-11-12
Hi 

Situtaion:
I've got this USB wireless stick using a Realtek RTL 8187l chipset plugged into a Lucid box running kernel 2.6.32-25.
Problem:
On every boot it will not connect because the stick is not recognized. Doing a lsusb or lspci reveals that it doesn't appear to be listed.
However. if I unplug the stick and plug it in again it works fine until next boot.
sofar:
runnin dmesg | grep USB, I see a lot of lines saying:
new low speed USB Device using uhci hcd and address 5
usb device is not accepting adress 5 error -71 (
or: 
new low speed USB Device using uhci hcd and address 2
device descriptor read/64. error -71
this goes on till address 9

Doing lsmode doesn't show any USB or chipset modules loaded.


What can I do to solve this?

---

### Post by Scallyph on 2010-11-12
Update;
I tried adding the noacpi option to the boot (temporarily) that didn't help
I tried to unload uhci_hcd with 'sudo modprobe -r uhci_hcd after unplug and plug in this USB wifi (after I disabled the working connection by right-clicking the icon networkmanager in taskbar at the upper right corner) that also didn't help.
So i plugged in USB memory stick (while system was down) rebooted, clickin on "places" selected removable drive and it just opened (auto mounted)
did not try to read or write to it.
brought system down again unplugged memory stick 
plugged in USB wifi
brought system up again
and now wifi works without un/pluggin!
booted system several times, to be sure (restarts and shutdown and start up)
Still workin!
Must say it takes about a min or 2 before network is up.

Can someone explain the process behind this?

---

### Post by skralljt on 2012-01-11
I have the same problem: usb wireless device not recognized after boot.  Unplug and replug it, and wicd starts working automatically.  I wish the fix worked as you described because it is a real pain to bend over my computer and replug this stupid thing every time I reboot.

---

