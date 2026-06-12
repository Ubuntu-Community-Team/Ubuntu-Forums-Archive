---
title: "Problem setting up Netgear WNDA3100 in 10.04 in Parallels Desktop"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by abey79 on 2010-08-12
Hello all,

I'm trying to setup a Netgear WNDA3100 (chipset: Atheros 9170) on a brand new Ubuntu Server 10.04 LTS running as virtual machine in Parallels Desktop for Mac. I'm by no means an expert, but I think I've setup everything correctly. In particular, the ar9170usb module is loaded. Yet, I can't seem to be able to have the wlan interface brought to existence and keep getting errors such as "usb 1-1: can't set config #1, error -110".

I suspect Parallels' USB emulation might be the problem, but they became pretty good lately and I haven't run into USB problems for while.

```
abey@ubuntu:~$ uname -r
2.6.32-24-generic-pae
abey@ubuntu:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0846:9010 NetGear, Inc. WNDA3100 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
abey@ubuntu:~$ lsmod
Module                  Size  Used by
ar9170usb              51232  0 
mac80211              205146  1 ar9170usb
led_class               2864  1 ar9170usb
ath                     7611  1 ar9170usb
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_intel8x0           25588  0 
cfg80211              126517  3 ar9170usb,mac80211,ath
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm                70886  2 snd_intel8x0,snd_ac97_codec
snd_timer              19098  1 snd_pcm
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd                    54148  4 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
psmouse                63245  0 
soundcore               6620  1 snd
serio_raw               3978  0 
snd_page_alloc          7172  2 snd_intel8x0,snd_pcm
lp                      7028  0 
shpchp                 28884  0 
parport                32635  1 lp
intel_agp              24415  0 
agpgart                31788  1 intel_agp
floppy                 53080  0 
ne2k_pci                6381  0 
8390                    8385  1 ne2k_pci
abey@ubuntu:~$ dmesg | tail
[   11.989232] intel8x0: measure - unreliable DMA position..
[   11.994244] intel8x0: clocking to 48000
[   19.816394] eth0: no IPv6 routers present
[   64.276065] usb 1-1: USB disconnect, address 3
[   68.828360] usb 1-1: new high speed USB device using ehci_hcd and address 4
[   73.972499] usb 1-1: unable to read config index 0 descriptor/all
[   73.977149] usb 1-1: can't read configurations, error -110
[   74.092391] usb 1-1: new high speed USB device using ehci_hcd and address 5
[   74.262398] usb 1-1: configuration #1 chosen from 1 choice
[   79.260085] usb 1-1: can't set config #1, error -110
abey@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

Any help welcome!

TIA,
Antoine

---

### Post by netmanny on 2010-08-19
Have you tried this ?
[http://wireless.kernel.org/en/users/Drivers/ar9170](http://wireless.kernel.org/en/users/Drivers/ar9170)

---

### Post by Dane-o on 2011-01-06
Hi - I am having the exact same problem.. I've got the right driver installed (ar9170usb), but it just throws the errors after I plug it in:

[  191.604557] usb 1-1: new high speed USB device using ehci_hcd and address 2
[  196.772801] usb 1-1: can't set config #1, error -110
[  496.235455] usb 1-1: USB disconnect, address 2
[  500.200707] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  505.368531] usb 1-1: can't set config #1, error -110
[  780.001706] usb 1-1: USB disconnect, address 3
[ 1771.904862] usb 1-1: new high speed USB device using ehci_hcd and address 4
[ 1777.072602] usb 1-1: can't set config #1, error -110
[ 1789.514886] usb 1-1: USB disconnect, address 4
[ 1801.196251] usb 1-1: new high speed USB device using ehci_hcd and address 5
[ 1806.337333] usb 1-1: unable to read config index 0 descriptor/all
[ 1806.337339] usb 1-1: can't read configurations, error -110
[ 1806.448244] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 1811.616346] usb 1-1: can't set config #1, error -110

the ar9170 driver page doesn't seem to help.. everything there says to make, install, unload/load and it should just work.

Anyone got the same problem and got this working?  my device is a Dlink dwa 160 a2, which uses the ar9170usb chipset.

thanks in advance!

Dane

---

### Post by Dane-o on 2011-01-07
Hey - I have resolved this issue.. I took the spot-the-difference approach and realised that a usb memory stick (that had worked earlier in my session) threw the same messages.

I did a re-install of ubuntu 10.10 under virtual box (for mac), built/installed/loaded the drivers, and it worked perfectly.

So my simplistic summation is that it's an issue with parallels.. I have been a little disappointed with parallels running linux distros - most of the time the 'parallels tools' don't even install (meaning no copy-paste from os x etc etc), and other bugs like this one.  Maybe they spend too much time focusing on windows VM performance?

---

