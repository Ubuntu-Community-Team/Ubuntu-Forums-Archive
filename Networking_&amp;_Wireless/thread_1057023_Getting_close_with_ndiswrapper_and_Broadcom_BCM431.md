---
title: "Getting close with ndiswrapper and Broadcom BCM4318"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by dan2020 on 2009-02-01
I have spent about a week trying to get wireless working on a Dell Inspirion 530 which is equiped with a broadcom wireless card.  The machine is dual-boot with windows vista 64-bit, and wireless works fine when operating in vista.

Before trying ndiswrapper, I was able to get wireless working with b43-fwcutter, but the connection was unreliable with regards to speed and disconnects, so I decided to try ndiswrapper and see if it works any better.

Currently I'm getting the following results:

> $ uname -a
Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux


> $lspci -nnv
02:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device [1043:100f]
	Flags: bus master, fast devsel, latency 64, IRQ 21
	Memory at fddfe000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: ndiswrapper
	Kernel modules: ssb


The windows driver seems to be isntalled correctly.
> $ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)


I had to use a work-around to remove ndiswrapper and ssb and then reinsert using modprobe in rc.local.  That's why you see a deregistration here.  If I don't do this, then I get nothing out of iwconifg.
> $ dmesg | grep -e wlan -e ndis
[   11.015366] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   11.154214] usbcore: registered new interface driver ndiswrapper
[   29.532681] usbcore: deregistering interface driver ndiswrapper
[   29.623063] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   29.782086] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[   29.784937] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[   29.785302] ndiswrapper 0000:02:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   29.793082] ndiswrapper: using IRQ 21
[   30.149658] wlan0: ethernet device 00:23:54:6f:fd:ad using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   30.149718] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   30.151626] usbcore: registered new interface driver ndiswrapper


> $ iwconfig
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


> 
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:9b:1f:d7:65  
          inet addr:xxx.xxx.xxx.xxx  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2149440 (2.1 MB)  TX bytes:232349 (232.3 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


> 
$ lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:23:54:6f:fd:ad
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,10/12/2006, 4.100. latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g


The output from the lshw command makes me think that the card just needs to be enabled, but since this is a desktop machine, there is not a separate enable switch for wireless.  When I previously had b43-fwcutter working, I would see the led on the wireless care come on, but I don't see that now.

Should I be doing something to turn on the wifi card when using ndiswrapper?  I've checked bios, and there is nothing related to turning on wifi.  Is there a config bit somewhere that I need to turn on?

---

### Post by dmizer on 2009-02-01
I believe the native drivers should work for this card now. In early Hardy beta and some of the early Hardy kernels, the native module had problems but it should be working now. Just make sure you have all your updates, and use the restricted drivers manager to upload the firmware.

---

### Post by dan2020 on 2009-02-01
If you mean b43, I tried that, and it didn't work so well - lot's of disconnects and slow throughput.

---

### Post by dmizer on 2009-02-01
Yes, I did mean the b43 module. I haven't seen anyone complaining about this card in a while, so I figured that a majority of the issues had been resolved. Are you sure your running the current kernel?

Otherwise, post the output of:
```
lsmod
```

---

### Post by dan2020 on 2009-02-01
I think this is the latest, or at least, it should be close.

> $ uname -a
Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux


> $ lsmod
Module                  Size  Used by
isofs                  44072  1 
ssb                    46340  0 
ndiswrapper           253696  0 
binfmt_misc            18700  1 
i915                   44928  2 
drm                   110304  3 i915
af_packet              29568  2 
rfcomm                 51104  0 
sco                    20612  2 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,sco,bnep,l2cap
ppdev                  16904  0 
acpi_cpufreq           16400  0 
cpufreq_ondemand       16400  2 
cpufreq_userspace      12420  0 
cpufreq_stats          14468  0 
freq_table             13568  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave      10368  0 
cpufreq_conservative    16392  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
pci_slot               13704  0 
wmi                    15808  0 
video                  29204  0 
output                 11776  1 video
container              12288  0 
battery                21128  0 
ipt_REJECT             11776  1 
xt_comment             10240  1 
ipt_LOG                14468  4 
xt_limit               11268  4 
ipt_addrtype           11136  4 
xt_state               10752  2 
xt_tcpudp              11776  8 
xt_conntrack           13184  2 
ip6_tables             29712  0 
nf_nat_irc             10880  0 
nf_conntrack_irc       14776  1 nf_nat_irc
nf_nat_ftp             11648  0 
nf_nat                 29080  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      24856  6 nf_nat
nf_conntrack_ftp       17720  1 nf_nat_ftp
nf_conntrack           84512  8 xt_state,xt_conntrack,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         11520  1 
ip_tables              28176  1 iptable_filter
x_tables               31752  10 ipt_REJECT,xt_comment,ipt_LOG,xt_limit,ipt_addrtype,xt_state,xt_tcpudp,xt_conntrack,ip6_tables,ip_tables
ac                     13448  0 
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
dcdbas                 16688  0 
psmouse                51612  0 
serio_raw              14596  0 
evdev                  20512  6 
pcspkr                 11136  0 
snd_hda_intel         492336  3 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              39280  1 
shpchp                 42140  0 
soundcore              16800  1 snd
iTCO_wdt               21072  0 
pci_hotplug            39216  1 shpchp
iTCO_vendor_support    12420  1 iTCO_wdt
button                 15904  0 
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
ext3                  150544  1 
jbd                    66856  1 ext3
mbcache                17924  1 ext3
loop                   26380  2 
sd_mod                 45864  2 
sr_mod                 24644  1 
cdrom                  47784  1 sr_mod
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
ata_generic            14212  0 
pata_acpi              13568  0 
usbhid                 39776  0 
hid                    59072  1 usbhid
ata_piix               29444  2 
libata                201312  3 ata_generic,pata_acpi,ata_piix
scsi_mod              183160  4 sd_mod,sr_mod,sg,libata
dock                   18464  1 libata
ehci_hcd               49548  0 
uhci_hcd               34336  0 
e1000e                128680  0 
usbcore               175888  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                27424  0 
processor              47800  2 acpi_cpufreq,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  5 


---

### Post by kevdog on 2009-02-01
ndiswrapper is getting trickier to make work these days due to the lack of support and now patching of source depending on kernel version.  But however if you are open to a new approach, you are in luck.  A totally open source Broadcom solution (its open source not unlike b43 except the b43 driver had closed source firmware) is available for you.  It's available for the 4306 and 4318 chipset.  I have it up and running for my 4306 card and think it works great.  Here is the link if you don't mind experimenting a little:
[http://linuxfans.betaserver.org/](http://linuxfans.betaserver.org/)

---

### Post by dan2020 on 2009-02-01
I'm using the new driver now, so it seems to work.  I'll try it for a few days and let you know, if it has any problems.

Thanks!

---

### Post by dmizer on 2009-02-02
> **kevdog said:**
> ndiswrapper is getting trickier to make work these days due to the lack of support and now patching of source depending on kernel version.  But however if you are open to a new approach, you are in luck.  A totally open source Broadcom solution (its open source not unlike b43 except the b43 driver had closed source firmware) is available for you.  It's available for the 4306 and 4318 chipset.  I have it up and running for my 4306 card and think it works great.  Here is the link if you don't mind experimenting a little:
[http://linuxfans.betaserver.org/](http://linuxfans.betaserver.org/)

I knew there was a new driver out there somewhere. Thanks for popping in!

---

### Post by dan2020 on 2009-02-03
This new driver is working quite well so far.  Once thing, I'm seeing the following in my log files:

> 
Feb  3 17:09:02 ubuntu kernel: [35120.643196] wlan0: deauthenticated
Feb  3 17:09:03 ubuntu kernel: [35121.640520] wlan0: authenticate with AP 00:1e:e5:b5:ca:e7
Feb  3 17:09:03 ubuntu kernel: [35121.642275] wlan0: authenticated
Feb  3 17:09:03 ubuntu kernel: [35121.642282] wlan0: associate with AP 00:1e:e5:b5:ca:e7
Feb  3 17:09:03 ubuntu kernel: [35121.644613] wlan0: RX ReassocResp from 00:1e:e5:b5:ca:e7 (capab=0x411 status=0 aid=1)
Feb  3 17:09:03 ubuntu kernel: [35121.644619] wlan0: associated
Feb  3 17:17:01 ubuntu /USR/SBIN/CRON[2025]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  3 17:29:02 ubuntu kernel: [36320.642275] wlan0: deauthenticated
Feb  3 17:29:03 ubuntu kernel: [36321.640577] wlan0: authenticate with AP 00:1e:e5:b5:ca:e7
Feb  3 17:29:03 ubuntu kernel: [36321.643385] wlan0: authenticated
Feb  3 17:29:03 ubuntu kernel: [36321.643394] wlan0: associate with AP 00:1e:e5:b5:ca:e7
Feb  3 17:29:03 ubuntu kernel: [36321.645682] wlan0: RX ReassocResp from 00:1e:e5:b5:ca:e7 (capab=0x411 status=0 aid=1)
Feb  3 17:29:03 ubuntu kernel: [36321.645689] wlan0: associated
Feb  3 17:44:11 ubuntu -- MARK --


Is this normal wireless operation?  Maybe the card goes into power saving mode periodically or something?

---

