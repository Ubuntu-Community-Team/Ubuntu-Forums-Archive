---
title: "Linksys /9.04/Toshiba Satellite"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by cmittle on 2009-07-12
I've recently updated my laptop from Hardy to Jaunty by dist-upgrading from Hardy to Intrepid then immediately again to Jaunty.  My wireless was working fine in Hardy, I did not check in Intrepid but now is not working in Jaunty.  I've attached all the neccessary output I just need someone to help me intepret it.

As far as I can tell my computer is detecting the card but it just is unable to see the wireless signals available.

Computer:
Toshiba Satellite A15-S129. 

Wireless card:
```
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
```

Interface:
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:08:0d:2f:c7:65  
          inet addr:192.168.1.131  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:dff:fe2f:c765/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:827 errors:0 dropped:0 overruns:0 frame:0
          TX packets:755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:996248 (996.2 KB)  TX bytes:116818 (116.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2704 (2.7 KB)  TX bytes:2704 (2.7 KB)

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"STA8B7630"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Modules:
```
cory@cory-laptop:~$ lsmod
Module                  Size  Used by
nls_cp437              13696  0 
cifs                  266916  0 
binfmt_misc            16776  1 
i915                   65668  2 
drm                    96296  3 i915
lp                     17156  0 
joydev                 18368  0 
acx                   104196  0 
pcmcia                 44748  0 
ppdev                  15620  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                61972  0 
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                 10496  0 
serio_raw              13316  0 
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
yenta_socket           32396  2 
rsrc_nonstatic         19328  1 yenta_socket
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 40212  0 
toshiba_acpi           18624  0 
input_polldev          11912  1 toshiba_acpi
video                  25360  0 
output                 11008  1 video
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
usbhid                 42336  0 
e100                   41740  0 
mii                    13312  1 e100
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

Kernel boot messages:
```
[  244.280842] Call Trace:
[  244.280847]  [<c04fcbf6>] ? printk+0x18/0x1a
[  244.280852]  [<c0139b24>] warn_on_slowpath+0x54/0x80
[  244.280860]  [<c0109cf0>] ? nommu_free_coherent+0x0/0x20
[  244.280864]  [<c01949da>] ? free_hot_page+0xa/0x10
[  244.280867]  [<c0194dcf>] ? __free_pages+0x2f/0x40
[  244.280876]  [<ef906647>] acxpci_free_desc_queues+0x297/0x2a0 [acx]
[  244.280884]  [<ef906695>] acxpci_s_delete_dma_regions+0x45/0x60 [acx]
[  244.280892]  [<ef9085e5>] acxpci_e_remove+0x105/0x29d [acx]
[  244.280896]  [<c020a43f>] ? sysfs_hash_and_remove+0x5f/0x70
[  244.280903]  [<c02dc569>] pci_device_remove+0x19/0x40
[  244.280906]  [<c034ef94>] __device_release_driver+0x74/0xb0
[  244.280910]  [<c034f0a3>] device_release_driver+0x23/0x40
[  244.280914]  [<c034e622>] bus_remove_device+0x82/0xb0
[  244.280917]  [<c034cd78>] device_del+0xe8/0x190
[  244.280920]  [<c034ce2b>] device_unregister+0xb/0x20
[  244.280924]  [<c02d8213>] pci_stop_dev+0x23/0x30
[  244.280927]  [<c02d8291>] pci_destroy_dev+0x11/0x80
[  244.280930]  [<c02d8390>] pci_remove_bus_device+0x30/0x40
[  244.280934]  [<c02d83c9>] pci_remove_behind_bridge+0x29/0x40
[  244.280943]  [<ef7ea0a3>] cb_free+0x43/0x50 [pcmcia_core]
[  244.280951]  [<ef7e6691>] socket_shutdown+0x81/0xf0 [pcmcia_core]
[  244.280955]  [<c04fcbf6>] ? printk+0x18/0x1a
[  244.280964]  [<ef7e68b4>] socket_remove+0x44/0x50 [pcmcia_core]
[  244.280973]  [<ef7e7157>] pccardd+0x1d7/0x290 [pcmcia_core]
[  244.280980]  [<ef7e6f80>] ? pccardd+0x0/0x290 [pcmcia_core]
[  244.280985]  [<c014e90c>] kthread+0x3c/0x70
[  244.280988]  [<c014e8d0>] ? kthread+0x0/0x70
[  244.280992]  [<c0105477>] kernel_thread_helper+0x7/0x10
[  244.280994] ---[ end trace c74ba80fccfa2c4b ]---
[  244.281030] acx_pci 0000:02:00.0: PCI INT A disabled
[  366.992073] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[  366.992121] pci 0000:02:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
[  366.992130] pci 0000:02:00.0: reg 14 32bit mmio: [0x000000-0x01ffff]
[  366.992174] pci 0000:02:00.0: supports D1 D2
[  366.992177] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[  366.992183] pci 0000:02:00.0: PME# disabled
[  366.997175] acx_pci 0000:02:00.0: enabling device (0000 -> 0002)
[  366.997192] acx_pci 0000:02:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[  366.997201] acx_pci 0000:02:00.0: setting latency timer to 64
[  366.997351] acx: found ACX111-based wireless network card at 0000:02:00.0, irq:11, phymem1:0x40020000, phymem2:0x40000000, mem1:0xefc5c000, mem1_size:8192, mem2:0xefb40000, mem2_size:131072
[  366.998365] acx: loading firmware for acx1111 chipset with radio ID 16
[  366.998371] acx_pci 0000:02:00.0: firmware: requesting acx/1.2.1.34/tiacx111c16
[  367.820567] NVS_vendor_offs:0221 probe_delay:200 eof_memory:1114112
[  367.820573] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
[  367.820575] AntennaID:00 Len:02 Data:01 02 
[  367.820579] PowerLevelID:01 Len:02 Data:001E 000A 
[  367.820583] DataRatesID:02 Len:05 Data:02 04 11 22 44 
[  367.820588] DomainID:03 Len:06 Data:10 20 30 31 32 40 
[  367.820595] ProductID:04 Len:09 Data:TI ACX100
[  367.820597] ManufacturerID:05 Len:07 Data:TI Test
[  367.880056] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
[  367.886591] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.28-13-generic

```

Scan for networks:
```
cory@cory-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

```

Version:
```
cory@cory-laptop:~$ lsb_release -d
Description:	Ubuntu 9.04
```

Kernel:
```
cory@cory-laptop:~$ uname -mr
2.6.28-13-generic i686
```

Restarting network:
```
cory@cory-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for cory: 
 * Reconfiguring network interfaces...                                                       Ignoring unknown interface eth0=eth0.
                                                                                      [ OK ]

```

Any advice would be appreciated.
Cory

---

### Post by superprash2003 on 2009-07-12
laptops come with a wireless switch, which has an ON/OFF button or a keyboard shorcut.. make sure that the wifi switch is ON.. 

for reference : [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

### Post by thatroom on 2009-08-01
do you really want that to be your answer? about a freakin' switch? anyone who can regurgitate all of that data had BETTER have checked the switch first off!

---

