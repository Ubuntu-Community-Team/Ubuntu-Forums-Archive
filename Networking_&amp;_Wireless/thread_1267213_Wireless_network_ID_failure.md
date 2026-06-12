---
title: "Wireless network ID failure"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by Droidling on 2009-09-15
I'm trying to connect to a wireless network from a Dell Latitude D520 that I just installed Jaunty on. After install I was asked if I wanted to use the proprietary Broadcom driver and I said yes. The wired connection seems to work. With the wired network unplugged I see a list of available networks in the NetworkManager applet. Attempting to connect allows me to enter my 128 bit shared passphrase for the WEP secured network. It never makes a connection, After a few minutes it brings up the network identification required screen again. I tried editing the connection through the GUI. I couldn't find anything that would work.

I've been reading through the other wireless connection threads. I ran lshw to try to check my setup. Not exactly sure how to interpret it. 

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:92:b9:a6:32
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:66:fc:dd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0a:9f:8c:26:a5:7f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Cuba71 on 2009-09-15
It's hard to tell weather the driver you're using is the problem, but I'm attaching a link to Broadcom's Linux driver support page, it has info on the STA driver for the BCM-4311

   [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

### Post by Droidling on 2009-09-15
> **Cuba71 said:**
> It's hard to tell weather the driver you're using is the problem, but I'm attaching a link to Broadcom's Linux driver support page, it has info on the STA driver for the BCM-4311

   [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

About once a year I struggle to get a linux system running. So far the OS has beaten me into submission every time. Assume I know absolutely nothing. I read through the Broadcom readme file, but am still not sure if I need to uninstall an open source driver first. How do I know if I need the kernel patch?

---

### Post by Droidling on 2009-09-16
New information: I was able to connect to a wireless network That has WPA security. Still can't connect to the WEP secured network at my work. This makes me think I have the correct drivers. 

A friend mentioned that it might be the network connection manager. Is there a different connection manager you could recommend?

---

### Post by Droidling on 2009-09-16
CoolHand posted something in another thread that fixed my issue. I'm not sure if this is a bug I should report. Apparently the Network Manager application translated my pass-phrase incorrectly. CoolHand posted this link [http://www.andrewscompanies.com/tools/wep.asp]("http://www.andrewscompanies.com/tools/wep.asp"). Using this to encode my passphrase solved my problem. Is this a bug I should report? How do I go about doing that?

Terry

---

