---
title: "Have accidently disabled eth0 :( Help!"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by Irishpolyglot on 2010-06-22
In trying to set my computer up as a wireless router, I couldn't find any simple solution so I have tried a few complicated options, which I should not have as I didn't understand the coding and didn't read the instructions carefully enough (I know... n00b mistake...)

So now I have no more Internet connection! I need to connect through the Ethernet but I don't see it any more. I see wifi connections (that I have no access to), but whatever I have done has made the ethernet (eth0) totally invisible.

When I right click and Edit connections it isn't there any more. If I try to add it, it doesn't stick (and I wouldn't know what settings to use anyway).

The instructions I followed were:
[https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint)

So now I'd be better forgetting about setting up Ubuntu as a router - I just want my direct Internet back...
Please advise me on how to return to default access on Ethernet! Is there a simple procedure to go through to cancel what I just did to return to default? 

Help hugely appreciated!!

---

### Post by Irishpolyglot on 2010-06-22
[BUMP]
No ideas? I can't use Internet tethered via my Android phone forever...

---

### Post by TRoe on 2010-06-22
I had a similar issue with eth0 just disappearing after a reboot. I realized it had started after a kernel update. After some digging on the internet, I found out that it was related to ACPI power management. Try adding a kernel argument in Grub that disables this and see if that works. You could also turn it off in BIOS if the feature is available.
 
[http://ubuntuforums.org/showthread.php?t=95425](http://ubuntuforums.org/showthread.php?t=95425)

---

### Post by Irishpolyglot on 2010-06-22
Thanks for the advice, but I don't think it will help in my situation. I didn't perform any kernel upgrades - this was due to unwise reconfiguration of network settings. As far as I know this isn't at all related to power management. I'd rather not start going down other paths of randomly changing settings...

Is there no simple way to get back to where I was before? Can I uninstall some aspect of networking and reinstall it, or restore config files to default in any way?

---

### Post by TRoe on 2010-06-22
Maybe this will help:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
 
While it may not be of much use to you now, to avoid situations like this, I always keep a notebook by my computer and I write down every change that I make so I can undo things later.
 
Does dmesg reveal any hardware issues on boot?
 
Another tactic (although admittedly shotgunning it) would be to go into Synaptic and search for "network" and reinstall everything in the search results that is currently installed...

---

### Post by Irishpolyglot on 2010-06-22
Thanks TRoe!
I can confirm that what has caused the problem would have been playing around with the /etc/network/interfaces and other configurations mentioned on the page you gave. Can someone tell me what I should replace? At the moment it looks like:

```
auto lo
iface lo inet loopback

#isp
auto eth0
iface eth0 inet dhcp
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#Gateway -
auto eth0
iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.rules
post-down iptables-save > /etc/iptables.rules

#Wireless Setup
auto ath0
iface ath0 inet manual
wireless-mode master
wireless-essid pivotpoint

#Bridge interface
auto br0
iface br0 inet static
    address 10.1.1.1
    network 10.1.1.0
    netmask 255.255.255.0
    broadcast 10.1.1.255
    bridge-ports eth1 ath0
```

Wise words from TRoe - from now on EVERY change I make to configurations gets noted and the previous version gets backed up. I'm glad this is only a matter of stupid configuration on my part and no serious damage has likely been caused.

While I've learned my lesson, could someone suggest to me what I should replace in this file? Out of the changes I made I am *hoping* that this configuration file is what messed things up for me. It is extremely unlikely that hardware issues are causing this. The big issue that caused the problem can be located very easily as between the computer and the chair...

---

### Post by Irishpolyglot on 2010-06-22
Solved!
I noticed that I was getting a "device not managed" error where eth0 should have been so I found a thread that suggested changing managed=false to true in 
/etc/NetworkManager/nm-system-settings.conf 
and that seems to have done the trick! I am seeing a bunch of random names under Ethernet, but it's working at least!

Must stop myself from going on a chaotic configuration file rampage in future...

---

