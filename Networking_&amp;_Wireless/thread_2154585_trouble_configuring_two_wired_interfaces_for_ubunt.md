---
title: "trouble configuring two wired interfaces for ubuntu server running in Virtualbox"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by chronodekar on 2013-06-15
I have a windows laptop upon which I've installed Virtualbox. The host (windows 7 64bit) has two network interfaces - wired & wireless.

With Virtualbox, I created a system with two network interfaces (both wired) connected to the host system's wired and wireless adapters via bridge configuration (this lets me SSH into the virtual system from the LAN).

Ubuntu server 13.04 was installed as the virtual machine. The initial setup detected two network interfaces and asked me to select a primary one. This is now eth0 (corresponding to the host wired connection).

I moved my laptop to another location where I've only got wireless internet. The host (windows) connects just fine. But my virtual ubuntu system refuses to connect to the network. Any suggestions on how I can get it to work? Internet searching let me to run the following commands,

[IMG]http://imageshack.us/a/img811/8889/lwk.png[/IMG]

and this one,

[IMG]http://imageshack.us/a/img834/4642/x1h.png[/IMG]

Basically, I want to setup the networking so that the virtual system will be connected regardless of me moving the host laptop between wire/wireless areas. Rebooting the virtual system between these shifts is not a problem. Any help would be appreciated.

-chronodekar

---

### Post by houstonbofh on 2013-06-15
You are bridged to a device that does not always exist, so you will not always "detect" the second nic when the system starts.

---

### Post by chronodekar on 2013-06-16
> **houstonbofh said:**
> You are bridged to a device that does not always exist, so you will not always "detect" the second nic when the system starts.

VirtualBox has a setting where you can 'disconnect' the network cable from a wired port. Even if I remove it, ubuntu refuses to use the second NIC.

For my purposes, I found a solution;

[IMG]http://img842.imageshack.us/img842/8427/5ik.png[/IMG] 

Before I turn on the virtual ubuntu system, I just switch over network device to whatever my host windows is using at the moment. It works.

But on the original problem; I'm curious about Ubuntu networking; why doesn't it switch over to the second NIC when the first one is in a disconnected state?

Puzzled,
chronodekar

---

