---
title: "WiFI not showing up on ubuntu 11.04"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by jtmcc on 2011-07-08
I just upgraded to 11.04 just this morning and I tried to get on the internet. Under the networking thing there is only wired connections. How do I fix this. I have a dell vostro 1000 with a Dell 1390 WLAN mini-card. Please help.

---

### Post by nm_geo on 2011-07-09
Run these in terminal - paste results 
```

lspci -nn
``````
rfkill list all
``````
sudo lshw -C network
```Those will give us a start..

---

### Post by jtmcc on 2011-07-09
I inputed these commands and came out with the following answers;

Answer to code: [FONT=Verdana][FONT=&quot]lspci -nn

[/FONT][/FONT]  00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10) 
  00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f] 
  00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37] 
  00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38] 
  00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380] 
  00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387] 
  00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388] 
  00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389] 
  00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a] 
  00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b] 
  00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386] 
  00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14) 
  00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c] 
  00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] 
  00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d] 
  00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] 
  00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100] 
  00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101] 
  00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102] 
  00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103] 
  01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200] [1002:5974] 
  05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) 
  08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02) 
  08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19) 
  08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01) 
  


Answer to code: [FONT=&quot]rfkill list all

[/FONT]  0: dell-wifi: Wireless LAN 
        Soft blocked: no 
        Hard blocked: no 
  


Answer to code: [FONT=&quot]sudo lshw -C network

[/FONT]  *-network               
         description: Network controller 
         product: BCM4311 802.11b/g WLAN 
         vendor: Broadcom Corporation 
         physical id: 0 
         bus info: pci@0000:05:00.0 
         version: 01 
         width: 32 bits 
         clock: 33MHz 
         capabilities: pm msi pciexpress bus_master cap_list 
         configuration: driver=b43-pci-bridge latency=0 
         resources: irq:18 memory:c0200000-c0203fff 
    *-network 
         description: Ethernet interface 
         product: BCM4401-B0 100Base-TX 
         vendor: Broadcom Corporation 
         physical id: 0 
         bus info: pci@0000:08:00.0 
         logical name: eth0 
         version: 02 
         serial: 00:1d:09:aa:ca:a0 
         size: 10Mbit/s 
         capacity: 100Mbit/s 
         width: 32 bits 
         clock: 33MHz 
         capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
         configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s 
         resources: irq:21 memory:c0300000-c0301fff 
  
I hope you will be able to fix my wifi problem. Thanks!

---

### Post by nm_geo on 2011-07-11
Go to Synaptic and do a search on _bcm._ Makle sure you have b43-fwcutter and firmware-b43-installer installed. If you have any others please remove them right there.
 
Have you tried to install the STA (wl) driver throught Additional Drivers before. No matter we will figure it out.
 
do a 
 
```
lsmod 
```
 
and
 
```
 dmesg | egrep 'wl|ssb|b43|firmware' 
```

---

### Post by jtmcc on 2011-07-13
Ok, when you say "Search on bcm...make sure u have ONLY..." does that mean i delete all others?

Yes, I have installed the brodcom STA wireless driver using wired connection. It says it is activated.

I ran the codes. This is what resulted.

_lsmod_
Module                  Size  Used by
nls_utf8               12493  1
udf                    83795  1
crc_itu_t              12627  1 udf
parport_pc             32111  0
ppdev                  12849  0
snd_hda_codec_idt      60537  1
snd_hda_intel          24140  2
b44                    35301  0
radeon                896428  3
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
ssb                    45942  1 b44
snd_seq_midi           13132  0
wl                   2642531  0
binfmt_misc            13213  1
ttm                    65184  1 radeon
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         40745  1 radeon
joydev                 17322  0
dell_wmi               12601  0
vboxnetadp             13323  0
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
vboxnetflt             27855  0
vboxdrv               219250  2 vboxnetadp,vboxnetflt
sparse_keymap          13666  1 dell_wmi
drm                   180037  5 radeon,ttm,drm_kms_helper
dell_laptop            13515  0
snd_timer              28659  2 snd_pcm,snd_seq
dcdbas                 14054  1 dell_laptop
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0
i2c_algo_bit           13184  1 radeon
soundcore              12600  1 snd
sp5100_tco             13456  0
shpchp                 32345  0
serio_raw              12990  0
i2c_piix4              13095  0
lib80211               14570  1 wl
ati_agp                13202  0
k8temp                 12872  0
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  0
lp                     13349  0
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  3
sdhci_pci              13623  0
libahci                25548  1 ahci
sdhci                  22720  1 sdhci_pci
pata_atiixp            12968  1
usbhid                 41704  0
hid                    77084  1 usbhid

_dmesg..._

[   19.203880] wl: module license 'MIXED/Proprietary' taints kernel.
[   20.276098] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   20.276107] wl 0000:05:00.0: setting latency timer to 64
[   20.335570] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[   20.368123] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[   20.368137] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[   20.368145] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[   20.368152] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[   20.412384] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[   20.475461] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   20.475471] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   20.475480] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   20.529546] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[   20.558465] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:aa:ca:a0

I hope this helps!

---

### Post by nm_geo on 2011-07-15
Let's try to remove the STA (wl) driver ...

You and I have the same wireless card and I can not get the STA (wl) wireless to work in Natty.  However I can get the b43 driver working and it seems to work pretty well for me.



With wired ethernet connected ..

Yes, do that search on _bcm_  remove all that are installed.

Then install b43-fwcutter and the firmware-b43-installer in Synaptic.

Then reboot..without cable connected.. I think you will then be able to connect to your wireless using the Network-Manager radar looking icon in upper panel

---

### Post by atomicben on 2011-07-15
This is an addendum to what nm_geo is saying.  nm_geo helped me with my broadcom a couple weeks ago.  I made notes to myself.  I'm going to put the notes here. 

Installing wifi for Broadcom b43!

First you need to disable the Broadcom STA drivers and revert to the B43 drivers.

sudo cp /etc/modprobe.d/blacklist.conf /etc/modprobe.d/blacklist.original.conf
sudo gedit /etc/modprobe.d/blacklist.conf
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf

go to System > Administration > Additional Drivers
If Broadcom STA is still there and in use, hit REMOVE.

You may or may not have to reboot at this time.  I suggest you reboot.

Now you have NO wifi drivers because STA is blacklisted and B43 isn't installed yet.

Start Synaptic Package Manager
Search for B43
You need to install 2 packages:
b43-fwcutter (the version I am using is 1:013-2)
firmware-b43-installer (the version I am using is 4.150.10.5-4)

Once you install those, there's a pretty good chance that if you go to System > Administration > Additional Drivers again, it will be listed (STA will be listed too).  Choose the B43 drivers.  Mine started up my wifi card right away but you may have to reboot.

THANKS AGAIN NM_GEO!

---

### Post by nm_geo on 2011-07-16
> **atomicben said:**
> This is an addendum to what nm_geo is saying.  nm_geo helped me with my broadcom a couple weeks ago.  I made notes to myself.  I'm going to put the notes here. 

Installing wifi for Broadcom b43!

First you need to disable the Broadcom STA drivers and revert to the B43 drivers.

sudo cp /etc/modprobe.d/blacklist.conf /etc/modprobe.d/blacklist.original.conf
sudo gedit /etc/modprobe.d/blacklist.conf
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf

go to System > Administration > Additional Drivers
If Broadcom STA is still there and in use, hit REMOVE.

You may or may not have to reboot at this time.  I suggest you reboot.

Now you have NO wifi drivers because STA is blacklisted and B43 isn't installed yet.

Start Synaptic Package Manager
Search for B43
You need to install 2 packages:
b43-fwcutter (the version I am using is 1:013-2)
firmware-b43-installer (the version I am using is 4.150.10.5-4)

Once you install those, there's a pretty good chance that if you go to System > Administration > Additional Drivers again, it will be listed (STA will be listed too).  Choose the B43 drivers.  Mine started up my wifi card right away but you may have to reboot.

THANKS AGAIN NM_GEO!

[COLOR=DeepSkyBlue]**YOU ARE WELCOME**[/COLOR] atomicben..

How is it going jtmcc? Let us know..

Here is the problem with jtmcc's setup he has b44 driver for the ethernet and it needs ssb module.  The STA (wl) wireless driver wants to blacklist ssb module. He needs the b43 driver because he needs the ssb module and it works well on Natty 11.04.

---

### Post by jtmcc on 2011-07-17
Thank you SO much!!!!!!! It worked amazingly! I can get on the wireless network now (instead of switching to and from xp! SLOW!). Thank you so much for your time and effort to help me!:D

---

### Post by nm_geo on 2011-07-17
Please mark solved it may help others.  Glad we found a solution you see the b44 for wired requires the ssb module and STA (wl) tries to blacklist the ssb module.

---

### Post by dennism220 on 2011-07-18
Thanks everyone. This just got me up an running with my first Ubuntu installation. :)

Nice job!

---

### Post by nm_geo on 2011-07-19
> **dennism220 said:**
> Thanks everyone. This just got me up an running with my first Ubuntu installation. :)
 
Nice job!
 
Good deal.. These Solved threads help lots of people. Enjoy..

---

### Post by Bolverksson on 2011-07-20
I just wanted to thank NM and Atomic and even the guy who started this post!!! :D I am new to both Linux and laptops, but I now have a wireless connection with my Dell Inspiron 6400 and its Broadcom 4311.

---

### Post by smadeira on 2011-07-22
This worked very well for my Dell Inspiron 1520.  I now have wireless.  Many thanks to you for having the answer.

---

### Post by RonnieJ on 2011-10-25
> **atomicben said:**
> This is an addendum to what nm_geo is saying.  nm_geo helped me with my broadcom a couple weeks ago.  I made notes to myself.  I'm going to put the notes here. 

Installing wifi for Broadcom b43!

First you need to disable the Broadcom STA drivers and revert to the B43 drivers.

sudo cp /etc/modprobe.d/blacklist.conf /etc/modprobe.d/blacklist.original.conf
sudo gedit /etc/modprobe.d/blacklist.conf
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf

go to System > Administration > Additional Drivers
If Broadcom STA is still there and in use, hit REMOVE.

You may or may not have to reboot at this time.  I suggest you reboot.

Now you have NO wifi drivers because STA is blacklisted and B43 isn't installed yet.

Start Synaptic Package Manager
Search for B43
You need to install 2 packages:
b43-fwcutter (the version I am using is 1:013-2)
firmware-b43-installer (the version I am using is 4.150.10.5-4)

Once you install those, there's a pretty good chance that if you go to System > Administration > Additional Drivers again, it will be listed (STA will be listed too).  Choose the B43 drivers.  Mine started up my wifi card right away but you may have to reboot.

THANKS AGAIN NM_GEO!

I tried this one on ubuntu 10.04 without any luck... now STA and b43 isent showing up in the Hardware drivers... befire STA did... but I need b43 to enable the monitor on my broadcom.. any ideas?

---

