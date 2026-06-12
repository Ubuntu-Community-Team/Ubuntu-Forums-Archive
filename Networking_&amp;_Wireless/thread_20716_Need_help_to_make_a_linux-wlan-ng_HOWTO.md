---
title: "Need help to make a linux-wlan-ng HOWTO"
date: 2005-03-18
forum: Networking &amp; Wireless
---

### Post by cvalstad on 2005-03-18
I am a pretty new to Linux, and I need help to make my computer (Powerbook G4) connect with a DWL-122 usb wlan adapter. As I have read, many people have this usb adapter and also need help to install the linux-wlan-ng package in order to make it work. I dont have any regular internet connection (only wireless access), and I must therefore download the files I need and use a usb memory stick to transfer them to Ubuntulinux 5.04. I have downloaded the linux-wlan-ng file I need but I am having some problems installing it. 

this is whats happening when I install the linux-wlan file using this command:
sudo apt-get install linux-wlan-ng --> then....

Build Prism2.5 USB (_usb) driver? (y/n) [n]: y

Linux source directory [/usr/src/linux]:
Linux source tree /usr/src/linux is incomplete or missing!
See the HOWTO for a list of FTP sites for current kernel sources.

Configuration failed

make: *** [config] Error 1

What do I need to do? Maybe someone can make detailed HOWTO in order to help everybody that needs wireless access?

---

### Post by lao_V on 2005-04-04
I guess you need to download the linux-headers for your architecture. They are normally installed in /usr/src/linux-headers/architecture. Append that path with /include when compiling your drivers

---

