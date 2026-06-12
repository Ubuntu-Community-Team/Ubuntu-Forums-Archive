---
title: "&quot;iwconfig retry&quot; screwed up my wireless config? (BCM4318"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by vyco10 on 2009-03-04
I recently installed Ubuntu 8.10 on my Dell Latitude 110L laptop. Wireless has worked from the beginning... up until yesterday afternoon (*March 3rd*). I was trying to figure out how to refresh/rescan for wireless connections and, not really knowing what I was doing, typed "iwconfig retry" in terminal and since then the internal wireless card hasn't worked.

My wireless card is the "Broadcom BCM4318 Air Force One" card. I'm really stumped as to what is going on with the card. I tried uninstalling network-manager and installing wicd, but that didn't do anything.

Thanks for your help

---

### Post by Crafty Kisses on 2009-03-04
Try running these commands, see if you get any results:
```
sudo ifdown wlan0
sudo ifup wlan0
```

---

### Post by vyco10 on 2009-03-04
I ran "sudo ifdown wlan0" and got:

```
interface wlan0 not configured
```

...which doesn't make any sense because the card was working yesterday afternoon.

Now, I have since started using an external Linksys Wireless-G 2.4 GHz PCI adapter which works, but that may have caused some problems with the other card and confused something in the configuration. I have no idea. But right now the external Linksys adapter is disconnected and it's not even being recognized right now.

I ran "sudo ifup wlan0" and got:

```
Ignoring unknown interface wlan0=wlan0.
```

[IMG]http://www.websitetoolbox.com/images/boards/smilies/confused.gif[/IMG]

---

### Post by Ayuthia on 2009-03-04
Can you post the result:
```
lshw -C network
```

It might help us see if the wireless module is active and if a logical name has been assigned.

---

### Post by vyco10 on 2009-03-04
> **Ayuthia said:**
> Can you post the result:
```
lshw -C network
```

It might help us see if the wireless module is active and if a logical name has been assigned.

Here is the output from "lshw -C network":

```
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:17:47:24
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a4:33:ac:29
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: a6:ad:c3:f7:e7:15
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by vyco10 on 2009-03-05
I ran across another troubleshooting step-by-step guide when searching Google for the results I got from the commands above, which can be found [here]("http://www.denis-talbot.com/forum/index.php?topic=5578.0;wap2"), and it was saying that I would need to edit the interfaces file in the /etc/network directory. Anyway, this is what is in the interfaces file right now:

```
auto lo
iface lo inet loopback

```

If that helps at all.

---

### Post by vyco10 on 2009-03-05
Bump

---

### Post by vyco10 on 2009-03-06
Again, I could really use some help here. Thanks.

---

### Post by vyco10 on 2009-03-07
> [URL="https://help.ubuntu.com/8.10/internet/C/troubleshooting.html"]Check that the device is on
[/URL]
   1.

      Many wireless network devices can be turned on or off. Check to see if there is a hardware switch, some devices can be switched off from Windows and may need to be turned back on from Windows.


I figured out the problem: my own stupidity. I had forgotten all about hitting fn + F2, which is what turns the wireless card off internally, the day it "stopped working".

---

### Post by Ayuthia on 2009-03-07
Sorry for not posting back earlier, but sometimes you can find out that the switch is off by checking dmesg:
```
dmesg|grep b43
```
Usually the b43 module can tell if the switch is off and will mention it in dmesg.

---

### Post by vyco10 on 2009-03-07
> **Ayuthia said:**
> Sorry for not posting back earlier, but sometimes you can find out that the switch is off by checking dmesg:
```
dmesg|grep b43
```
Usually the b43 module can tell if the switch is off and will mention it in dmesg.

That's alright (*delayed response*). I'm just glad it was something simple and not some obscure configuration I screwed up that would've taken forever to find the fix for... or taken me through a reinstall. lol It was getting me down because I've decided, at least on my laptop, to finally and permanently switch to Ubuntu/Linux. I'd finally found the version of Linux that works with my BCM4318 Air Forece card straight "out of the box" without me having to go to the forums to find out how to install ndiswrapper or whatever and then having wireless crap out on me a few days later.

But anyway, I'm back in the airwaves and riding that wave of Linux freedom to glory. Or something. And thanks for the dmesg command. That will probably save me another headache in a couple of days.

---

### Post by kevdog on 2009-03-08
So what was the problem?

---

### Post by vyco10 on 2009-03-08
> **kevdog said:**
> So what was the problem?

Me. Hitting "fn + F2" on my laptop turns wireless on and off. I had turned it off and forgotten that I had turned it off.

---

