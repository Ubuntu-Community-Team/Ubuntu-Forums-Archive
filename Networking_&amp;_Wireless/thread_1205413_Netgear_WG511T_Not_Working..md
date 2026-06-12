---
title: "Netgear WG511T Not Working."
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by Falcata on 2009-07-06
My laptop's Netgear WG511T wireless card, which in the past has worked flawlessly in Ubuntu and Fedora, has suddenly stopped working.  And I don't know why.  What are some things I can do as far as the command line or GUI tools that I can use to get it working, or find out why it is not working?

---

### Post by Sankou on 2009-07-06
How did you install the driver for it? Was it detected automatically or did you use ndiswrapper?

---

### Post by Crafty Kisses on 2009-07-06
As stated some more information would be helpful. What are the results of the following commands?
```
lshw -C network
iwconfig
```

---

### Post by Sankou on 2009-07-06
**If you used ndiswrapper**, run this and search for your wireless card to see what driver is being used:

lshw -C Network

The result should be something like this:

*-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wlan0
       version: 02
       serial: 00:16:01:7d:23:25
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes **driver=ndiswrapper+usrmaxg** driverversion=1.5

That's my wireless card, I used ndiswrapper to install it. It should say ndiswrapper +[your driver]

If that's not the result, blacklist the driver thats there and run this:

sudo update-initramfs -k all -u

Then reboot.

---

### Post by Falcata on 2009-07-06
I was not using ndiswrapper, as the driver for this wireless card is built-in, so it works out of the box usually.  Anyways, here's the output for those two commands:

```
~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 78
       serial: 00:b0:d0:05:76:01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x latency=80 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:0f:b5:64:10:45
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
```

```
~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"HM2_HOME"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by superprash2003 on 2009-07-06
post output of **sudo dhclient wlan0**

---

### Post by Falcata on 2009-07-06
I cannot say that this looks like a good result:

```
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0f:b5:64:10:45
Sending on   LPF/wlan0/00:0f:b5:64:10:45
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I will attempt to run a liveCD and see if that works.  Will be using puppy linux because I don't think this laptop's hardware (700mhz pentium3 with 256mb of RAM) is strong enough to handle Ubuntu liveCD.

---

### Post by Falcata on 2009-07-06
The puppy liveCD didn't work.  I'm guessing that the wireless card has outlived itself.

---

### Post by superprash2003 on 2009-07-07
you could try setting up a static ip for your wlan0 interface as it doesnt seem to be getting an ip

---

### Post by Falcata on 2009-07-07
How do I do that?

---

### Post by superprash2003 on 2009-07-08
here is a guide with screenshots [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by Falcata on 2009-07-08
Tried that just now, and it didn't work.  I'm guessing the wireless card probably failed.

---

### Post by nityajacob on 2009-07-17
I just installed Ubuntu and my Netgear WG511T does not work. I am new to Linux. Help please.

---

