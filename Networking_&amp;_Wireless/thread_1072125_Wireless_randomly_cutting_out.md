---
title: "Wireless randomly cutting out"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by HammerOfDoubt on 2009-02-17
Hey there.

Once in a while, say every 20-50 minutes, my connection will completely freeze up and nothing on the internet will load up. And exiting or reclicking the link or restarting Firefox doesn't work. I actually have to wait for the load to time out and then refresh for the site to come up. I thought it was something with the cache, so I made it twice as big, but it still happens just as often.

Any ideas on what it could be?

This is literally the very last "thing" about ubuntu onmy system. I got Wine running the 2 games I play, and allother issues I had are smoothed out. Once I get my connection working normally, I won't ever have to look at Vista again.

---

### Post by superprash2003 on 2009-02-17
try changing your DNS servers to opendns - 208.67.222.222 and 208.67.220.220
Reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by HammerOfDoubt on 2009-02-17
Load times are faster now. I will post again if it hangs anymore.

Thanks

---

### Post by HammerOfDoubt on 2009-02-17
It's still cutting out

Found the sticky about what information to include when asking about wireless issues.

Hope this GIANT wad of info helps someone help me.

----------------

1 ) Machine Brand and Model (PC/Laptop):
Custom Build. Specs in my sig.

2 ) Wireless Brand, Model and Wireless Chipset:
```
ozgar@Hellmouth:~$ lspci
00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller (rev 01)
00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge (rev 01)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
06:01.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
06:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
```

```
ozgar@Hellmouth:~$ lsusb
Bus 008 Device 002: ID 15d9:0a41  
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

3 ) check interface:
```
ozgar@Hellmouth:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:79:d9:0b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:15:79:d9:0c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15219 (15.2 KB)  TX bytes:15219 (15.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:11:e8:dc:3f  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:11ff:fee8:dc3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17515 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19158142 (19.1 MB)  TX bytes:3078214 (3.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-11-E8-DC-3F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

ozgar@Hellmouth:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Diamanda"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:6B:50:27:06   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=60/100  Signal level:-56 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions. 
```

4 ) Check for modules:
```
ozgar@Hellmouth:~$ lsmod
Module                  Size  Used by
ipv6                  314312  14 
aes_x86_64             16384  1 
aes_generic            36392  1 aes_x86_64
af_packet              29568  4 
binfmt_misc            18700  1 
rfcomm                 51104  0 
sco                    20612  2 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
l2cap                  33280  6 rfcomm,bnep
bluetooth              70820  6 rfcomm,sco,bnep,l2cap
ppdev                  16904  0 
acpi_cpufreq           16400  3 
cpufreq_ondemand       16400  1 
cpufreq_userspace      12420  0 
cpufreq_conservative    16392  0 
cpufreq_powersave      10368  0 
cpufreq_stats          14468  0 
freq_table             13568  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
video                  29204  0 
output                 11776  1 video
wmi                    15808  0 
container              12288  0 
pci_slot               13704  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
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
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4                   10368  2 
ecb                    11520  2 
snd_timer              34320  2 snd_pcm,snd_seq
crypto_blkcipher       27780  1 ecb
nvidia               7815240  36 
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
evdev                  20512  6 
i2c_core               36128  1 nvidia
ath9k                 296248  0 
snd                    79432  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              253440  1 ath9k
soundcore              16800  1 snd
iTCO_wdt               21072  0 
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
cfg80211               37136  1 mac80211
button                 15904  0 
pcspkr                 11136  0 
iTCO_vendor_support    12420  1 iTCO_wdt
shpchp                 42140  0 
pci_hotplug            39216  1 shpchp
ext3                  150544  1 
jbd                    66856  1 ext3
mbcache                17924  1 ext3
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
sd_mod                 45864  3 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
usbhid                 39776  0 
hid                    59072  1 usbhid
ata_piix               29444  2 
pata_jmicron           12288  0 
ata_generic            14212  0 
pata_acpi              13568  0 
libata                201312  4 ata_piix,pata_jmicron,ata_generic,pata_acpi
ohci1394               41524  0 
ieee1394              110592  2 sbp2,ohci1394
scsi_mod              183160  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   18464  1 libata
sky2                   61444  0 
uhci_hcd               34336  0 
ehci_hcd               49548  0 
usbcore               175888  4 usbhid,uhci_hcd,ehci_hcd
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

5 ) Kernel boot messages
Big one.
```
[    0.652383] pci 0000:00:1b.0: PME# disabled
[    0.652419] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.652422] pci 0000:00:1c.0: PME# disabled
[    0.652458] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.652461] pci 0000:00:1c.2: PME# disabled
[    0.652497] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.652500] pci 0000:00:1c.4: PME# disabled
[    0.652535] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.652538] pci 0000:00:1c.5: PME# disabled
[    0.652572] PCI: 0000:00:1d.0 reg 20 io port: [9080, 909f]
[    0.652621] PCI: 0000:00:1d.1 reg 20 io port: [9400, 941f]
[    0.652670] PCI: 0000:00:1d.2 reg 20 io port: [9480, 949f]
[    0.652722] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f9fff800, f9fffbff]
[    0.652760] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.652763] pci 0000:00:1d.7: PME# disabled
[    0.652852] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.652854] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.652881] PCI: 0000:00:1f.2 reg 10 io port: [8000, 8007]
[    0.652885] PCI: 0000:00:1f.2 reg 14 io port: [7c00, 7c03]
[    0.652889] PCI: 0000:00:1f.2 reg 18 io port: [7880, 7887]
[    0.652894] PCI: 0000:00:1f.2 reg 1c io port: [7800, 7803]
[    0.652898] PCI: 0000:00:1f.2 reg 20 io port: [7480, 748f]
[    0.652902] PCI: 0000:00:1f.2 reg 24 io port: [7400, 740f]
[    0.652929] PCI: 0000:00:1f.3 reg 10 64bit mmio: [f9fff400, f9fff4ff]
[    0.652939] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[    0.652971] PCI: 0000:00:1f.5 reg 10 io port: [9000, 9007]
[    0.652975] PCI: 0000:00:1f.5 reg 14 io port: [8c00, 8c03]
[    0.652979] PCI: 0000:00:1f.5 reg 18 io port: [8880, 8887]
[    0.652983] PCI: 0000:00:1f.5 reg 1c io port: [8800, 8803]
[    0.652987] PCI: 0000:00:1f.5 reg 20 io port: [8480, 848f]
[    0.652991] PCI: 0000:00:1f.5 reg 24 io port: [8400, 840f]
[    0.653029] PCI: 0000:01:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.653036] PCI: 0000:01:00.0 reg 14 64bit mmio: [c0000000, dfffffff]
[    0.653042] PCI: 0000:01:00.0 reg 1c 64bit mmio: [fa000000, fbffffff]
[    0.653046] PCI: 0000:01:00.0 reg 24 io port: [ac00, ac7f]
[    0.653050] PCI: 0000:01:00.0 reg 30 32bit mmio: [fe7e0000, fe7fffff]
[    0.653085] PCI: bridge 0000:00:01.0 io port: [a000, afff]
[    0.653087] PCI: bridge 0000:00:01.0 32bit mmio: [fa000000, fe7fffff]
[    0.653090] PCI: bridge 0000:00:01.0 64bit mmio pref: [c0000000, dfffffff]
[    0.653124] PCI: bridge 0000:00:1c.0 64bit mmio pref: [f8f00000, f8ffffff]
[    0.653173] PCI: 0000:04:00.0 reg 10 64bit mmio: [feafc000, feafffff]
[    0.653180] PCI: 0000:04:00.0 reg 18 io port: [d800, d8ff]
[    0.653202] PCI: 0000:04:00.0 reg 30 32bit mmio: [feac0000, feadffff]
[    0.653218] pci 0000:04:00.0: supports D1
[    0.653219] pci 0000:04:00.0: supports D2
[    0.653221] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.653225] pci 0000:04:00.0: PME# disabled
[    0.653250] PCI: bridge 0000:00:1c.2 io port: [d000, dfff]
[    0.653252] PCI: bridge 0000:00:1c.2 32bit mmio: [fea00000, feafffff]
[    0.653304] PCI: 0000:03:00.0 reg 10 io port: [cc00, cc07]
[    0.653311] PCI: 0000:03:00.0 reg 14 io port: [c880, c883]
[    0.653319] PCI: 0000:03:00.0 reg 18 io port: [c800, c807]
[    0.653327] PCI: 0000:03:00.0 reg 1c io port: [c480, c483]
[    0.653334] PCI: 0000:03:00.0 reg 20 io port: [c400, c40f]
[    0.653348] PCI: 0000:03:00.0 reg 30 32bit mmio: [fe9f0000, fe9fffff]
[    0.653394] PCI: bridge 0000:00:1c.4 io port: [c000, cfff]
[    0.653397] PCI: bridge 0000:00:1c.4 32bit mmio: [fe900000, fe9fffff]
[    0.653449] PCI: 0000:02:00.0 reg 10 64bit mmio: [fe8fc000, fe8fffff]
[    0.653455] PCI: 0000:02:00.0 reg 18 io port: [b800, b8ff]
[    0.653478] PCI: 0000:02:00.0 reg 30 32bit mmio: [fe8c0000, fe8dffff]
[    0.653494] pci 0000:02:00.0: supports D1
[    0.653495] pci 0000:02:00.0: supports D2
[    0.653496] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.653500] pci 0000:02:00.0: PME# disabled
[    0.653525] PCI: bridge 0000:00:1c.5 io port: [b000, bfff]
[    0.653528] PCI: bridge 0000:00:1c.5 32bit mmio: [fe800000, fe8fffff]
[    0.653565] PCI: 0000:06:01.0 reg 10 32bit mmio: [febf0000, febfffff]
[    0.653629] PCI: 0000:06:03.0 reg 10 32bit mmio: [febef800, febeffff]
[    0.653635] PCI: 0000:06:03.0 reg 14 io port: [ec00, ec7f]
[    0.653667] pci 0000:06:03.0: supports D2
[    0.653668] pci 0000:06:03.0: PME# supported from D2 D3hot D3cold
[    0.653672] pci 0000:06:03.0: PME# disabled
[    0.653702] pci 0000:00:1e.0: transparent bridge
[    0.653704] PCI: bridge 0000:00:1e.0 io port: [e000, efff]
[    0.653707] PCI: bridge 0000:00:1e.0 32bit mmio: [feb00000, febfffff]
[    0.653733] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.653958] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.654058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.654191] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.654289] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.654387] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.654488] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.672943] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.672943] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.672943] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.672943] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.672943] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.672943] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.672943] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.673024] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.676044] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 9F, should be 97 [20080609]
[    0.676076] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.676085] pnp: PnP ACPI init
[    0.676085] ACPI: bus type pnp registered
[    0.676764] pnp: PnP ACPI: found 16 devices
[    0.676764] ACPI: ACPI bus type pnp unregistered
[    0.676764] PCI: Using ACPI for IRQ routing
[    0.696039] NET: Registered protocol family 8
[    0.696041] NET: Registered protocol family 20
[    0.696051] NetLabel: Initializing
[    0.696051] NetLabel:  domain hash size = 128
[    0.696051] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.696051] NetLabel:  unlabeled traffic allowed by default
[    0.696064] PCI-GART: No AMD northbridge found.
[    0.696068] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.696072] hpet0: 4 64-bit timers, 14318180 Hz
[    0.698870] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.698872]    actual entries 65586
[    0.698946] AppArmor: AppArmor Filesystem Enabled
[    0.698962] ACPI: RTC can wake from S4
[    0.700036] Switched to high resolution mode on CPU 0
[    0.700613] Switched to high resolution mode on CPU 1
[    0.700617] Switched to high resolution mode on CPU 3
[    0.700665] Switched to high resolution mode on CPU 2
[    0.712015] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.712022] system 00:07: ioport range 0x290-0x297 has been reserved
[    0.712026] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.712028] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.712029] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.712031] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.712033] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.712035] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.712037] system 00:08: iomem range 0xffa00000-0xffafffff has been reserved
[    0.712039] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.712041] system 00:08: iomem range 0xffe00000-0xffefffff could not be reserved
[    0.712042] system 00:08: iomem range 0xfff00000-0xfffffffe could not be reserved
[    0.712047] system 00:0b: iomem range 0xffc00000-0xffdfffff has been reserved
[    0.712051] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.712052] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.712057] system 00:0e: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.712061] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    0.712062] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
[    0.712064] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[    0.712066] system 00:0f: iomem range 0x100000-0xbfffffff could not be reserved
[    0.717147] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.717149] pci 0000:00:01.0:   IO window: 0xa000-0xafff
[    0.717152] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfe7fffff
[    0.717154] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000dfffffff
[    0.717157] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:05
[    0.717158] pci 0000:00:1c.0:   IO window: disabled
[    0.717161] pci 0000:00:1c.0:   MEM window: disabled
[    0.717164] pci 0000:00:1c.0:   PREFETCH window: 0x000000f8f00000-0x000000f8ffffff
[    0.717168] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.717171] pci 0000:00:1c.2:   IO window: 0xd000-0xdfff
[    0.717174] pci 0000:00:1c.2:   MEM window: 0xfea00000-0xfeafffff
[    0.717177] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.717181] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.717183] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.717187] pci 0000:00:1c.4:   MEM window: 0xfe900000-0xfe9fffff
[    0.717189] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.717194] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.717196] pci 0000:00:1c.5:   IO window: 0xb000-0xbfff
[    0.717199] pci 0000:00:1c.5:   MEM window: 0xfe800000-0xfe8fffff
[    0.717202] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.717206] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.717208] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.717212] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.717214] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.717225] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.717228] pci 0000:00:01.0: setting latency timer to 64
[    0.717234] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.717237] pci 0000:00:1c.0: setting latency timer to 64
[    0.717242] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.717245] pci 0000:00:1c.2: setting latency timer to 64
[    0.717250] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.717253] pci 0000:00:1c.4: setting latency timer to 64
[    0.717258] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.717261] pci 0000:00:1c.5: setting latency timer to 64
[    0.717265] pci 0000:00:1e.0: setting latency timer to 64
[    0.717268] bus: 00 index 0 io port: [0, ffff]
[    0.717269] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.717270] bus: 01 index 0 io port: [a000, afff]
[    0.717271] bus: 01 index 1 mmio: [fa000000, fe7fffff]
[    0.717273] bus: 01 index 2 mmio: [c0000000, dfffffff]
[    0.717274] bus: 01 index 3 mmio: [0, 0]
[    0.717275] bus: 05 index 0 mmio: [0, 0]
[    0.717276] bus: 05 index 1 mmio: [0, 0]
[    0.717277] bus: 05 index 2 mmio: [f8f00000, f8ffffff]
[    0.717278] bus: 05 index 3 mmio: [0, 0]
[    0.717280] bus: 04 index 0 io port: [d000, dfff]
[    0.717281] bus: 04 index 1 mmio: [fea00000, feafffff]
[    0.717282] bus: 04 index 2 mmio: [0, 0]
[    0.717283] bus: 04 index 3 mmio: [0, 0]
[    0.717284] bus: 03 index 0 io port: [c000, cfff]
[    0.717286] bus: 03 index 1 mmio: [fe900000, fe9fffff]
[    0.717287] bus: 03 index 2 mmio: [0, 0]
[    0.717288] bus: 03 index 3 mmio: [0, 0]
[    0.717289] bus: 02 index 0 io port: [b000, bfff]
[    0.717290] bus: 02 index 1 mmio: [fe800000, fe8fffff]
[    0.717291] bus: 02 index 2 mmio: [0, 0]
[    0.717292] bus: 02 index 3 mmio: [0, 0]
[    0.717294] bus: 06 index 0 io port: [e000, efff]
[    0.717295] bus: 06 index 1 mmio: [feb00000, febfffff]
[    0.717296] bus: 06 index 2 mmio: [0, 0]
[    0.717297] bus: 06 index 3 io port: [0, ffff]
[    0.717298] bus: 06 index 4 mmio: [0, ffffffffffffffff]
[    0.717306] NET: Registered protocol family 2
[    0.760120] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.761105] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.765601] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.766215] TCP: Hash tables configured (established 524288 bind 65536)
[    0.766217] TCP reno registered
[    0.776121] NET: Registered protocol family 1
[    0.776210] checking if image is initramfs... it is
[    1.353992] Freeing initrd memory: 8467k freed
[    1.358684] audit: initializing netlink socket (disabled)
[    1.358701] type=2000 audit(1234880792.357:1): initialized
[    1.363457] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.365577] VFS: Disk quotas dquot_6.5.1
[    1.365644] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.365725] msgmni has been set to 7918
[    1.365817] io scheduler noop registered
[    1.365819] io scheduler anticipatory registered
[    1.365820] io scheduler deadline registered
[    1.365926] io scheduler cfq registered (default)
[    1.366054] pci 0000:01:00.0: Boot video device
[    1.366146] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.366166] pcieport-driver 0000:00:01.0: found MSI capability
[    1.366186] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.366222] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.366284] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.366308] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.366333] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.366368] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.366407] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.366480] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.366504] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.366528] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.366563] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.366597] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.366669] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.366693] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.366717] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.366753] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.366788] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.366861] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.366885] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.366910] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.366945] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.366980] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.390807] hpet_resources: 0xfed00000 is busy
[    1.390878] Linux agpgart interface v0.103
[    1.390882] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.392510] brd: module loaded
[    1.392563] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.392646] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.392647] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.393142] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.417645] mice: PS/2 mouse device common for all mice
[    1.417749] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.417770] rtc0: alarms up to one month, y3k, hpet irqs
[    1.417806] cpuidle: using governor ladder
[    1.417808] cpuidle: using governor menu
[    1.418080] TCP cubic registered
[    1.418243] registered taskstats version 1
[    1.418363]   Magic number: 13:111:435
[    1.418503] rtc_cmos 00:03: setting system clock to 2009-02-17 14:26:33 UTC (1234880793)
[    1.418505] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.418507] EDD information not available.
[    1.418538] Freeing unused kernel memory: 540k freed
[    1.418681] Write protecting the kernel read-only data: 4352k
[    1.437161] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.520999] fuse init (API version 7.9)
[    1.535408] ACPI: SSDT BFF8E0D0, 01D2 (r1    AMI   CPU1PM        1 INTL 20060113)
[    1.535724] processor ACPI0007:00: registered as cooling_device0
[    1.535981] ACPI: SSDT BFF8E2B0, 0143 (r1    AMI   CPU2PM        1 INTL 20060113)
[    1.536271] processor ACPI0007:01: registered as cooling_device1
[    1.536529] ACPI: SSDT BFF8E400, 0143 (r1    AMI   CPU3PM        1 INTL 20060113)
[    1.536825] processor ACPI0007:02: registered as cooling_device2
[    1.537080] ACPI: SSDT BFF8E550, 0143 (r1    AMI   CPU4PM        1 INTL 20060113)
[    1.537368] processor ACPI0007:03: registered as cooling_device3
[    1.657868] usbcore: registered new interface driver usbfs
[    1.657886] usbcore: registered new interface driver hub
[    1.657920] usbcore: registered new device driver usb
[    1.659696] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.659709] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.659712] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.659753] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.663658] ehci_hcd 0000:00:1a.7: debug port 1
[    1.663663] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.663676] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
[    1.667623] USB Universal Host Controller Interface driver v3.0
[    1.677598] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    1.677729] usb usb1: configuration #1 chosen from 1 choice
[    1.677750] hub 1-0:1.0: USB hub found
[    1.677757] hub 1-0:1.0: 6 ports detected
[    1.706245] No dock devices found.
[    1.714383] SCSI subsystem initialized
[    1.742810] libata version 3.00 loaded.
[    1.781888] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.781900] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.781903] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.781944] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 2
[    1.781988] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00009800
[    1.782132] usb usb2: configuration #1 chosen from 1 choice
[    1.782151] hub 2-0:1.0: USB hub found
[    1.782157] hub 2-0:1.0: 2 ports detected
[    1.888241] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.888253] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.888257] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.888278] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 3
[    1.888316] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00009880
[    1.888394] usb usb3: configuration #1 chosen from 1 choice
[    1.888413] hub 3-0:1.0: USB hub found
[    1.888418] hub 3-0:1.0: 2 ports detected
[    1.992224] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.992234] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.992237] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.992257] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 4
[    1.992284] uhci_hcd 0000:00:1a.2: irq 18, io base 0x00009c00
[    1.992362] usb usb4: configuration #1 chosen from 1 choice
[    1.992380] hub 4-0:1.0: USB hub found
[    1.992385] hub 4-0:1.0: 2 ports detected
[    2.096269] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.096283] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.096286] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.096309] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    2.100214] ehci_hcd 0000:00:1d.7: debug port 1
[    2.100219] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.100234] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
[    2.112008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.112077] usb usb5: configuration #1 chosen from 1 choice
[    2.112097] hub 5-0:1.0: USB hub found
[    2.112102] hub 5-0:1.0: 6 ports detected
[    2.320113] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.320119] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.320122] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.320152] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    2.320175] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00009080
[    2.320234] usb usb6: configuration #1 chosen from 1 choice
[    2.320251] hub 6-0:1.0: USB hub found
[    2.320256] hub 6-0:1.0: 2 ports detected
[    2.424111] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.424116] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.424119] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.424134] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    2.424160] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00009400
[    2.424222] usb usb7: configuration #1 chosen from 1 choice
[    2.424239] hub 7-0:1.0: USB hub found
[    2.424244] hub 7-0:1.0: 2 ports detected
[    2.528211] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.528216] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.528219] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.528235] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    2.528255] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009480
[    2.528312] usb usb8: configuration #1 chosen from 1 choice
[    2.528328] hub 8-0:1.0: USB hub found
[    2.528333] hub 8-0:1.0: 2 ports detected
[    2.736447] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    2.736469] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    2.736479] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    2.736513] sky2 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.736521] sky2 0000:04:00.0: setting latency timer to 64
[    2.736536] sky2 0000:04:00.0: v1.22 addr 0xfeafc000 irq 18 Yukon-2 EC Ultra rev 3
[    2.736659] pata_acpi 0000:00:1f.5: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    2.736846] sky2 eth0: addr 00:22:15:79:d9:0b
[    2.736861] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.736866] sky2 0000:02:00.0: setting latency timer to 64
[    2.736878] sky2 0000:02:00.0: v1.22 addr 0xfe8fc000 irq 17 Yukon-2 EC Ultra rev 3
[    2.737173] sky2 eth1: addr 00:22:15:79:d9:0c
[    2.737193] ohci1394 0000:06:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.737505] pata_acpi 0000:00:1f.5: setting latency timer to 64
[    2.737514] pata_acpi 0000:00:1f.5: PCI INT B disabled
[    2.737533] pata_acpi 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.737549] pata_acpi 0000:03:00.0: setting latency timer to 64
[    2.737558] pata_acpi 0000:03:00.0: PCI INT A disabled
[    2.790047] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[febef800-febeffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.799005] pata_jmicron 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.799033] pata_jmicron 0000:03:00.0: setting latency timer to 64
[    2.799083] scsi0 : pata_jmicron
[    2.799163] scsi1 : pata_jmicron
[    2.799868] ata1: PATA max UDMA/100 cmd 0xcc00 ctl 0xc880 bmdma 0xc400 irq 16
[    2.799870] ata2: PATA max UDMA/100 cmd 0xc800 ctl 0xc480 bmdma 0xc408 irq 16
[    2.848015] usb 8-1: new low speed USB device using uhci_hcd and address 2
[    3.014801] usb 8-1: configuration #1 chosen from 1 choice
[    3.027811] usbcore: registered new interface driver hiddev
[    3.042810] input: USB Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1:1.0/input/input2
[    3.056757] input,hidraw0: USB HID v1.10 Mouse [USB Mouse] on usb-0000:00:1d.2-1
[    3.056772] usbcore: registered new interface driver usbhid
[    3.057765] usbhid: v2.6:USB HID core driver
[    3.108102] ata_piix 0000:00:1f.2: version 2.12
[    3.108114] ata_piix 0000:00:1f.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    3.108120] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.108159] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.109532] scsi2 : ata_piix
[    3.110217] scsi3 : ata_piix
[    3.111626] ata3: SATA max UDMA/133 cmd 0x8000 ctl 0x7c00 bmdma 0x7480 irq 22
[    3.111631] ata4: SATA max UDMA/133 cmd 0x7880 ctl 0x7800 bmdma 0x7488 irq 22
[    3.592059] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.608946] ata3.00: ATA-8: WDC WD6400AAKS-75A7B0, 01.03B01, max UDMA/133
[    3.608948] ata3.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.608961] ata3.01: ATA-8: WDC WD5000AAKS-65A7B0, 01.03B01, max UDMA/133
[    3.608963] ata3.01: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.624966] ata3.00: configured for UDMA/133
[    3.632175] ata3.01: configured for UDMA/133
[    4.064123] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c00016a8a22]
[    4.108057] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.108138] ata4.01: NODEV after polling detection
[    4.120169] ata4.00: ATAPI: SONY    DVD RW DRU-V200S, 1.60, max UDMA/100
[    4.132174] ata4.00: configured for UDMA/100
[    4.132267] scsi 2:0:0:0: Direct-Access     ATA      WDC WD6400AAKS-7 01.0 PQ: 0 ANSI: 5
[    4.132406] scsi 2:0:0:0: Attached scsi generic sg0 type 0
[    4.132452] scsi 2:0:1:0: Direct-Access     ATA      WDC WD5000AAKS-6 01.0 PQ: 0 ANSI: 5
[    4.132516] scsi 2:0:1:0: Attached scsi generic sg1 type 0
[    4.134119] scsi 3:0:0:0: CD-ROM            SONY     DVD RW DRU-V200S 1.60 PQ: 0 ANSI: 5
[    4.134191] scsi 3:0:0:0: Attached scsi generic sg2 type 5
[    4.134223] ata_piix 0000:00:1f.5: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    4.134227] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    4.134263] ata_piix 0000:00:1f.5: setting latency timer to 64
[    4.134434] scsi4 : ata_piix
[    4.134486] scsi5 : ata_piix
[    4.135570] ata5: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8480 irq 22
[    4.135573] ata6: SATA max UDMA/133 cmd 0x8880 ctl 0x8800 bmdma 0x8488 irq 22
[    4.462563] ata5: SATA link down (SStatus 0 SControl 300)
[    4.790544] ata6: SATA link down (SStatus 0 SControl 300)
[    4.801878] Driver 'sd' needs updating - please use bus_type methods
[    4.801959] sd 2:0:0:0: [sda] 1250263728 512-byte hardware sectors (640135 MB)
[    4.801971] sd 2:0:0:0: [sda] Write Protect is off
[    4.801973] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.801991] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.802041] sd 2:0:0:0: [sda] 1250263728 512-byte hardware sectors (640135 MB)
[    4.802052] sd 2:0:0:0: [sda] Write Protect is off
[    4.802053] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.802071] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.802074]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.812303]  sda1
[    4.812393] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.813502] sd 2:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    4.813514] sd 2:0:1:0: [sdb] Write Protect is off
[    4.813516] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.813534] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.813586] sd 2:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    4.813596] sd 2:0:1:0: [sdb] Write Protect is off
[    4.813597] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    4.813615] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.813617]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    4.840997] sd 2:0:1:0: [sdb] Attached SCSI disk
[    4.846014] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.846016] Uniform CD-ROM driver Revision: 3.20
[    4.846090] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    5.128548] PM: Starting manual resume from disk
[    5.128551] PM: Resume from partition 8:22
[    5.128552] PM: Checking hibernation image.
[    5.128718] PM: Resume from disk failed.
[    5.175210] kjournald starting.  Commit interval 5 seconds
[    5.175227] EXT3-fs: mounted filesystem with ordered data mode.
[    9.879618] udevd version 124 started
[   10.164069] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.167824] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.242509] iTCO_vendor_support: vendor-support=0
[   10.243343] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   10.261155] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   10.296034] ACPI: Power Button (FF) [PWRF]
[   10.296134] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   10.300702] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   10.300782] iTCO_wdt: Found a ICH9R TCO device (Version=2, TCOBASE=0x0860)
[   10.300915] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.328037] ACPI: Power Button (CM) [PWRB]
[   10.437658] ath9k: 0.1
[   10.437697] ath9k 0000:06:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.863728] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   11.063071] nvidia: module license 'NVIDIA' taints kernel.
[   11.338680] phy0: Atheros 5416: mem=0xffffc20000660000, irq=17
[   11.341140] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.341147] nvidia 0000:01:00.0: setting latency timer to 64
[   11.341360] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.82  Tue Nov  4 16:50:05 PST 2008
[   11.758002] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.758021] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.901376] lp: driver loaded but no devices found
[   13.009888] Adding 11880028k swap on /dev/sdb6.  Priority:-1 extents:1 across:11880028k
[   13.555422] EXT3 FS on sdb5, internal journal
[   14.983227] type=1505 audit(1234880807.213:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4418
[   15.081270] type=1505 audit(1234880807.313:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4423
[   15.081420] type=1505 audit(1234880807.313:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4423
[   15.216576] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.685369] ACPI: WMI: Mapper loaded
[   16.479224] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   16.623049] ppdev: user-space parallel port driver
[   18.638123] Bluetooth: Core ver 2.13
[   18.639061] NET: Registered protocol family 31
[   18.639064] Bluetooth: HCI device and connection manager initialized
[   18.639067] Bluetooth: HCI socket layer initialized
[   18.656189] Bluetooth: L2CAP ver 2.11
[   18.656194] Bluetooth: L2CAP socket layer initialized
[   18.669426] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.669431] Bluetooth: BNEP filters: protocol multicast
[   18.712458] Bridge firewalling registered
[   18.726373] Bluetooth: SCO (Voice Link) ver 0.6
[   18.726379] Bluetooth: SCO socket layer initialized
[   18.918509] Bluetooth: RFCOMM socket layer initialized
[   18.918526] Bluetooth: RFCOMM TTY layer initialized
[   18.918528] Bluetooth: RFCOMM ver 1.10
[   22.997216] sky2 eth1: enabling interface
[   23.001477] sky2 eth0: enabling interface
[   23.204633] NET: Registered protocol family 17
[   60.773058] wlan0: authenticate with AP 00:22:6b:50:27:06
[   60.972521] wlan0: authenticate with AP 00:22:6b:50:27:06
[   61.176514] wlan0: authenticate with AP 00:22:6b:50:27:06
[   61.372016] wlan0: authentication with AP 00:22:6b:50:27:06 timed out
[   77.482636] wlan0: authenticate with AP 00:22:6b:50:27:06
[   77.482728] wlan0: authenticate with AP 00:22:6b:50:27:06
[   77.485554] wlan0: authenticated
[   77.485560] wlan0: associate with AP 00:22:6b:50:27:06
[   77.490086] wlan0: RX AssocResp from 00:22:6b:50:27:06 (capab=0x411 status=0 aid=1)
[   77.490089] wlan0: associated
[   77.490237] wlan0 (WE) : Wireless Event too big (338)
[   81.887561] NET: Registered protocol family 10
[   81.888060] lo: Disabled Privacy Extensions
[   81.888592] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   81.888851] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   92.836006] wlan0: no IPv6 routers present

```

6 ) Network configuration
```
ozgar@Hellmouth:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 12
       serial: 00:22:15:79:d9:0b
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 12
       serial: 00:22:15:79:d9:0c
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: wmaster0
       version: 01
       serial: 00:1b:11:e8:dc:3f
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.102 latency=168 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:0f:ca:89:ff:25
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

7 ) Scan for networks:
```
ozgar@Hellmouth:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```

9 ) Kernel/architecture
2.6.27-11-generic x86_64

10 ) Restarting the network
```
ozgar@Hellmouth:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]
```

---

### Post by HammerOfDoubt on 2009-02-17
> **superprash2003 said:**
> try changing your DNS servers to opendns - 208.67.222.222 and 208.67.220.220
Reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

It actually made it hang up _more_, so I undid this change. But really, thanks anyway.

---

### Post by Crafty Kisses on 2009-02-17
Well it would appear you have the following wireless card:
```
Atheros Communications Inc. AR5008 Wireless Network Adapter
```
Have you installed this package?
```
sudo apt-get install madwifi-tools
```

---

### Post by HammerOfDoubt on 2009-02-17
> **Codename said:**
> Well it would appear you have the following wireless card:
```
Atheros Communications Inc. AR5008 Wireless Network Adapter
```
Have you installed this package?
```
sudo apt-get install madwifi-tools
```

I'm at work. I will try this once I get home.

Can you give me a quick run-down of what it is/does or a link explaining more?

---

### Post by HammerOfDoubt on 2009-02-18
It happens noticeably less, but it still happens.

Anyone else have any ideas?

---

### Post by superprash2003 on 2009-02-19
is this a DSL connection??

---

### Post by ulfj on 2009-02-19
I have the same problem,all was working great them it appeared yesterday.
Thought it was my connection with hughes net so I took my laptop to work and it does the same thing here.Looking forward for help on this myself

---

### Post by HammerOfDoubt on 2009-02-20
> **superprash2003 said:**
> is this a DSL connection??

It's a cable modem. I don't think it's related to the type of connection I have. This problem doesn't happen when I boot Vista or on any other computers here.

Should I set up ndiswrapper?

---

### Post by HammerOfDoubt on 2009-02-21
Some patterns I noticed. It doesnt happen when I play online games or during downloads, only when looking at websites. When a site locks up, everything else using the connection locks up. a download will drag down or the online game will freeze/disconnect.

Could it be browser related? I'm using Firefox.

---

### Post by BazookaAce on 2009-02-22
I'm having the same problem. My wireless cuts when i'm using Transmission. I had this problem before, but after installing Madwifi the problem was gone.. But last week it began to disconnect again.

---

### Post by HammerOfDoubt on 2009-02-24
I'm still expeiencing this problem.

---

### Post by BazookaAce on 2009-02-24
Still the same here to. But i've noticed that it only happens when i'm using transmission.

---

### Post by HammerOfDoubt on 2009-02-24
> **BazookaAce said:**
> Still the same here to. But i've noticed that it only happens when i'm using transmission.

Have you tried Deluge for torrents?

Transmission never worked for me.

---

### Post by BazookaAce on 2009-02-24
I used Deluge before, but after a few weeks i only got errors, and the application itself wouldn't open, so i installed Transmission. But i guess i can install it again and see if the connection will kill it self or not :)

But about your problem. I read some place that it may be the Network Manager that causes this problems. You may want to try something else. You can find other managers in Synaptics and the repository (add/remove). Remember to have another computer nearby with a connection in case it won't work, so you can download the network manager again and move it to the troubled computer.

---

### Post by White Owl on 2009-02-24
I had the same experience with the QUICKERTEK. I highley recommend NOT TO BUY QUICKERTEK products. They hang up on their customers and do not respect the consumers points of view.

BOYCOTT QUICKERTEK!

---

### Post by Augsburg on 2009-05-05
$ sudo apt-get install pump

Then when it cuts out:

$ sudo pump -i eth0

---

### Post by BazookaAce on 2009-05-05
What does "Pump" do?

---

### Post by Augsburg on 2009-05-05
pump - configure network interface via BOOTP or DHCP protocol

see [http://pwet.fr/man/linux/administration_systeme/pump](http://pwet.fr/man/linux/administration_systeme/pump)

I had a Damn small linux Distro that came with it, and it worked great.  I'm surprised it's not standard with Ubuntu.

---

### Post by Augsburg on 2009-05-05
oops! double post.

---

### Post by BazookaAce on 2009-05-05
That part is fine, but what does Pump exactly do? Does it pump up baloons? Redecorate my room?

---

### Post by Augsburg on 2009-05-05
sorry about the re-reply.  it basically just refreshes the network connection.

---

### Post by BazookaAce on 2009-05-05
Aha! Thats nice! 

*Writing down*

---

