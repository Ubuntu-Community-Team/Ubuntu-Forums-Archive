---
title: "Wifi not detected on 10.04"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by nbulchandani on 2010-04-29
Hello,
just installed ubuntu 10.04 and the wifi networks are not detected as in 9.10.In 9.10 installing bcm-wl helped me.. but here the pacakage does not even  install succesfully....i have installed b43..
Thanks

---

### Post by BrianIsNew on 2010-04-29
Can we see if it's alive?
Open a terminal and post the output of **ifconfig**

Can we see if it's detecting anything?
Post the output of **iwlist scan**

Can we see what you're working with?
Post the output of **lspci**

---

### Post by nbulchandani on 2010-04-30
Hello,
The outputs are as
nishant@nishant-laptop:~$ ifconfig
eth0   
   Link encap:Ethernet  HWaddr 00:21:70:be:30:28  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24080 (24.0 KB)  TX bytes:24080 (24.0 KB)

nishant@nishant-laptop:~$ clear

nishant@nishant-laptop:~$ ifconfig
eth0  
    Link encap:Ethernet  HWaddr 00:21:70:be:30:28  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24080 (24.0 KB)  TX bytes:24080 (24.0 KB)


nishant@nishant-laptop:~$ iwlist scan
lo 
       Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

pan0      Interface doesn't support scanning.


nishant@nishant-laptop:~$ lspci
00:00.0
 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
nishant@nishant-laptop:~$ 

sorry for the formatting..i copied it in a text file from linux....
Thanks

---

### Post by bkratz on 2010-04-30
> **nbulchandani said:**
> Hello,
just installed ubuntu 10.04 and the wifi networks are not detected as in 9.10.In 9.10 installing bcm-wl helped me.. but here the pacakage does not even  install succesfully....i have installed b43..
Thanks


In 9.10 that card was not supported with b43 and had to use the sta driver (bcm-wl......). With the introduction of kernel 2.6.32 or later b43 is supposed to do the job for you. See your card listing here

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

In the Ubuntu/debian sections-- it says to ( with a wired connection)

```
sudo apt-get install b43-fwcutter
```


You may have competing drivers if you tried both sta and b43. 

If you post the output of:

```
lsmod
```

that is LSMOD in lowecase) and also

```
sudo lshw -C network
```

perhaps we can determine which is in control. (that was LSHW in lowercase)

---

### Post by nbulchandani on 2010-05-01
nishant@nishant-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
rfcomm                 33421  4 
ppdev                   5259  0 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
joydev                  8708  0 
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
arc4                    1153  2 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  3 
drm_kms_helper         29297  1 i915
dell_wmi                1793  0 
b43                   157218  0 
drm                   162471  4 i915,drm_kms_helper
sdhci_pci               5470  0 
uvcvideo               56990  0 
psmouse                63245  0 
mac80211              204922  1 b43
intel_agp              24177  2 i915
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
btusb                  10925  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
dell_laptop             6856  0 
sdhci                  15462  1 sdhci_pci
dcdbas                  5422  1 dell_laptop
serio_raw               3978  0 
i2c_algo_bit            5028  1 i915
agpgart                31724  2 drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
cfg80211              126485  2 b43,mac80211
led_class               2864  2 b43,sdhci
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
r8169                  33884  0 
mii                     4381  1 r8169
ieee1394               81181  1 ohci1394
ahci                   32008  3 
ssb                    37336  1 b43
nishant@nishant-laptop:~$ sudo lshw -C network
[sudo] password for nishant: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:be:30:28
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:5000(size=256) memory:f8610000-f8610fff(prefetchable) memory:f8600000-f860ffff(prefetchable) memory:f8620000-f862ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:24:2b:60:a5:58
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

