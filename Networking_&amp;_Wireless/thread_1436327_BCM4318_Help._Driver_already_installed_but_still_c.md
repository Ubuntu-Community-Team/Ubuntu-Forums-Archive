---
title: "BCM4318 Help. Driver already installed but still can't connect."
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by nphls on 2010-03-22
Even though having already spent many hours trying to connect to the internet from Ubuntu, I still haven't done it succesfully.

What I've done so far:

```

nuno@Houdini:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)

```

```

nuno@Houdini:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
**01:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
04:00.0 VGA compatible controller: ATI Technologies Inc R423 UK [Radeon X800SE (PCIE)]
04:00.1 Display controller: ATI Technologies Inc Radeon R423 UK (PCIE) [X800 SE] (Secondary)

```

On the bar at the top, under 'Wireless Networks' it reads: "disconnected".

Any help is greatly appreciated. Thanks.

---

### Post by bkratz on 2010-03-22
> **nphls said:**
> Even though having already spent many hours trying to connect to the internet from Ubuntu, I still haven't done it succesfully.



On the bar at the top, under 'Wireless Networks' it reads: "disconnected".

Any help is greatly appreciated. Thanks.

Since you are using ndiswrapper what version of Ubuntu have you installed, there is a good chance that you are having more than one driver fighting for control

Could you please also post

```
iwconfig
sudo lshw -C network
lsmod
```

using the code tags (#) for readability.

---

### Post by nphls on 2010-03-22
Thanks for your reply.

Here they are:

```

nuno@Houdini:~$ iwconfig
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


```

```

nuno@Houdini:~$ sudo lshw -C network
[sudo] password for nuno: 
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 19
       serial: 00:13:d4:56:25:d7
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:cfefc000-cfefffff ioport:c800(size=256) memory:cfec0000-cfedffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:cfdfe000-cfdfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f3:33:8b:36
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

```

nuno@Houdini:~$ lsmod
Module                  Size  Used by
isofs                  31620  1 
udf                    80900  0 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
b43                   122136  0 
mac80211              181236  1 b43
cfg80211               93052  2 b43,mac80211
ppdev                   6688  0 
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
asus_atk0110            8252  0 
led_class               4096  1 b43
dm_crypt               12928  0 
snd_hda_codec_cmedia     9244  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_cmedia,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
floppy                 54916  0 
sky2                   46560  0 
ssb                    35300  1 b43
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
intel_agp              27484  0 
agpgart                34988  3 ttm,drm,intel_agp
ramzswap                8880  1 
xvmalloc                5180  1 ramzswap
lzo_decompress          2620  1 ramzswap
lzo_compress            2300  1 ramzswap


```

---

### Post by bkratz on 2010-03-22
> **nphls said:**
> Thanks for your reply.


          Tx-Power=0 dBm   

       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:cfdfe000-cfdfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f3:33:8b:36


```

nuno@Houdini:~$ lsmod
Module                  Size  Used by

b43                   122136  0 

ssb                    35300  1 b43




Several issues, and I may have to see what I have listed and add to it since I don't have the original post showing during reply, but I don't even see ndiswrapper listed in the loaded modules, but I do see both b43 and ssb listed, which would probably conflict with ndiswrapper anyway. It might be as simple as

[CODE]sudo modprobe b43
```

but i also see that txpower is listed as 0db which might also be a problem you might try

```
sudo iwconfig wlan0 txpower 15
```

to give it a boost, if an error occurs you might reduce it to 5.
Try these and see if they help.  We may to blacklist ssb, but let's see what happens first.

---

### Post by nphls on 2010-03-23
Here is the terminal log:

```
**nuno@Houdini:~$ sudo modprobe b43**
[sudo] password for nuno: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
**nuno@Houdini:~$ sudo iwconfig wlan0 txpower 15**

```


Now, at the top bar under 'Wirelles Networks' I get 'device not ready'.

Thanks again for your help.

---

### Post by bkratz on 2010-03-23
> **nphls said:**
> Here is the terminal log:

```
**nuno@Houdini:~$ sudo modprobe b43**
[sudo] password for nuno: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
**nuno@Houdini:~$ sudo iwconfig wlan0 txpower 15**

```


Now, at the top bar under 'Wirelles Networks' I get 'device not ready'.

Thanks again for your help.

Can we see a new

```
sudo lshw -C network
sudo iwlist scan

```

---

### Post by nphls on 2010-03-23
```

nuno@Houdini:~$ sudo lshw -C network
[sudo] password for nuno: 
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 19
       serial: 00:13:d4:56:25:d7
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:cfefc000-cfefffff ioport:c800(size=256) memory:cfec0000-cfedffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:cfdfe000-cfdfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f3:33:8b:36
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


```

```

nuno@Houdini:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


```

In the bar at the top, I get 'disconnected'. Probably when I checked eralier I didn't give enough time (I had recently rebooted) to the wirelless card to initialize or something like that.

---

### Post by bkratz on 2010-03-23
Since we don't seem to be making much progress and ndiswrapper doesn't show up anyway in the modules, how about we try to get the b43 driver functional, and ignore ndiswrapper. See this page it specifically talks about your card and making it functional. 

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

The b43 driver should work with it. See about 1/2 way down under the heading Ubuntu/Debian  By the way since we did the " sudo modprobe b43 " 
it disappeared when you rebooted ( we didn't make it permanent).

---

### Post by nphls on 2010-03-24
I think I have already installed that.

```
nuno@Houdini:~$ sudo apt-get install b43-fwcutter
[sudo] password for nuno: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
nuno@Houdini:~$
```

I still don't get a green light in wirelles card.

---

### Post by nphls on 2010-03-24
Any more ideas?

---

### Post by nphls on 2010-03-30
Can anyone please give me any more guidance? Thanks very much.

---

