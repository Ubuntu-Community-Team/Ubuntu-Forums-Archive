---
title: "Help! Wireless card disabled, unable to enable it"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by igloo88 on 2010-01-23
I can't connect to the Internet through my wireless card. Plus, it's disabled and I can't enable it. It's grayed-out in the Network Manager on the top panel.

I ran this code in a terminal:

```

*****@ubuntu:~$ sudo lshw -C network
[sudo] password for ******: 
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:9c:17:57
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:f9fff000-f9ffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:8d:75:31
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.80 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:f9bfe000-f9bfffff

```How do i enable it? or do i have to reinstall my wireless drivers?

btw, I'm running Ubuntu 9.10 64 bit

---

### Post by adam814 on 2010-01-23
Have you tried simply bringing up the interface with ifconfig?
```
sudo ifconfig wlan0 up
```

If that doesn't do the trick you should make sure to delete any sections in /etc/network/interfaces that refer to wlan0 or wmaster0.

---

### Post by igloo88 on 2010-01-25
no that didn't work. and all i have in interface is 
```

auto lo
iface lo inet loopback

```

I don't think its the wireless card problem i think its the software it self.
like this is the message i get when start of up my computer.

```

Jan 23 15:16:36 ubuntu avahi: Avahi detected that your currently configured local DNS server serves
Jan 23 15:16:36 ubuntu avahi: a domain .local. This is inherently incompatible with Avahi and thus
Jan 23 15:16:36 ubuntu avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Jan 23 15:16:36 ubuntu avahi: contact your administrator and convince him to use a different DNS domain,
Jan 23 15:16:36 ubuntu avahi: since .local should be used exclusively for Zeroconf technology.
Jan 23 15:16:36 ubuntu avahi: For more information, see http://avahi.org/wiki/AvahiAndUnicastDotLocal

```

---

### Post by chili555 on 2010-01-25
Please let us see:```
rfkill list
```Thanks.

---

### Post by igloo88 on 2010-01-25
ok, here it is.
```

lingam@ubuntu:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by chili555 on 2010-01-25
> Hard blocked: yesThat usually means the hardware wireless switch on the front or side of your laptop has become nudged over to 'off.' Nudge it back and you'll be all set.

---

### Post by igloo88 on 2010-01-25
no it's not. Thats the first thing i checked.

---

### Post by chili555 on 2010-01-25
Let's try something else:```
sudo rmmod -f dell-laptop
rfkill list
```Any joy?

---

### Post by igloo88 on 2010-01-25
IT WORKED! Thank-you!!
But, it seems that I have to run the code every time I login to Ubuntu. Is there a way i can have automatically run the code at startup?

---

### Post by chili555 on 2010-01-25
The module dell-laptop may have some other functions aside from crippling your wireless. If other keys or funtions now do not work correctly, we may have other work to do. Post back if you need more help.```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a single line:```
blacklist dell-laptop
```Proofread, save and close gedit and you should be set.

---

### Post by igloo88 on 2010-01-25
Ya, that did the trick. Thank you again. I'll be sure to post again if run it to more issues.

---

### Post by duclamnguyen on 2010-07-01
Hi Guys,

I know the thread it old but i ran into the exact same problem here. I can't figure it out for the life of me.. so any help would be great.

duclamnguyen@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:67:6f:c9
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:26 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:e1:7d:c9:75
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:c2000000-c200ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

duclamnguyen@ubuntu:~$ sudo rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

This is the blacklist.conf:

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

Thanks in advance,

Lam

---

### Post by duclamnguyen on 2010-07-01
oh and i'm running ubuntu studio 10.04 on the Compag Presario CG50... wireless was working perfectly in ubuntu 10.04 ???

---

### Post by duclamnguyen on 2010-07-01
:D ok guys you can ignore the post above... i installed the network-manager, restarted my computer and wireless was enabled for some reason... beats me...

thanks anyways.

---

