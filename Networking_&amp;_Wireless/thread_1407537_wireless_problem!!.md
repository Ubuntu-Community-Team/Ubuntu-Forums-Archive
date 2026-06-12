---
title: "wireless problem!!"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by behzadsh on 2010-02-15
[FONT=Arial]hi, today I was just install ubuntu 9.10 and I've got problem with wireless.
I read other topic but I couldn't fix problem

some information:

**iwconfig:**
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

[B]ifconfig:
[/B][/FONT]```

eth0      Link encap:Ethernet  HWaddr 00:1e:c9:01:e9:a3  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c9ff:fe01:e9a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2621 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2538467 (2.5 MB)  TX bytes:395388 (395.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

**sudo lshw -C network:**
```

  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:c9:01:e9:a3
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v3.04 ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:fe5f0000-fe5fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:3a:28:97:89
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

**lspci:**
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

**lsusb:**
```

Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

**lsmod:**
```

Module                  Size  Used by
binfmt_misc             8356  1 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
ppdev                   6688  0 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
arc4                    1660  2 
ecb                     2524  2 
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
b43                   122136  0 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
uvcvideo               59080  0 
joydev                 10272  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              181236  1 b43
videodev               36736  1 uvcvideo
dell_wmi                2564  0 
iptable_filter          3100  0 
v4l1_compat            14496  2 uvcvideo,videodev
sdhci_pci               7100  0 
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
ip_tables              11692  1 iptable_filter
sdhci                  17472  1 sdhci_pci
dell_laptop             8128  0 
btusb                  11856  2 
lp                      8964  0 
parport                35340  2 ppdev,lp
cfg80211               93052  2 b43,mac80211
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
psmouse                56180  0 
x_tables               16544  1 ip_tables
serio_raw               5280  0 
dcdbas                  7292  1 dell_laptop
led_class               4096  2 b43,sdhci
usbhid                 38208  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
tg3                   109600  0 
ssb                    35300  1 b43
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

```


P.S.
I installed ubuntu on **Dell vostro 1400** laptop

---

### Post by chili555 on 2010-02-15
Please see:  [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themIs your wireless not working because your wired ethernet is plugged in and in use?> eth0      Link encap:Ethernet  HWaddr 00:1e:c9:01:e9:a3  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0


---

### Post by behzadsh on 2010-02-15
It didn't work. I'm using ethernet for getting help ;)
actually I think my wireless is disabled, and I don't know how to enable it.

when I tried "*iwlist wlano scan*",:
```

wlan0     Failed to read scan data : Network is down

```

and when I tried "*ifup wlan0*":
```

Ignoring unknown interface wlan0=wlan0

```

thanks anyway

---

### Post by chili555 on 2010-02-15
How about letting us see:```
dmesg | grep b43
```Thanks.

---

### Post by Cabs21 on 2010-02-15
just to make sure.  Did you install your wireless drivers?  Also is there a switch on the outside of your laptop that would turn the wireless card on/off.(betting there is)  and is it turned ON?

---

### Post by behzadsh on 2010-02-15
After I did***dmesg | grep b43*** I return some error that navigate me to [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43) I read this page and everything solved.

I should say [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) was helpful too.

thanks for your supports dudes :)

---

### Post by behzadsh on 2010-02-17
Once again it didn't work. This time happened after I upgrade my linux kernel for sound problems.
There's no wlan0 interface any more. I tried to do what I've done befor but it didn't work.
Wireless driver is installed, and when I type lsmod -C network, I got network UNCLAIMED for wireless

---

### Post by jane_gjorce on 2010-02-18
Hello!
I have a dell laptop 2.0 GH with 2 GB RAM memory. 9:04 Ubuntu installed but have a problem with the wireless, my wireless on Ubuntu 9:04 does **not work** install **wicd** but again just **not working** so I asked you to help me to tell me what should I do to be able to activate wireless on my laptop
greeting</span>[LEFT][IMG]http://www.google.com/images/cleardot.gif[/IMG][/LEFT]

---

### Post by chili555 on 2010-02-18
> **behzadsh said:**
> Once again it didn't work. This time happened after I upgrade my linux kernel for sound problems.
There's no wlan0 interface any more. I tried to do what I've done befor but it didn't work.
Wireless driver is installed, and when I type lsmod -C network, I got network UNCLAIMED for wirelessWhat does this tell us?```
dmesg | grep b43
```Thanks.

---

### Post by elkoselim on 2010-02-18
I have an HP6735s laptop (bcm4322 wireless adapter) with ubuntu 9.10 (2.6.32-02063208-generic). First of all, I tried to use aircrack-ng. FAILED! :sad: Now, could anyone send me step by step solution for installing driver and how to make bcm4322 work with aircrack-ng.

---

### Post by chili555 on 2010-02-18
@jane
@elko

Please start a new thread. Your questions don't seem relevant to b43 and firmware.

---

### Post by wojox on 2010-02-18
```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```

Got my Dell bcm43.xx working.

---

### Post by behzadsh on 2010-02-18
> **chili555 said:**
> What does this tell us?```
dmesg | grep b43
```Thanks.
nothing!

---

### Post by chili555 on 2010-02-18
Well, then let's load it:```
sudo modprobe b43
```Now is your wireless active? If that does it, we'll take steps to load it automagically on boot.

---

### Post by behzadsh on 2010-02-18
> **chili555 said:**
> Well, then let's load it:```
sudo modprobe b43
```Now is your wireless active? If that does it, we'll take steps to load it automagically on boot.
thanks a lot it works!

---

### Post by chili555 on 2010-02-18
> we'll take steps to load it automagically on boot.Please so:```
sudo su
echo "b43" >> /etc/modules
```It should now load correctly on boot.

---

