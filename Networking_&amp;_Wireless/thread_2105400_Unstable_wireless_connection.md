---
title: "Unstable wireless connection"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by robertjones on 2013-01-15
Hello there. I'm new to Linux and i just installed Mint 14 on my desktop. I got pretty much  everything working, except my wireless. I can use it right now, i am able to connect, but my connection is absolutely unstable with random spikes and freeze moments.

It appears that rt73 driver ( [http://ubuntuforums.org/showthread.php?t=923387](http://ubuntuforums.org/showthread.php?t=923387) )  would work with this device, but i can't install it. I get an error when i try to execute the 'make' command for rt73-cvs-daily.tar.gz module.

```
 ~/rt73-cvs-2008091809/Module $ make
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
rt73.ko failed to build!
make: *** [module] Error 1

```Since i don't know what's wrong or how to fix this stability problem, here is some things that i think it's relevant.

lsusb:
```
Bus 001 Device 007: ID 07d1:3c07 D-Link System DWA-110 Wireless G Adapter(rev.A1) [Ralink RT2571W]

```ifconfig:
```
eth0      Link encap:Ethernet  HWaddr f4:6d:04:d7:51:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:478947 (478.9 KB)  TX bytes:478947 (478.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:11:af:f3:1a  
          inet addr:192.168.0.110  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:11ff:feaf:f31a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1469681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1358863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1324008934 (1.3 GB)  TX bytes:967128459 (967.1 MB)

```lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: f4:6d:04:d7:51:63
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:50 ioport:d800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: 00:1b:11:af:f3:1a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.5.0-17-generic firmware=1.7 ip=192.168.0.110 link=yes multicast=yes wireless=IEEE 802.11bg
```and finally, from lsmod:

```
Module                  Size  Used by
rt73usb                31296  0 
rt2x00usb              20618  1 rt73usb
rt2x00lib              54891  2 rt73usb,rt2x00usb
mac80211              539908  2 rt2x00usb,rt2x00lib
cfg80211              206566  2 rt2x00lib,mac80211
vesafb                 13797  1 
arc4                   12529  2 
rfcomm                 46619  0 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
snd_hda_intel          33491  7 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
kvm                   414070  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
microcode              22803  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
joydev                 17457  0 
snd_timer              29425  2 snd_pcm,snd_seq
psmouse                95552  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_core              52451  0 
edac_mce_amd           23303  0 
serio_raw              13215  0 
k10temp                13126  0 
asus_atk0110           17646  0 
snd                    78734  23 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13205  0 
fglrx                4715211  142 
wmi                    19070  0 
sp5100_tco             13697  0 
soundcore              15047  1 snd
i2c_piix4              13167  0 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_sunplus            12619  0 
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  3 hid_sunplus,hid_generic,usbhid
firewire_ohci          40401  0 
firewire_core          64368  1 firewire_ohci
crc_itu_t              12707  2 rt73usb,firewire_core
pata_atiixp            13204  0 
r8169                  61650  0
```So, if anyone have any idea what's going on and how to fix, please help me, i would appreciate it
Thank you very much for your time!

---

