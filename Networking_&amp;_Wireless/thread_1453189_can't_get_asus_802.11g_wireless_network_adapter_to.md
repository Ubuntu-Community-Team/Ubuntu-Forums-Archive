---
title: "can't get asus 802.11g wireless network adapter to work"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by ryan1414 on 2010-04-12
I am using the latest version of Ubuntu that I installed using the windows wubi installer. i chose the 6GB install option. I have an asus 802.11g wireless network adapter that uses the broadcom BCM43XX chipset.
After i installed I typed in my wifi SSID and password. But when I click on system,administration,hardware drivers, it says this:
 
**No proprietary drivers are in use on this system.**
 
It doesn't even list my asus 802.11g wireless card there.
 
So i then installed the .DEB file named **bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386 **and now my asus 802.11g wireless card is displayed in system,administration,hardware drivers, But when I try to activate it it says this:
 
**install archive() failed.**
 
So i can't activate it. 
 
I tried using a .INF file and ndiswrapper but it doesn't work.
 
So i located these drivers here:
 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
 
But i can't install these drivers because I am a new ubuntu user and I don't understand the Terminal commands(I have looked at the tutorials).
If these drivers had a **.DEB** file then I could just double-click on it and it would install them automatically, but I can't find a .DEB file for the 32bit driver.
Does anyone know how I can convert **hybrid-portsrc-x86_32-v5.60.48.36.tar.gz **into a **.DEB** file so it will automatically install?

---

### Post by pdc on 2010-04-13
if you open a terminal: go to Applications (top left); Accessories; and terminal is at the bottom of the list; if  you type in 

> lspci -v and copy and paste the results back here; folks can see exactly what type of broadcom you have; (and you too can see what you have);

(the terminal has an Edit option on its top menu bar, and copy is listed there)

here is what is called the definitive guide;

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

from your results above, it may help you before you post back again to the forum

---

### Post by ryan1414 on 2010-04-14
-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wlan0
       version: 02
       serial: **REMOVED**
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,02/11/2005, 3.100. latency=64 link=no multicast=yes wireless=IEEE 802.11g

Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 100f
    Flags: bus master, fast devsel, latency 64, IRQ 17
    Memory at feade000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: ndiswrapper
    Kernel modules: ssb

---

### Post by leorolla on 2010-04-15
I just noticed you have ndiswrapper.

Remove it first:
```
sudo apt-get remove ndiswrapper-utils-1.9
echo blacklist ndiswrapper | sudo tee /etc/modprobe.d/blacklist-ndiswrapper.conf

```Reboot and see if you have wireless internet.

If not, try the following (if you can get wired internet).

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install b43-fwcutter

```

---

### Post by leorolla on 2010-04-15
I mean, IF you can get wired connection. Can you?

---

### Post by ryan1414 on 2010-04-15
> **leorolla said:**
> I just noticed you have ndiswrapper.
 
Remove it first:
```
sudo apt-get remove ndiswrapper-utils-1.9
echo blacklist ndiswrapper | sudo tee /etc/modprobe.d/blacklist-ndiswrapper.conf

```Reboot and see if you have wireless internet.
 
If not, try the following (if you can get wired internet).
 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install b43-fwcutter

```
 
ok i'll try these things.  Yes i can get ethernet wired internet, just not WiFi connection.

---

### Post by leorolla on 2010-04-15
I ask if you have Wired Internet because some of these commands require internet.

Don't worry about terminal commands.

I could tell you to open this and that application, to look for this and that etc... but with terminal commands it's just much faster and other people can easily verify that I am giving you the correct solution.

Copy-Pasting terminal commands is much faster for you too:

1. Aplications -> Accessories -> Terminal
2. Select the commands from this Forum with the  mouse
3. Do NOT select anything else with the mouse
4. Go to the terminal
5. Click with the middle mouse button on the terminal

Alternatively

1. Aplications -> Accessories -> Terminal
2. Select the commands from this Forum and Ctrl-V
3. Go to the terminal
4. Shift+Ctrl+V

---

### Post by ryan1414 on 2010-04-15
> **leorolla said:**
> I ask if you have Wired Internet because some of these commands require internet.

Don't worry about terminal commands.

I could tell you to open this and that application, to look for this and that etc... but with terminal commands it's just much faster and other people can easily verify that I am giving you the correct solution.

Copy-Pasting terminal commands is much faster for you too:

1. Aplications -> Accessories -> Terminal
2. Select the commands from this Forum with the  mouse
3. Do NOT select anything else with the mouse
4. Go to the terminal
5. Click with the middle mouse button on the terminal

Alternatively

1. Aplications -> Accessories -> Terminal
2. Select the commands from this Forum and Ctrl-V
3. Go to the terminal
4. Shift+Ctrl+V

my wifi still doesn't connect. it detects the AP but won't connect.

---

### Post by bkratz on 2010-04-15
> **ryan1414 said:**
> my wifi still doesn't connect. it detects the AP but won't connect.

@leorolla has done an excellent job of getting you to the correct driver for your card (b43). However, all the other installations you have tried may result in several different drivers trying to get control of your card. You might want to post the outputs of the following:


```
lsmod
cat /etc/modprobe.d/blacklist.conf
sudo lshw -C network

```

to get more insight.

---

### Post by leorolla on 2010-04-15
Also
```
grep blacklist /etc/modprobe.d/*
```

---

