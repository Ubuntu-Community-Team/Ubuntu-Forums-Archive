---
title: "How to restore wireless driver? ipw2200 screwed up by aircrack"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by flatcoke on 2009-03-18
[COLOR="Red"]UPDATED:

I've solved this problem. To sum up, if you are trying to use aircrack like me, _DO NOT_ use the instructions on their official website. It's heavily outdated. Also, _DO NOT_ install the "newest" ipw drivers or the "newest" ieee80211 drivers you get from Internet. It won't support newer kernels like mine (Intrepid, 2.6.27-11). If you DO mess up, re-install kernel images from Synaptic or (hopefully) read this thread would help.

As far as I know, if you really want to use Aircrack, remember its support to ipw2200 chips (Intel Wireless 2200BG in lspci) is heavily experimental, and some folks are actually working on that. If you want to enable injection on newer kernels, check out [this]("http://ubuntuforums.org/showthread.php?t=1060324") post.

If you know better, please feel more than free to post your solution on how to get aircrack working on ipw2200.[/COLOR]

ORIGINAL POST:
Hi, I've recently installed aircrack and it required me to install ieee80211. I followed the instructions but wasn't able to compile. As it turned out, I have lost my wireless as well. I suppose this must be a screw up of the driver, so I turned to the newest ipw2200 driver on sourceforge, followed the steps, but wasn't able to compile it too. Please help me to find out the best way to restore my wireless to where it was. Your efforts are greatly appreciated.

1 ) Machine Brand and Model (PC/Laptop):
```

HP DV1000 Laptop

```

2 ) Wireless Brand, Model and Wireless Chipset:
```

06:06.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)

```

3 ) check interface:
```

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:b9:e7:db  
          inet addr:10.0.0.3  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2c0:9fff:feb9:e7db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:28189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22479052 (22.4 MB)  TX bytes:3110499 (3.1 MB)
          Interrupt:16 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4658 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4658 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:338468 (338.4 KB)  TX bytes:338468 (338.4 KB)

```
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```


4 ) Check for modules:
```

Module                  Size  Used by
af_packet              25728  2 
i915                   38528  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
openafs               569244  1 
rfcomm                 44432  6 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  12 rfcomm,bnep
ipv6                  263972  12 
ppdev                  15620  0 
speedstep_centrino     15360  0 
cpufreq_ondemand       14988  1 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
freq_table             12672  3 speedstep_centrino,cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
pci_slot               12680  0 
sbshc                  13440  1 sbs
container              11520  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
nls_iso8859_1          12032  2 
nls_cp437              13696  2 
vfat                   18816  2 
fat                    57376  1 vfat
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
mmc_block              17924  2 
tifm_sd                18184  0 
pcmcia                 43052  0 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
psmouse                45200  0 
serio_raw              13444  0 
snd_seq_oss            38528  0 
pcspkr                 10624  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
joydev                 18368  0 
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
tifm_7xx1              13824  0 
mmc_core               58268  3 mmc_block,tifm_sd,sdhci
tifm_core              16028  2 tifm_sd,tifm_7xx1
evdev                  17696  13 
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
btusb                  19736  0 
bluetooth              61924  13 rfcomm,bnep,sco,l2cap,btusb
video                  25232  0 
output                 11008  1 video
wmi                    14504  0 
battery                18436  0 
ac                     12292  0 
button                 14224  0 
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ata_piix               24580  3 
pata_acpi              12160  0 
8139cp                 27520  0 
ata_generic            12932  0 
libata                178208  3 ata_piix,pata_acpi,ata_generic
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ohci1394               37936  0 
ieee1394               96324  2 sbp2,ohci1394
8139too                31616  0 
mii                    13440  2 8139cp,8139too
uhci_hcd               30736  0 
ehci_hcd               43788  0 
usbcore               149360  5 btusb,usbhid,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

5 ) Kernel boot messages
Code:
```

[   14.257203] ipw2200: Unknown symbol ieee80211_wx_get_encodeext
[   14.257645] ipw2200: Unknown symbol ieee80211_wx_set_encode
[   14.257809] ipw2200: Unknown symbol ieee80211_wx_get_encode
[   14.258238] ipw2200: Unknown symbol ieee80211_txb_free
[   14.258460] ipw2200: Unknown symbol ieee80211_wx_set_encodeext
[   14.258899] ipw2200: Unknown symbol ieee80211_wx_get_scan
[   14.259059] ipw2200: Unknown symbol escape_essid
[   14.259318] ipw2200: Unknown symbol ieee80211_freq_to_channel
[   14.259938] ipw2200: Unknown symbol ieee80211_set_geo
[   14.260492] ipw2200: Unknown symbol ieee80211_rx
[   14.260847] ipw2200: Unknown symbol ieee80211_channel_to_index
[   14.261583] ipw2200: Unknown symbol ieee80211_rx_mgt
[   14.261744] ipw2200: Unknown symbol ieee80211_get_geo
[   14.261987] ipw2200: Unknown symbol free_ieee80211
[   14.262543] ipw2200: Unknown symbol ieee80211_is_valid_channel
[   14.262848] ipw2200: Unknown symbol alloc_ieee80211

```
6 ) Network configuration
```

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:b9:e7:db
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.3 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:06:06.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=24 mingnt=3
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:0d:7b:fe:5e:1e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```


8 ) Ubuntu Version:

```

Intrepid Ibex
Kernel: 2.6.27-11-generic i686

```

10 ) Restarting the network:
```

 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

```

---

### Post by flatcoke on 2009-03-19
It seems like the ieee80211 i got from sourceforge, when installing it, got rid of my existing files and terminated with errors when installing the new one. So I ended up without the ieee80211 module. 
modprobe -l |grep ieee gives me:
```

modprobe -l |grep ieee
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/ieee1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/sbp2.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/pcilynx.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/raw1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/ohci1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/dv1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/eth1394.ko
/lib/modules/2.6.27-11-generic/kernel/drivers/ieee1394/video1394.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.27-11-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko

```
But there were no such directory named ieee80211 there, let alone the ko files. What should I do now? trying to install ieee80211 from sourceforge again gives me the same thing:
```

flatcoke@mm:~/documents/Download/ieee80211-1.2.18$ sudo make
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.27-11-generic for ieee80211 components...
make -C /lib/modules/2.6.27-11-generic/build M=/home/flatcoke/documents/Download/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
/home/flatcoke/documents/Download/ieee80211-1.2.18/Makefile:17: 
/home/flatcoke/documents/Download/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/flatcoke/documents/Download/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/flatcoke/documents/Download/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/flatcoke/documents/Download/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/flatcoke/documents/Download/ieee80211-1.2.18/ieee80211_module.o
/home/flatcoke/documents/Download/ieee80211-1.2.18/ieee80211_module.c: In function &#8216;ieee80211_init&#8217;:
/home/flatcoke/documents/Download/ieee80211-1.2.18/ieee80211_module.c:268: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/flatcoke/documents/Download/ieee80211-1.2.18/ieee80211_module.c:268: error: (Each undeclared identifier is reported only once
/home/flatcoke/documents/Download/ieee80211-1.2.18/ieee80211_module.c:268: error: for each function it appears in.)
/home/flatcoke/documents/Download/ieee80211-1.2.18/ieee80211_module.c: In function &#8216;ieee80211_exit&#8217;:
/home/flatcoke/documents/Download/ieee80211-1.2.18/ieee80211_module.c:297: error: &#8216;proc_net&#8217; undeclared (first use in this function)
make[2]: *** [/home/flatcoke/documents/Download/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/flatcoke/documents/Download/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [modules] Error 2
flatcoke@mm:~/documents/Download/ieee80211-1.2.18$ 

```
It also doesn't help whether you run it ```
sudo make SHELL=bin/bash
``` or not. Upon further inspection of the code, I found that all of the compile errors came from within ```
#ifdef CONFIG_IEEE80211_DEBUG ..... #endif
```, which is pretty interesting. If I comment out these codes and compile, it shows this error instead: ```
/home/flatcoke/documents/Download/ieee80211-1.2.17/ieee80211_tx.c: In function &#8216;ieee80211_classify&#8217;:
/home/flatcoke/documents/Download/ieee80211-1.2.17/ieee80211_tx.c:232: error: &#8216;struct sk_buff&#8217; has no member named &#8216;nh&#8217;

```

---

### Post by flatcoke on 2009-03-19
PLease do help.

---

### Post by flatcoke on 2009-03-19
After a whole day of trail and errors, I think my problem is that I'll need a new ieee80211 module. My original one shipped with intrepid is gone. Since rarely anyone would mess up their modules, there's little instruction on the internet about how to install it. Please help.

---

### Post by flatcoke on 2009-03-19
I reinstalled all my kernel images and linux headers. Now I got ieee80211 loaded. The problem is, once doing ```
sudo modprobe ipw2200
```, it says```
FATAL: Error inserting ipw2200 (/lib/modules/2.6.27-11-generic/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
dmesg gives:
 ```
dmesg |grep ipw
[   15.744056] ipw2200: Unknown parameter `disable_hw_scan'

```. I've booted into 2.6.27-7 too but it's the same error. I've checked the .ko files and all of the ones currently on my system are those came with Live CD. So there must be something wrong outside of kernel.

---

### Post by flatcoke on 2009-03-19
Okay. Last post. I got it all fixed up now, took me 2 days to figure out. The bright side is as a newbie Linux user, I learned a lot about kernels, drivers, and modules. Now back to the topic...

Apparently the ipw2200 driver I got from sourceforge puts a custom configuration file in my /etc/modprobe.d/ directory. It(the downloaded driver) has a parameter which the native module doesn't use. It's called disable_hw_scan as mentioned in the post above. Simply removed the file, I got my wireless up again.

---

### Post by DoxSearch on 2009-03-21
What was the process of repairing this??/ I am stuck without wifi right now.

---

### Post by flatcoke on 2009-03-22
If you just want your wi-fi back and doens't care about injection for now(like me), just simply:

1. mark "linux-image-[YOUR KERNEL VERSION]" and "linux-image-generic" as re-install in Synaptic. Apply.
2. Remove the ipw2200 file(if any, or replace the name with your card chipset) in directory /etc/modprobe.d/ You might need to sudo that.
3. Restart. You won't lose anything if you don't have custom built kernel or custom modules or anything like that.

---

### Post by machinehead101 on 2009-03-25
here this is the easy fix
```

sudo apt-get --reinstall install linux-headers-`uname -r`
```

THEN

```
sudo apt-get --reinstall install linux-image-2.6.27-11-generic
```

THEN restart and you should be good to go

---

