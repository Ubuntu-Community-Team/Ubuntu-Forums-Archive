---
title: "Wireless chip turned off by Vista?"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by dbourne on 2010-07-08
Summary:  my wireless works fine in Vista - LED comes on and everything works great.  In Ubuntu, the LED for the wireless does not come on and it is not recognized - wireless icon reads 'Networking Disabled'.

More background (information transcribed by 'hand' - sorry for any typos):

Sony Vaio PCG-7Z2L
Dual Boot Vista / Ubuntu 10.04 Linux 2.6.32-22

At first, wireless worked fine.  Then for a while (weeks), things worked as long as I pulled out the power cord and battery, held down the power button for 20 seconds, and then booted up.  Now, things work fine in Vista, but Ubuntu doesn't give me any wireless loving.

Any thoughts?  Is this a Vista issue, and if so is there a workaround?  I have tried doing a hard reboot with Vista running (so it has no time to turn off the wireless card), but that didn't work.  I also turned off all the Vaio and Vista wireless power management I could find, but no dice.

Does this seem like a hardware problem?  Software?  Something based on a recent upgrade?

In case it wasn't obvious, I have made sure the physical wireless switch is on.  I even tried it off to see if somehow Ubuntu had become confused.  Another page suggested booting with it off and turning it on - that didn't work either.

Additional system info follows.  Any help is appreciated!

```
> iwconfig

lo no wireless extensions

eth0 no wireless extensions

wlan- IEE 802.11bg ESSID:off/any
Mode:Managed Access Point: not-associated Tx-power=0 dBm
Retry long limit:7 RTS thr:off framement thr:off
power management:off

> rfkill list

0: phy0: wireless lan
soft blocked: no
hard blocked: no

> lshw -c network

*- network DISABLED
description wireless interface
product: AR5001 wireless network adapeter
vendor: atheros
physical id: 0
bus info: pci@000:06:00.0
logical name: wlan0
version:01
serial: stuff
width: 64 bits
clock: 33 MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=802.11bg
resources: irq:18 memory:fa000000-fa00ffff

> lsmod | grep "ath5k"

ath5k   121792 0
mac80211 204922 1 ath5k
ath 7611 1 ath5k
cfg80211 126485 3 ath5k, mac80211, ath
led_class 2864 1 ath5k

>  dmesg

lots of stuff....
ath5k phy0: atheros ar2325 chip found (MAC: 0xe2 PHY: 0x70)
```

---

### Post by fourpxdirectory on 2010-07-08
There is often a switch on the side, bottom, or front of the laptop that *turns* the card on or *off*.

---

### Post by dbourne on 2010-07-08
Yes - there is a switch right next to the LEDs.  I checked to ensure it was on.  It works in Vista when in the on position, but it does not work in ubuntu, even though it used to work and it appears I still have the appropriate driver loaded....

---

### Post by dbourne on 2010-07-21
Hey folks.  This is for anyone else who stumbles on my posting and has a similar problem.

Somehow, I managed to disable networking.  The fix was surprisingly easy, once I found a mention of it on another thread: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1436828](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1436828).

DawieS says:

"If you right-click on the network Icon, is Network enabled?

If so, and you don't have connection, you can then click on Edit Connections and check your networking parameters."

So, right-click on the network Icon, enable networking, and maybe that will be the fix for you as well.

---

