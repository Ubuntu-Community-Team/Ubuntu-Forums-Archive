---
title: "Cannot install Ubuntu Touch apps"
date: 2014-01-12
forum: Mobile Technology Discussions (CLOSED)
---

### Post by jan-banan on 2014-01-12
So I've had my Nexus 4 running Ubuntu Touch for a couple of months now, and I haven't installed a single app since it isn't possible. I am aware that the file system is read only, so just now I plugged it in to my computer, adb shell'ed into it and enabled read/write with the mount /dev/loop0/ -o remount,rw command. I ran sudo apt-get update && sudo apt-get upgrade which was all fine, I upgraded some apps. Then I tried sudo apt-get install ureadit which installed properly according to the terminal, but I cannot find it on the phone. I have tried other apps too but I still cannot find them on the phone, not even after I reboot the phone. Altough I tried sudo apt-get install touch-coreapps which gave me some duplicates and a new terminal app, so atleast something works altough it still doesn't work properly since I got duplicates (e.g the file browser and calculator). So is there a way to fix this? Or is it even supposed to work on my version? sudo system-image-cli -i gives the following: 
```
phablet@ubuntu-phablet:/$ sudo system-image-cli -i
[sudo] password for phablet: 
current build number: 100
device name: mako
channel: stable
last update: 2013-11-27 18:07:38
version version: 100
version ubuntu: 20131017
version device: 20131015

```

Any advice on how to fix it?

---

### Post by grahammechanical on 2014-01-13
I have not installed Ubuntu Touch on a mobile device but I have installed Unity 8 and the core apps on my desktop. There will be duplicates simply because Ubuntu Touch is Ubuntu and not a Ubuntu for the phone. The intention is to converge the Touch code base into the desktop code base. The aim is to have a Ubuntu smartphone that can become a PC when connected to a monitor and keyboard. So, the code base will have the standard desktop applications when running as a PC and mobile apps when running on mobile devices.

On my desktop I have duplicates of File Manager, System Settings, Network Manager and any mobile app that has a duplicate on the desktop such as calculator. As for the other problems that you are having, I cannot help you.

Regards.

---

