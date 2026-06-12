---
title: "Just installed ndiswrapper, wlan0 now gone"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by bedake on 2009-03-17
Hi, I have a broadcom 4318 card in my laptop and just installed ndiswrapper in an attempt to get WPA encryption working so I can actually use my laptop at school.

After installing ndiswrapper I no longer have a wlan0 interface.
when entering iwconfig it returns an interface I do not recall seeing before called pan0.

I followed the ndiswrapper guide in the ubuntu wiki

---

### Post by CJ_Hudson on 2009-03-17
Can I recommend "Beginning Ubuntu Linux: Book/DVD Package 2nd Editon: From Novice to Professional (Beginning from Novice to Professional)" by Keir Thomas on Apress? It has a fully comprehensive guide to getting the wireless connection working on your computer in Ubuntu and I couldn't have got mine to work without it.

---

### Post by bedake on 2009-03-17
> **MogBug said:**
> Can I recommend "Beginning Ubuntu Linux: Book/DVD Package 2nd Editon: From Novice to Professional (Beginning from Novice to Professional)" by Keir Thomas on Apress? It has a fully comprehensive guide to getting the wireless connection working on your computer in Ubuntu and I couldn't have got mine to work without it.

Thank you for the recommendation, unfortunately I do not have any money.

Following the guide on: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

To verify ndiswrapper was installed:
ndiswrapper -l
bcmwl5 : driver installed
     device (14E4:4318) present (alternate driver: ssb)



I am about to attempt the installation guide featured on this webpage: [http://onlyubuntu.blogspot.com/2008/10/how-to-setup-broadcom-wireless-bcm4312.html](http://onlyubuntu.blogspot.com/2008/10/how-to-setup-broadcom-wireless-bcm4312.html)




I followed that guide exactly how it said to, yet wlan0 remains nowhere to be found and pan0 remains.

---

### Post by bedake on 2009-03-17
I just entered lshw -c network and the output was:
> WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:b0:79:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.100 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:06:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:99:49:ad:3e:fd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes




I understand pan0 is typically a bluetooth interface?  I am not sure where or when that started showing up but I do no have bluetooth on my laptop.  Is there any explanation for why my wlan0 is not showing up?

iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



I'm not sure what this tells you but here it is:
> 
bedake@bedake-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  2 
i915                   38528  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
sco                    18308  2 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 sco,rfcomm,bnep,l2cap
b44                    35984  0 
ssb                    40580  1 b44
ndiswrapper           196380  0 
ppdev                  15620  0 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
cpufreq_userspace      11396  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
container              11520  0 
pci_slot               12680  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
pcmcia                 43052  0 
evdev                  17696  10 
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
video                  25232  0 
output                 11008  1 video
serio_raw              13444  0 
snd_seq_dummy          10884  0 
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
psmouse                45200  0 
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
tifm_7xx1              13824  0 
mmc_core               58268  1 sdhci
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
tifm_core              16028  1 tifm_7xx1
wmi                    14504  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
battery                18436  0 
ac                     12292  0 
snd_rawmidi            29824  1 snd_seq_midi
button                 14224  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                 10624  0 
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33724  1 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
agpgart                42184  3 drm,intel_agp
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  2 
pata_acpi              12160  0 
8139cp                 27520  0 
ata_generic            12932  0 
libata                178208  3 ata_piix,pata_acpi,ata_generic
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ohci1394               37936  0 
ieee1394               96324  2 sbp2,ohci1394
8139too                31616  0 
mii                    13440  3 b44,8139cp,8139too
uhci_hcd               30736  0 
ehci_hcd               43788  0 
usbcore               149360  4 ndiswrapper,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  1 
bedake@bedake-laptop:~$ 


---

### Post by pytheas22 on 2009-03-18
It looks like your card is not working because of a driver conflict--the ssb module is still claiming it, instead of ndiswrapper.  To solve that problem, run these commands:
```

sudo rmmod b44
sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo depmod -a
sudo modprobe ndiswrapper
```

At this point, the card should come up after a few seconds, assuming that everything else was configured correctly.  If this works, we can make the change permanent (for the time being, these changes will be erased when you reboot your computer).

---

### Post by bedake on 2009-03-19
> **pytheas22 said:**
> It looks like your card is not working because of a driver conflict--the ssb module is still claiming it, instead of ndiswrapper.  To solve that problem, run these commands:
```

sudo rmmod b44
sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo depmod -a
sudo modprobe ndiswrapper
```

At this point, the card should come up after a few seconds, assuming that everything else was configured correctly.  If this works, we can make the change permanent (for the time being, these changes will be erased when you reboot your computer).

Thank you for the response, Since I realized it wasnt working I unblacklisted all the bcm43xx entries in /etc/modeprobe.dl and am currently typing this from the laptop using the bcm drivers.  Should I re blacklist entries and reboot or could I just enter those commands without bothering first?




Well figuring it wouldnt make a permanent difference if I made the attempt without first blacklisting the b43 drivers I attempted entering the commands to which I believe I experienced some errors.

```

bedake@bedake-laptop:~$ sudo rmmod b44
bedake@bedake-laptop:~$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules
bedake@bedake-laptop:~$ sudo rmmod ssb
bedake@bedake-laptop:~$ sudo rmmod ndiswrapper
bedake@bedake-laptop:~$ sudo depmod -a
^[[A^[[Bbedake@bedake-laptop:~$ sudo modprobe ndiswrapper
WARNING: /etc/modprobe.d/blacklist line 35: ignoring bad line starting with 'bcm43xx'
WARNING: /etc/modprobe.d/blacklist line 46: ignoring bad line starting with 'bcm43xx'
WARNING: /etc/modprobe.d/blacklist line 47: ignoring bad line starting with 'b43'
WARNING: /etc/modprobe.d/blacklist line 48: ignoring bad line starting with 'b43legacy'
WARNING: /etc/modprobe.d/blacklist line 50: ignoring bad line starting with 'bcm43xx'

```

output of lshw -c Network:

```
bedake@bedake-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:b0:79:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: wlan0
       version: 02
       serial: 00:90:4b:f5:d0:0c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,02/11/2005, 3.100. ip=192.168.1.128 latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:0f:18:92:ed:91
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
bedake@bedake-laptop:~$ 


```

Am I right that it looks like wlan0 is being controlled by ndiswrapper?  If this is the case, what steps should I take to ensure the bcm drivers are not loaded at startup?  Blacklisting did not seem to work though im sure the error lies with me.

---

### Post by misterfixit on 2009-03-19
> **MogBug said:**
> Can I recommend "Beginning Ubuntu Linux: Book/DVD Package 2nd Editon: From Novice to Professional (Beginning from Novice to Professional)" by Keir Thomas on Apress? It has a fully comprehensive guide to getting the wireless connection working on your computer in Ubuntu and I couldn't have got mine to work without it.

Please send me your copy.  Thanks in advance!

---

### Post by pytheas22 on 2009-03-19
> Am I right that it looks like wlan0 is being controlled by ndiswrapper? If this is the case, what steps should I take to ensure the bcm drivers are not loaded at startup? Blacklisting did not seem to work though im sure the error lies with me.

Yes, ndiswrapper was controlling the card.  If it worked correctly and you want to make the change permanent, you can create a boot script to remove the b43 and bcm43xx modules at boot.  To do so, first type:
```

sudo gedit /etc/init.d/wifi-fix.sh
```

A blank file will open.  Add these lines to it:
```

#!/bin/bash

rmmod b43
rmmod b44
rmmod bcm43xx
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
ifconfig wlan0 up
```

Next, save and close the file.  Then run these commands:
```

cd /etc/init.d
sudo chmod +x wifi-fix.sh
sudo update-rc.d wifi-fix.sh defaults
```

Now the script should automatically take care of the module issues for you.  If not, let me know.

Also, FYI, the reason the blacklist wasn't working, I think, is because you only added the module name to the /etc/modprobe.d/blacklist file.  You need to prefix the module name with the word 'blacklist'.  In other words, if you want to blacklist the b43 driver, you have to add the line:
```

blacklist b43
```

to the file, not just:
```

b43
```

on its own.

---

### Post by CJ_Hudson on 2009-04-14
> **misterfixit said:**
> Please send me your copy.  Thanks in advance!

I asked nicely and my local library got it for me. It cost me 50p by the way. There is quite a lot of interest locally in Ubuntu. Nice to know you are not alone.

  Actually I was wondering if I will have to set that all up again if I upgrade to Jaunty. It really was a great big faff around but now I have my router/peripheral-signal problem sorted out it was worth it for a nice steady connection. 

  I spent many days in the lazy hazy summer pegging away at my keyboard expecting the entire thing to implode at any moment when I could have been lying on the lawn gazing at clouds pondering the significance of existence!

---

