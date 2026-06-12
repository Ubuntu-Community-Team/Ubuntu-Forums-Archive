---
title: "Wired Internet gone after adding a wireless device"
date: 2006-01-30
forum: Networking &amp; Wireless
---

### Post by NeoChaosX on 2006-01-30
Okay, I recently got a new wireless adapter for my laptop - a D-Link DWL-G630 (version C2). Since it's based on an Atheros chipset, it was deteced just fine by Kubuntu. However, trying to use it with my wired Ethernet connection ran into trouble. Let me explain my situation first. I'm a student at a university that has a wireless network, and I'm using this adapter to access it's network. However, at home, I use an Ethernet connection to a router on DSL for 'net access, no wireless involved whatsoever. My laptop dual boots both Kubuntu and Windows XP.

Okay, so when I got this adapter and put it in the first time at home, it was to check to see if Kubuntu would see it. It did, and I rebooted to Windows to install the drivers for it there. I then decided to reboot back to KDE, which is when my problems started. When I logged into KDE, connecting to the Internet didn't happen. It seems my system made my new wireless adapter (interface ath0) the new default way to access the Internet.  I tried messing with the Network Settings in KDE, changing so that the gateway would be my wired router's IP and it owuld be accessed from my Ethernet device (interface eth0). No go. I then tried removing the wireless card, and rebooting. Even without the card inserted, KDE still refuses to connect through eth0. So now I have no way to get on the Internet at home with Kubuntu.

My questions is: first, how do I get back my wired Internet? And second, how do I force Kubuntu to use the Ethernet connection as the default, and only use the wireless device as a fallback? I'm not exactly experienced in messing with the /etc/network/interfaces file. Any help here would be appreciated.

---

### Post by bikeboy on 2006-01-30
I have both working on my laptop with the wireless default, but I can turn on the wired when I want through System > Admin > Networking by activating the eth0 device and deactivating the wlan0 device.

Try posting the output of cat /etc/network/interfaces so we can have a look at what it's trying to do.

---

### Post by NeoChaosX on 2006-01-30
Okay, here's /etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet static
        address 192.168.1.12
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 206.13.28.12 206.13.29.12

iface ath0 inet dhcp

auto ath0

```

---

### Post by bikeboy on 2006-01-30
To get it to load eth0 by default try adding
"auto eth0"
without the quotes, after the dns nameservers bit. This won't make it use ethernet with wireless as a fallback but it should allow use of the ethernet by default.

Btw, sorry for misreading before but I gave part of my instructions for Ubuntu not Kubuntu. Not sure of the graphical network stuff under KDE but I might be able to work that out later as I'm mucking around with Knoppix on another computer.

---

### Post by h3xx3r on 2006-01-30
have you tried ..    network-manager   this works for me 
have it auto start on login and you can choose networks with a click of the mouse.

---

### Post by NeoChaosX on 2006-01-30
I've temporarily fixed the problem. I commented out all the lines for static configuration, and making my Ethernet device use DHCP rather than static addresses. However, I really need to have the Ethernet device be static (I need to have ports open on my router in order to do things like file transfer over Gaim,  and this requires a static address), so I'm wondering if there's anyone here who has been able to have both a static Ethernet device and a dynamic wireless device how I'm supposed to set it up that way.

---

### Post by NeoChaosX on 2006-01-30
...can a mod move this to the Hardware section, Neworking specifically?

---

### Post by NeoChaosX on 2006-01-31
Never mind about the move, I've fixed all my problems. I misspelled "auto ath0" as "auto ath 0" during one of my edits. I fixed that, and now my wireless card and Ethernet are working together just fine.

---

