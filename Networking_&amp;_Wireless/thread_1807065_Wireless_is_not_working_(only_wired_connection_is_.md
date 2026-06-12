---
title: "Wireless is not working (only wired connection is working)"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by nn2 on 2011-07-18
Hello,

I am new to ubuntu, just installed it, and I need help with wireless connection. I can connect to the internet with wired connection. The switch for the device is on but this command "sudo lshw -C network" has the following results:

#

[sudo] password for nn: 
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:45:23:7d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full ip=192.168.2.2 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1f:e1:82:55:68
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fe:7d:8c:31:a8:4b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

#


ty nn

---

### Post by johnalexrob on 2011-07-18
I'll be honest, I've been using Linux for almost a year now and didn't know there was a lshw command. 

start with "ifconfig wlan0 up" to activate the device. 

what desktop environment are you using? that would help me determine what to do.

---

### Post by nn2 on 2011-07-19
Hi johnalexrob, ty for reply!

I tried "ifconfig wlan0 up" and i get the message: "SIOCSIFFLAGS: Permission denied"
I am using Dell XPS laptop M1330

---

### Post by johnalexrob on 2011-07-19
try it with sudo (sudo ifconfig wlan0 up).  

what I meant by desktop environment is what windowing system like Gnome or KDE. Does your copy have a letter before it like Xubuntu or Kubuntu? Usually these have different network manager applets and knowing which you're using would help me out. If you're using gnome, try "nm-applet &" and look for an icon to pop up. from that point, you just have to click it and slect your network. If you use KDE, try adding the network manager applet to your panel through the "add items" menu that shows up when right-clicking the panel. 

Good luck!

---

### Post by nn2 on 2011-07-20
Hi again, this time i get the message "SIOCSIFFLAGS: No such file or directory". That can't be good..

At " nm-applet & " i get this message

#
nn@nn-laptop:~$ nm-applet &
[1] 9496
nn@nn-laptop:~$ 
** (nm-applet:9496): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

#


ps: I am using Ubuntu 9.04 Desktop edition, and there is no letter before it, Xubuntu, Kubuntu etc.

---

### Post by nn2 on 2011-07-20
[COLOR=black]Ha! smth changed though. At the network manager icon , under Wireless Networks says "device not ready"[/COLOR] in grey. Before it was nothing there.

---

### Post by nm_geo on 2011-07-20
Let do a few more nn

```
lspci -nn | grep 0280
```
```

lsmod
```

---

### Post by wildmanne39 on 2011-07-20
Hi, have a look at this link and follow the directions for the 4312 card.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)
If you need more help post back here.
Thank you

---

### Post by rMatey on 2011-07-20
Install the ubuntu-restricted-extras (without dashes) in your Software Center to get those drivers.

---

### Post by ahears on 2011-07-20
**Your post shows the device is disabled. It is probably blocked by software.
**To enable the hardware try:**

> 

rfkill list

[B]The output should be similar to:
[/B]
> 

0: Broadcom Bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    [COLOR=Red]Soft blocked: yes[/COLOR]
    Hard blocked: no


**If Wireless is blocked then try:**

> 

rfkill unblock [COLOR=Red][B]wifi
[/B][/COLOR]
**This should re-enable wifi.**

---

### Post by nm_geo on 2011-07-21
Guys he has no wireless driver installed yet and trying 9.04 as I read.

---

### Post by nn2 on 2011-07-21
Hello everyone, thank u for your help!

Problem is solved! 
I have upgraded to 10.04 and I'm using Broadcom B43 wireless driver. 

tx again nn

---

### Post by nm_geo on 2011-07-21
> **nn2 said:**
> Hello everyone, thank u for your help!

Problem is solved! 
I have upgraded to 10.04 and I'm using Broadcom B43 wireless driver. 

tx again nn

Cool thanks for marking solved and you will like 10.04 better and can upgrade for quite a while.

---

### Post by wildmanne39 on 2011-07-21
Hi, thats great I was going to suggest upgrading then fixing the wireless.

---

### Post by nn2 on 2011-07-30
Yes, it works fine this edition and has better graphics :)

---

