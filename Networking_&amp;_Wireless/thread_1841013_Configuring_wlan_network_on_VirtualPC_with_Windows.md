---
title: "Configuring wlan network on VirtualPC with Windows XP"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by EgorAnd on 2011-09-08
Hi! I have Ubuntu 11.04 installed on my laptop. I've recently installed VirtualBox and configured a Windows XP SP3 virtual machine. All works fine except of networking: my laptop is connected to my wireless home network and the virtual machine can't see it. I've tried to find the solution in settings, googled for answers but to no avail. Will appreciate any kind of help, thanks in advance.

---

### Post by haqking on 2011-09-08
> **EgorAnd said:**
> Hi! I have Ubuntu 11.04 installed on my laptop. I've recently installed VirtualBox and configured a Windows XP SP3 virtual machine. All works fine except of networking: my laptop is connected to my wireless home network and the virtual machine can't see it. I've tried to find the solution in settings, googled for answers but to no avail. Will appreciate any kind of help, thanks in advance.


Choose NAT from your VM settings, unless you want bridged.  You can vary the adapter from the dropdown list, see attachment for my windows network settings.

NAT is easiest but mine is bridged and has a static IP on my LAN.

Bind it to whatever connection you want to virtualise, wlan0 or eht0 etc

---

### Post by EgorAnd on 2011-09-09
**haqking**, thanks for your answer, it works now!

---

### Post by haqking on 2011-09-09
> **EgorAnd said:**
> **haqking**, thanks for your answer, it works now!


Awesome im glad i could help.

Remember to mark your thread as solved using thread tools to assist others when searching for solutions.

cheers

---

