---
title: "Can't find any wireless networks with Sitecom 54g USB dongle"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by plinders on 2010-12-08
Hi everyone,

Yesterday, I decided to set up Ubuntu again, as a dual boot with Windows 7. I installed it via WUBI, because that was the easiest method.
Anyway, after installing, I noticed I couldn't connect to a WiFi network. In fact, my dongle wouldn't detect any wireless networks. On Windows (from where I'm typing this at the moment) I can find several networks. I do have some experience with Linux and WiFi, but this never happened to me. I have had problems like failing to install drivers via ndiswrapper, and just the general setting up of my dongle. So, I checked if the system detected my dongle, using the commands 'lsusb' and 'iwconfig'. In both occasions, it did detect my dongle and it didn't show any problems whatsoever.
Furthermore, I tried this:
```
sudo -s
ifconfig wlan0 down
ifconfig wlan0 up
iwlist wlan0 scan
```
This resulted in the message that no networks were found.
Wireless networks does show up in the network manager in the top right corner of the screen, all it shows is 'disconnected', no wireless networks as it used to show.

These are my system specs (if relevant)
CPU: AMD Phenom II X4 955 (Black Edition)
RAM: 4gb DDR3
GPU: ATi Radeon HD5750
Mobo: Gigabyte MA770T-UD3
HD: 1Tb Samsung HD103SJ
USB Dongle: Sitecom WL-608 BL

So, I'm kind of stuck, could you help me?
Thanks in advance,
plinders

---

### Post by plinders on 2010-12-09
Anyone?

I HAVE searched the forums for a solution, but most threads are about Broadcom WiFi modules and state as a solution that the user has to install the drivers again via ndiswrapper. However, personally I'm under the impression that this problem is not caused by the lack of drivers (but I may try this method).

---

### Post by TBABill on 2010-12-09
can you copy and paste what is in each of the following files:
/etc/modprobe.d/blacklist.conf
/etc/modules

edit: I believe your device needs to have the Ralink RT2870 driver enabled in order to work. We'll see what is in these files to know if you have the right devices blacklisted (ignored) and the right driver in modules.

---

### Post by plinders on 2010-12-09
> **TBABill said:**
> can you copy and paste what is in each of the following files:
/etc/modprobe.d/blacklist.conf
/etc/modules

edit: I believe your device needs to have the Ralink RT2870 driver enabled in order to work. We'll see what is in these files to know if you have the right devices blacklisted (ignored) and the right driver in modules.

Here you go:

blacklist.conf:
```
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

```

and modules:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

```

Note: I have tried to use ndiswrapper just now, that failed. Same results as without ndiswrapper (I used the vista64 drivers which were on the cd which I got together with the dongle).

---

### Post by TBABill on 2010-12-09
[http://www.matthartley.com/rt2870-linux-driver-on-ubuntu-10-04/](http://www.matthartley.com/rt2870-linux-driver-on-ubuntu-10-04/)

This has a step by step to get the RT2870 going in Ubuntu and rather than retype it here, can you go there and just start at step 1?

---

### Post by plinders on 2010-12-30
> **TBABill said:**
> [http://www.matthartley.com/rt2870-linux-driver-on-ubuntu-10-04/](http://www.matthartley.com/rt2870-linux-driver-on-ubuntu-10-04/)

This has a step by step to get the RT2870 going in Ubuntu and rather than retype it here, can you go there and just start at step 1?

Ok, I followed this guide. (It took some time as I was trying to work with it, after trying to install various drivers via ndiswrapper, which of course failed. I just did a fresh install via wubi.)
I get to the point that I can connect to my network, but then I can't load any webpage (not even the router's page (192.168.1.254)) So, I followed the troubleshooting part of the guide, 

```
Following my instructions to the letter, including NOT trying other driver attempts with this dongle previously yet no connection to be had. Symptoms include the network manager appearing to connect, yet no websites are able to fully load? This would be due to problems with your router acting as a DNS server instead of your ISP.

a) From a terminal, sudo cp /etc/resolv.conf /etc/resolv.conf.auto

b) sudo gedit /etc/dhcp3/dhclient.conf

c)

# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;

save and exit — the above will have you using OpenDNS servers for all of your DNS resolution needs.
```

But after this, there was no improvement.
It might be useful to know, that at the first step of the guide,

```
First thing is to prepare the system for the driver compilation. Therefore it is needed to install certain tools and the headers of the running kernel:

    sudo su
    apt-get install build-essential linux-headers-`uname -r`
    Download this package (alternative mirror):
    Open the file with your favorite text editor:
    gedit /where-ever-it-was-downloaded-to/RT2870_LinuxSTA_V2.3.0.0/os/linux/config.mk

```

I get an error saying 'package build-essential cannot be found'.

I hope you can help, as I feel I'm almost there thanks to you.

---

### Post by plinders on 2010-12-31
It might be interesting to know, when I run iwconfig I get the following:

```
ESSID: SpeedTouchFC9EB1
```

And in the same line, I get the following:
```
RT3070
```
Which is weird, as I'm using the RT2870 driver.

---

### Post by Dlambert on 2010-12-31
When I have to use a wireless adapter in Ubuntu, it will only work when the device is plugged it before boot. I have no clue if this is relevant, but hey. And my experience with WUBI was that my wireless card wouldn't work, but then i tried a live CD install and it worked like a charm.

---

### Post by plinders on 2011-01-01
> **Dlambert said:**
> When I have to use a wireless adapter in Ubuntu, it will only work when the device is plugged it before boot. I have no clue if this is relevant, but hey. And my experience with WUBI was that my wireless card wouldn't work, but then i tried a live CD install and it worked like a charm.

I removed my WUBI install, set up a new partition and installed Ubuntu 10.10. I could find networks immediately, so I connected to my network. Just like before, I couldn't open any webpage (including the router's page) and

```
ping -c 4 www.google.com
``` (for example)

Gave me this message:
```
Network unreachable
```

Furthermore, after about 5 minutes of being connected, I lose my connection, and I can't connect to the network at all.

---

