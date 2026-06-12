---
title: "Linksys WMP110 / Ubuntu 8.10 64bit / Dell 630i"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by travist120 on 2009-01-19
My Linksys WMP110 will not work under ndiswrapper or anything else. Is there any way I can get it to work with native drivers? I've tried the Vista drivers and the XP drivers. Ndiswrapper says that the hardware  is present, but network manager doesn't pick that up.

lspci
```

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:05.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
03:08.0 Network controller: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus

```

lsmod
```

Module                  Size  Used by
ndiswrapper           253696  0 
isofs                  44072  1 
udf                    93480  0 
crc_itu_t              10496  1 udf
ipv6                  314312  14 
af_packet              29568  4 
arc4                   10368  2 
ecb                    11520  2 
crypto_blkcipher       27780  1 ecb
rt2500usb              29824  0 
rt2x00usb              20480  1 rt2500usb
rt2x00lib              40576  2 rt2500usb,rt2x00usb
rfkill                 19364  1 rt2x00lib
led_class              13192  1 rt2x00lib
mac80211              253440  2 rt2x00usb,rt2x00lib
cfg80211               37136  2 rt2x00lib,mac80211
binfmt_misc            18700  1 
rfcomm                 51104  0 
sco                    20612  2 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,sco,bnep,l2cap
ppdev                  16904  0 
acpi_cpufreq           16400  0 
cpufreq_stats          14468  0 
cpufreq_ondemand       16400  4 
cpufreq_powersave      10368  0 
cpufreq_conservative    16392  0 
cpufreq_userspace      12420  0 
freq_table             13568  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    22288  0 
wmi                    15808  0 
container              12288  0 
sbshc                  14592  1 sbs
video                  29204  0 
output                 11776  1 video
pci_slot               13704  0 
battery                21128  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
ac                     13448  0 
sbp2                   32652  0 
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
snd_hda_intel         492336  3 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
joydev                 20736  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
usbhid                 39776  0 
dcdbas                 16688  0 
isp1760                29488  0 
evdev                  20512  8 
serio_raw              14596  0 
hid                    59072  1 usbhid
pcspkr                 11136  0 
psmouse                51612  0 
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
nvidia               8118288  48 
i2c_nforce2            15752  0 
i2c_core               36128  2 nvidia,i2c_nforce2
button                 15904  0 
shpchp                 42140  0 
pci_hotplug            39216  1 shpchp
ext3                  150544  1 
jbd                    66856  1 ext3
mbcache                17924  1 ext3
pata_acpi              13568  0 
pata_amd               22020  0 
sr_mod                 24644  1 
cdrom                  47784  1 sr_mod
sd_mod                 45864  3 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
ohci1394               41524  0 
ieee1394              110592  2 sbp2,ohci1394
ata_generic            14212  0 
ohci_hcd               35100  0 
forcedeth              68112  0 
ehci_hcd               49548  0 
sata_nv                35336  3 
libata                201312  4 pata_acpi,pata_amd,ata_generic,sata_nv
usbcore               175888  8 ndiswrapper,rt2500usb,rt2x00usb,usbhid,isp1760,ohci_hcd,ehci_hcd
scsi_mod              183160  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   18464  1 libata
thermal                27424  0 
processor              47800  2 acpi_cpufreq,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  3 

```

uname -mr
```

2.6.27-11-generic x86_64

```

---

### Post by travist120 on 2009-02-08
Sorry to bump.

---

### Post by mfive on 2009-02-11
Hey man. I'm having the SAME issue. 

I can't get my wmp110 to work either.

I can see the networks in network manager, it will even allow me to "connect" to them, but as soon as it says connected and I fire up my browser, I get nothing. No internet connection at all. I can't even ping my router.

Does anybody have any suggestions that can help us??? Even if it's a different wireless card! (Although I do need some sort of rangebooster adapter)

---

### Post by travist120 on 2009-02-22
Still no resolve, I have tried everything I could think of. Some one please help!

---

### Post by mfive on 2009-02-22
Hey, I finally got mine to work. Unfortunately my problem lied in the static IP address that I was assigning my computer to.

I had a linksys router with the gateway 192.168.1.1, and I was assigning my computer a static of ip of 192.168.1.11. When I looked in my router settings, the "default" range for ip addresses was 192.168.1.100 - .150. I then changed my ip address to one in that range (192.168.1.130), and then it started working!

I stil don't even think I've tried it with DHCP.

Is yours static or DHCP? If static, what is your ip address you're assigning it?

---

### Post by travist120 on 2009-02-24
I haven't tried it with a static IP address, but I am having the problem of it using DHCP. And auto-config. I might try it with a static IP.

 All I have to do for that is set an IP out of range from the DHCP server on my linksys router right?

---

### Post by travist120 on 2009-02-28
Nothing, it doesn't even recognize the card

---

