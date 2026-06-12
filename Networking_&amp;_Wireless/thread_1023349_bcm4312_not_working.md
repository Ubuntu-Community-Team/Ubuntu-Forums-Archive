---
title: "bcm4312 not working"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by mjm461 on 2008-12-27
For ubuntu 8.10... which I am new to.

My wireless works with the default 2.6.27-9 kernel... but I was having some trouble with hibernating.  So I wanted to compile the latest kernel 2.6.28 and when I installed it, wireless stopped working.  bcm43 seems to exits... but does not work.  Also I used to have a wireless STA driver in the hardware drivers, but that disappeared.  The network controller does not seem to be active... Here is the output of lspci -v:

02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Subsystem: Hewlett-Packard Company Device 137c
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at db600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

Any ideas?

---

### Post by polmir on 2008-12-27
Run your Ubuntu from kernel 2.6.27-9 and type in terminal:```
lsmod
```and post output.

Start from new kernel and type in terminal:```
lsmod
```and post output.

---

### Post by Ayuthia on 2008-12-28
Were you trying to use the wl module or the b43?  If you were trying to use the wl module, you will have to compile the module manually because it does not come with the kernel.

If you are using b43, are you sure that the module is loaded?  You should check:
```
lsmod|grep -e b43 -e ssb
```and see that it is there.  You should also check:
```
dmesg|grep b43
```to see if there are any messages about the module.

---

### Post by mjm461 on 2008-12-28
Doesnt matter to me which module I use... as long as it works.  It works both ways when I use the default kernel.  Why do I need to recompile the wl module if I use it?  And where would I get it so I can compile it?

There is no output from either:
```

lsmod|grep -e b43 -e ssb
dmesg|grep b43

```

Here is the output from 2.6.27-9
```

Module                  Size  Used by
af_packet              29568  4 
i915                   44544  2 
drm                   110304  3 i915
binfmt_misc            18700  1 
rfcomm                 51104  0 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
sco                    20612  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,bnep,sco,l2cap
ppdev                  16904  0 
acpi_cpufreq           16400  1 
cpufreq_conservative    16392  0 
cpufreq_userspace      12420  0 
cpufreq_stats          14468  0 
cpufreq_ondemand       16400  1 
freq_table             13568  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave      10368  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
pci_slot               13704  0 
container              12288  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
joydev                 20736  0 
serio_raw              14596  0 
psmouse                51612  0 
uvcvideo               68616  0 
pcspkr                 11136  0 
compat_ioctl32         18176  1 uvcvideo
videodev               46720  2 uvcvideo,compat_ioctl32
v4l1_compat            24580  2 uvcvideo,videodev
evdev                  20512  14 
snd_hda_intel         489264  3 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
ieee80211_crypt_tkip    18048  0 
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
wl                   1085520  0 
ieee80211_crypt        14596  2 ieee80211_crypt_tkip,wl
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
video                  28948  0 
output                 11776  1 video
snd_timer              34320  2 snd_pcm,snd_seq
wmi                    15808  0 
ac                     13448  0 
battery                21128  0 
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 15904  0 
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
intel_agp              39280  1 
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
ext3                  150544  2 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
sd_mod                 45864  4 
crc_t10dif             10240  1 sd_mod
usb_storage            92864  0 
libusual               31784  1 usb_storage
sg                     45408  0 
usbhid                 39776  0 
hid                    59072  1 usbhid
ahci                   43148  3 
libata                200160  1 ahci
scsi_mod              183160  5 sr_mod,sd_mod,usb_storage,sg,libata
dock                   18464  1 libata
r8169                  40196  0 
ehci_hcd               48908  0 
uhci_hcd               34336  0 
usbcore               175376  7 uvcvideo,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                27424  0 
processor              47800  4 acpi_cpufreq,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  3 

```

Here is the output from 2.6.28
```

Module                  Size  Used by
ipv6                  308512  14 
i915                   74248  2 
drm                   122464  3 i915
binfmt_misc            18572  1 
rfcomm                 49440  0 
bridge                 63392  0 
stp                    11396  1 bridge
bnep                   23168  2 
sco                    20228  2 
l2cap                  32640  6 rfcomm,bnep
bluetooth              69668  6 rfcomm,bnep,sco,l2cap
ppdev                  17032  0 
acpi_cpufreq           16784  2 
cpufreq_conservative    16136  0 
cpufreq_userspace      12292  0 
cpufreq_stats          14468  0 
cpufreq_ondemand       16784  1 
freq_table             13824  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave      10240  0 
sbs                    22416  0 
sbshc                  14720  1 sbs
pci_slot               13704  0 
container              12544  0 
iptable_filter         11776  0 
ip_tables              27920  1 iptable_filter
x_tables               31752  1 ip_tables
parport_pc             44968  0 
lp                     19716  0 
parport                49456  3 ppdev,parport_pc,lp
joydev                 20608  0 
pcspkr                 11392  0 
uvcvideo               69640  0 
psmouse                54556  0 
compat_ioctl32         18432  1 uvcvideo
videodev               45440  2 uvcvideo,compat_ioctl32
v4l1_compat            24068  2 uvcvideo,videodev
serio_raw              14724  0 
iTCO_wdt               21456  0 
iTCO_vendor_support    12676  1 iTCO_wdt
evdev                  20128  12 
snd_hda_intel         540340  3 
snd_pcm_oss            51840  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                96392  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11780  0 
snd_seq_oss            42240  0 
snd_seq_midi           16000  0 
snd_rawmidi            33536  1 snd_seq_midi
snd_seq_midi_event     16896  2 snd_seq_oss,snd_seq_midi
video                  28948  0 
output                 11904  1 video
shpchp                 44700  0 
pci_hotplug            38960  1 shpchp
snd_seq                66144  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              32400  2 snd_pcm,snd_seq
snd_seq_device         16532  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77896  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    16192  0 
battery                21256  0 
button                 16032  0 
soundcore              16800  1 snd
ac                     13704  0 
intel_agp              39408  1 
snd_page_alloc         18960  2 snd_hda_intel,snd_pcm
ext3                  148240  2 
jbd                    63528  1 ext3
mbcache                17796  1 ext3
sr_mod                 24388  0 
cdrom                  46632  1 sr_mod
sd_mod                 45480  5 
crc_t10dif             10496  1 sd_mod
usbhid                 35776  0 
hid                    57280  1 usbhid
sg                     41696  0 
usb_storage            92992  0 
libusual               36136  1 usb_storage
ahci                   43404  4 
libata                202848  1 ahci
scsi_mod              186968  5 sr_mod,sd_mod,sg,usb_storage,libata
r8169                  45700  0 
mii                    14848  1 r8169
ehci_hcd               48140  0 
uhci_hcd               33952  0 
usbcore               177200  7 uvcvideo,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                27552  0 
processor              53944  4 acpi_cpufreq,thermal
fan                    13832  0 
fuse                   65344  5 


```

---

### Post by Ayuthia on 2008-12-28
You will need to use the wl driver.  I forgot that you said that you have a 4312 rev 01 card.  You will need to compile the driver from source.  I have not had a chance to try to compile it from source for the 2.6.28 kernel yet to see if the patch from 2.6.27 will work or if something else needs to be done.

---

### Post by kevdog on 2008-12-28
What functionality does the patch provide?

---

