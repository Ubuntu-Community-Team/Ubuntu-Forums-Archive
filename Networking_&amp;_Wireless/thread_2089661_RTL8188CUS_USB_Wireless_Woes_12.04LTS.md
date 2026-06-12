---
title: "RTL8188CUS USB Wireless Woes: 12.04LTS"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by Wildscot on 2012-11-29
Hi,

I realise there are a fair few posts on similar subjects on here but I'm getting nowhere. I'll try to give as much information as I can.

These commands I have mainly gleaned from other posts in the last 10 hours or so that this has been driving me mental.

I've a USB dongle which I cannot get working. This is a very minimal install for a project, a 12.04 Server install plus a few additional packages - no GUI.

```
$ uname -r
3.2.0-33-generic-pae
```

First up:

```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 002 Device 002: ID 04d9:1503 Holtek Semiconductor, Inc. Shortboard Lefty
Bus 002 Device 003: ID 192f:0416 Avago Technologies, Pte.
``` 

I've installed the drivers from [Realtek]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CUS") without any errors.

ifconfig doesn't show it but:

```
$ ifconfig -a
eth2      Link encap:Ethernet  HWaddr 00:14:2a:75:6d:7a  
          inet addr:192.168.1.26  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:fe75:6d7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:140634 (140.6 KB)  TX bytes:52299 (52.2 KB)
          Interrupt:19 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2026 (2.0 KB)  TX bytes:2026 (2.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0b:81:81:75:67  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Confirmed by:

```
$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth2
       version: 91
       serial: 00:14:2a:75:6d:7a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.26 latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 ioport:d800(size=256) memory:dfffc000-dfffcfff memory:dffc0000-dffdffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:2
       logical name: wlan0
       serial: 00:0b:81:81:75:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-33-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
```

Try to bring it up:

```
$ ifconfig wlan0 up
SIOCSIFFLAGS: Permission Denied
```

The issue seems to be:

```
$ dmesg | grep -e wlan -e 819
[   16.795746] rtl8192cu: MAC address: 00:0b:81:81:75:67
[   16.795758] rtl8192cu: Board Type 0
[   18.507142] usbcore: registered new interface driver rtl8192cu
[   18.641491] Error: Driver 'rtl8192cu' is already registered, aborting...
```

I've messed around with blacklisting and adding to /etc/modules without any success but I'm too frazzled and confused now. I've put all of that back the way it was.

Any help would be most excellent.

```
$lsmod
Module                  Size  Used by
vesafb                 13516  1 
arc4                   12473  2 
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi
psmouse                86486  0 
cfg80211              178679  2 rtlwifi,mac80211
snd_intel8x0           33455  0 
serio_raw              13027  0 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_timer              28931  1 snd_pcm
snd                    62064  4 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
sis_agp                13165  1 
i2c_sis96x             12743  0 
shpchp                 32325  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  1 lp
sis900                 22729  0 
usbhid                 41906  0 
hid                    77392  1 usbhid
```

If there's anything else that might be useful please just let me know.

Must...
       
sleep...


               now...

---

### Post by ahallubuntu on 2012-11-29
Did you follow this thread?

[http://ubuntuforums.org/showthread.php?t=2076315](http://ubuntuforums.org/showthread.php?t=2076315)

It worked for me - I wrote it and used it with this exact card.

FYI, your lsmod shows that "rtl8192cu" is still loaded and used (and 8192cu isn't), so the blacklisting didn't take effect.  Did you reboot afterward?

Tell us exactly what "messing around" you did with blacklisting and adding the new module name ("8192cu" not "rtl8192cu") to /etc/modules .

---

### Post by jualin on 2012-11-29
Yeah I have the same Network card and installing the drivers from Realtek worked. The ifconfig command may have failed because you did not do the command as the root user
```
sudo ifconfig wlan0 up
``` 
Also, you have to make sure that you have the right version of the driver since they are a couple of "8192". Good luck!

---

### Post by Wildscot on 2012-11-30
ahallubuntu - Thank you!

Following your link I now have the wireless up! I think that must have been the only thread I hadn't seen.

I'd come across the information in other threads but scattered across the posts or vaguely saying to blacklist this and that. Nothing as succinct as your post - thanks again.

Let me see if I can connect and make it stick and then I'll mark this as solved.

---

