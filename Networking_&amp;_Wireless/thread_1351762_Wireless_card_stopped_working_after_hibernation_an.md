---
title: "Wireless card stopped working after hibernation and hasn't worked since"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by captaincertamen on 2009-12-10
I recently installed Ubuntu on a new laptop. The wireless card worked fine; The computer connected to the network right away with no problems. After a few days of flawless operation, I put the computer into hibernation for the first time. When I restarted it, Ubuntu no longer recognized the existence of my wireless card. Completely shutting down and restarting the computer does not help.

The wireless card is an Intel Mini PCI Wireless 5300 AGN
I'm running Ubuntu 9.10 64-bit; this is the only operating system on the machine

Here's the results of some commands I had found on other posts about similar issues:

iwconfig[FONT=monospace]
[/FONT]lo                no wireless extensions[FONT=monospace]
[/FONT]eth0    no wireless extensions  
[FONT=monospace]
[/FONT]lshw -C network
this returns only information about the Ethernet Controller eth0

What's even more interesting is the little blue light on the laptop that shines if the Wireless Card is turned on. When I boot the computer, the light turns on like it should. As soon as Ubuntu boots, the light goes off. When I log off of Ubuntu, the light comes back on as soon as the screen goes black and goes off again when the computer finishes powering down. My card has no external on/off switch.

I'm new to Ubuntu and love it, but this problem is driving me crazy

---

### Post by ant2ne on 2009-12-10
what are the results of "ifconfig"? If you have a wlan0, can you then "ifconfig wlan0 up"

---

### Post by captaincertamen on 2009-12-11
ifconfig shows only lo and eth0

---

