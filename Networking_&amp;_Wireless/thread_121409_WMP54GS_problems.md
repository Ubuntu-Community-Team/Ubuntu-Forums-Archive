---
title: "WMP54GS problems"
date: 2006-01-25
forum: Networking &amp; Wireless
---

### Post by SoAnIs on 2006-01-25
Ok, It's 2 am so this will be brief. I'll expand upon this post later, when I'm awake.
I have this system as a dual boot, from an existing windows install, and the new Ubuntu install. I have experience with linux, but not much with Wireless LANs on Linux.
I do not have a wired networking card (well, I have 2, but I have no way to run wires.)
My wireless networking card is the linksys wmp54gs. (Broadcom 4306 chipset.)

I installed ubuntu just fine, and installed ndiswrapper-utils.
I ran the following commands:
ndiswrapper -i ~/wmp54gs/wmp54gs.inf
ndiswrapper -m
modprobe ndiswrapper

ndiswrapper -l
  Installed ndis drivers:
  wmp54gs driver present, hardware present

I added ndiswrapper to /etc/modules.

There is no wlan0 interface. "sudo ifup wlan0" fails (invalid interface), 
iwconfig gives the following:
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      no wireless extensions.
sit0      no wireless extensions.

SO: I have no net access in Linux, so I can't use apt-get/synaptic. Only wireless is availible. What did I do wrong (besides trying to install an OS at 2 in the morning.)?

---

