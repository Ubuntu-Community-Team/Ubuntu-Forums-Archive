---
title: "Internet connected, no page response."
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by wicxity on 2011-02-02
I've recently installed Ubuntu 10.10 on my Macbook Pro (no comment :-?) and I've run into a problem: Whether the connection be through an ethernet cable or wireless, there is almost no response from applications such as Ubuntu Software Center or Firefox, i.e. there is a complete connection, however firefox will display 'waiting for...etcetc" without relent, and Ubuntu Software Center will download up to 666B of data and pause, sometimes taking several minutes to reach 666B (and only after disabling Jockey-backend).
I've tried disabling IPv6 but to no avail.
Wireless connection is preferable, any idea what needs to be done?:confused:
I'll chuck ya some info :
___________________________________________________________________________________________________________________________________________________
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03) 
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) 
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) 
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) 
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) 
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03) 
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1) 
0b:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 05) 
0c:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8058 PCI-E Gigabit Ethernet Controller (rev 13) 
0d:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02) 
___________________________________________________________________________________________________________________________________________________
eth0      Link encap:Ethernet  HWaddr 00:1f:5b:e7:b6:9c  
          inet6 addr: fe80::21f:5bff:fee7:b69c/64 Scope:Link 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:2315 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1196 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:865362 (865.3 KB)  TX bytes:128233 (128.2 KB) 
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1e:c2:bd:ad:00  
          inet addr:10.0.0.9  Bcast:10.0.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::21e:c2ff:febd:ad00/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:2884 errors:0 dropped:0 overruns:0 frame:6923 
          TX packets:751 errors:16 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:1194674 (1.1 MB)  TX bytes:95981 (95.9 KB) 
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B) 

___________________________________________________________________________________________________________________________________________________
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:207  Noise level:166 
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0 
___________________________________________________________________________________________________________________________________________________
Module                  Size  Used by 
pppoe                   9015  0 
pppox                   2054  1 pppoe 
michael_mic             1744  4 
arc4                    1165  2 
binfmt_misc             6599  1 
rfcomm                 33811  4 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  4 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep               5040  1 snd_hda_codec 
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi 
snd_seq_midi_event      6047  1 snd_seq_midi 
lib80211_crypt_tkip     7736  0 
wl                   1959533  0 
nouveau               516971  2 
applesmc               24900  0 
led_class               2633  1 applesmc 
ttm                    56633  1 nouveau 
drm_kms_helper         30200  1 nouveau 
hid_apple               4523  0 
drm                   168054  4 nouveau,ttm,drm_kms_helper 
uvcvideo               55847  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              19067  2 snd_pcm,snd_seq 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq 
joydev                  8735  0 
snd                    49006  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
videodev               43098  1 uvcvideo 
i2c_algo_bit            5168  1 nouveau 
usbhid                 36882  0 
input_polldev           3491  1 applesmc 
soundcore                880  1 snd 
lib80211                5058  2 lib80211_crypt_tkip,wl 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm 
v4l1_compat            13359  2 uvcvideo,videodev 
hid                    67742  2 hid_apple,usbhid 
intel_agp              26360  0 
agpgart                32011  3 ttm,drm,intel_agp 
video                  18712  0 
output                  1883  1 video 
bcm5974                 7611  0 
btusb                  10969  0 
lp                      7342  0 
mbp_nvidia_bl           1943  0 
bluetooth              50500  7 rfcomm,sco,bnep,l2cap,btusb 
parport                31492  3 parport_pc,ppdev,lp 
firewire_ohci          21106  0 
firewire_core          46643  1 firewire_ohci 
crc_itu_t               1383  1 firewire_core 
sky2                   45127  0 
___________________________________________________________________________________________________________________________________________________
 *-network               
       description: Wireless interface 
       product: BCM4321 802.11a/b/g/n 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0b:00.0 
       logical name: eth1 
       version: 05 
       serial: 00:1e:c2:bd:ad:00 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.0.0.9 latency=0 multicast=yes wireless=IEEE 802.11abgn 
       resources: irq:16 memory:d7300000-d7303fff 
  *-network 
       description: Ethernet interface 
       product: 88E8058 PCI-E Gigabit Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       logical name: eth0 
       version: 13 
       serial: 00:1f:5b:e7:b6:9c 
       size: 100MB/s 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=100MB/s 
       resources: irq:45 memory:d7200000-d7203fff ioport:5000(size=256) memory:dba00000-dba1fff
___________________________________________________________________________________________________________________________________________________

---

### Post by wicxity on 2011-02-02
bump.

---

### Post by thefasterblueone on 2011-02-02
Checkout the sticky on the "Networking & Wireless" page.

[http://ubuntuforums.org/showthread.php?t=1604868]("http://ubuntuforums.org/showthread.php?t=1604868")

---

### Post by wicxity on 2011-02-03
Perfect! I can't thank you enough :D

---

