---
title: "Atheros  AR9285 (PCI-Express), Toshiba NB200"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by Rahulnlnz on 2009-06-21
Hi people,

Im new to linux, loved the screen shots and reviews of ubuntu and its netbook remix, and as I was sick of Windows, I installed it on my new netbook Toshiba NB200. I installed from USB as per ubuntu online guides. Everything works fine, except the wireless connection...the LED is on all the time..but it says 'no network connection' and no wireless signals are picked up (despite the LED). 

Ive tried all the various suggestions on these forums to fix it - ndiswrapper, etc, and even did 'sudo apt-get install linux-backports-modules-jaunty' update....but to no avail. I've tried various things for 3 days now, searched everywhere and tried what I can, but no luck. Im at wits end. I need some help from Linux pros! Please help me get my wireless internet working .
As per this 'sticky' thread -http://ubuntuforums.org/showthread.php?p=6183681  I've pasted a bunch of info below. Any advice gladly accepted :) Thank you!
[B]
Machine [/B]- Toshiba NB200
[B]
Wireless brand [/B]- Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) 


**Interface** - 

rahul@rahul-netbook:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:23:5a:0b:df:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:251 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B) 
rahul@rahul-netbook:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

pan0      no wireless extensions. 

**Modules** - 

rahul@rahul-netbook:~$ lsmod 
Module                  Size  Used by 
i915                   65668  2 
drm                    96296  3 i915 
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge 
bnep                   20224  2 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp 
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss 
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              29704  2 snd_pcm,snd_seq 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
uvcvideo               63240  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt 
intel_agp              34108  1 
compat_ioctl32          9344  1 uvcvideo 
videodev               41600  1 uvcvideo 
psmouse                61972  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
v4l1_compat            21764  2 uvcvideo,videodev 
pcspkr                 10496  0 
serio_raw              13316  0 
soundcore              15200  1 snd 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm 
agpgart                42696  3 drm,intel_agp 
ndiswrapper           193436  0 
input_polldev          11912  0 
video                  25360  0 
output                 11008  1 video 
r8169                  40836  0 
mii                    13312  1 r8169 
fbcon                  46112  0 
tileblit               10752  1 fbcon 
font                   16384  1 fbcon 
bitblit                13824  1 fbcon 
softcursor              9984  1 bitblit 

**Network Configuration -** 

*-network               
       description: Network controller 
       product: AR9285 Wireless Network Adapter (PCI-Express) 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper 
  *-network 
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:23:5a:0b:df:5c 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 96:42:82:ff:3d:eb 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 

**Scan for networks **- 

rahul@rahul-netbook:~$ iwlist scan wlan0 
iwlist: unknown command `wlan0' (check 'iwlist --help') 

[B]Ubuntu version - 
[/B]Ubuntu 9.04

[B]Kernel/architecture - 

[/B]  2.6.28-13-generic i686 




Please let me know if you need more info. I didnt put the Kernel boot messages up, because that was a long write up. Let me know If you need that.  

Thank you in advance!

R

---

### Post by Rahulnlnz on 2009-06-21
I forgot to point out that the netbook came with an OEM Windows XP home on it. I installed Ubuntu as a dual boot option, so now I think it uses GRUB boot loader? Anyway, the dual boot doesnt work for windows...takes me to a blue screen..but thats a different issue!

The point here, is that i DO have access to the Windows folder to find drivers to fix my problem above.

Hope to hear from someone out there soon!

---

### Post by Rahulnlnz on 2009-06-22
Playing around this afternoon, I ran the 'dmesg' command in Terminal and I've cut and pasted some things that might be relevant? (No idea, Im stabbing in the dark here....) help!

[   10.731828] ndiswrapper version 1.53 loaded (smp=yes, preempt=no) 
.....

[   11.508688] ndiswrapper (link_pe_images:603): DLL initialize failed for athw.sys 
[   11.508750] ndiswrapper: driver netathw (,02/13/2009,7.7.0.233) loaded 
[   11.509230] ndiswrapper 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   11.509245] ndiswrapper (mp_init:210): assuming WDM (non-NDIS) driver 
[   11.509471] usbcore: registered new interface driver ndiswrapper
......

[17502.160198] ndiswrapper (mp_set_power_state:375): eth%d does not support power management; halting the device 
[17502.160210] ndiswrapper (mp_halt:262): device f6419500 is not initialized - not halting 
.....

[17503.078856] ndiswrapper 0000:03:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b) 
[17503.078901] ndiswrapper 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf0100004) 
[17503.078912] ndiswrapper 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10) 
[17503.078927] ndiswrapper 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007) 
[17503.092133] ndiswrapper (mp_init:210): assuming WDM (non-NDIS) driver 
[17503.092142] ndiswrapper (mp_set_power_state:344): eth%d: couldn't set power to state 1; device not resumed 
[17503.092151] ndiswrapper (NdisDispatchPower:1336): couldn't set power to 1: 00010001 

....

---

### Post by endjuser on 2009-06-22
Hi,

same Atheros WLAN chip here, on my Asus eee-pc 1003hag. To make it work you should EITHER use ndiswrapper OR the updated Atheros driver in the backports package. 

I use the Atheros driver since it was easier to get it going. Just install the backports package for jaunty or intrepid. If you installed ndiswrapper, remember to disable ndiswrapper - look for "blacklisting modules" in the Ubuntu docs. If ndiswrapper has blacklisted the Atheros module ath9k, you must fix that, too. Remember, it's either .. or - you cannot use both of these wlan drivers together.

Simply installing the backports package did it for me. I did not play around with ndiswrapper yet. I might do in the future, since the connections established with the ath9k driver appear to me fairly weak. However, to get any wireless connectivity at all, it is the easiest thing to do.

---

### Post by Rahulnlnz on 2009-06-22
Hi endjuser,

Many thanks for the reply and suggestion! I will give that a go and see if it works. I'll un-install ndiswrapper I guess, and try your method. 

Right now though, I'm in the midst of updating the kernel to the latest one, as another forum suggested that may work. So will try that, then if that fails, come back to your suggestion.

:)

---

### Post by revbin on 2009-06-23
Hi there.
 
I am VERY new to Linux, like Rahulnlnz, but I can't get my head around a lot of this.  I have an NB200 and I also have dual booted Ubuntu with XP.  
 
I cannot get my wireless Atheros to work in Ubuntu.  I have tried typing ''sudo apt-get install linux-backports-modules-jaunty' in the terminal - said it could not be found.  I don't know how to 'install' the drivers.
 
Can someone help a newbie like me please?  
 
Many thanks.
 
Revbin

---

### Post by martinnjensen on 2009-06-23
@revbin & Rahulnlnz

Like you guys I am completely new to Linux, I just want a decent os on my new asus seashell. I have succeeded in getting the wireless to work by following these instructions:

[http://forum.eeeuser.com/viewtopic.php?id=69647](http://forum.eeeuser.com/viewtopic.php?id=69647)

Explains how to get the ethernet working, which seems  to be the easiet path to get the wireless working. Go to msg #24 for the details.

[http://www.amazon.com/Seashell-10-Inch-Netbook-Processor-Bluetooth/product-reviews/B0029QMDZI](http://www.amazon.com/Seashell-10-Inch-Netbook-Processor-Bluetooth/product-reviews/B0029QMDZI)

Explains how to install the wireless driver when the ethernet is working. Look for the review by a guy named Kurt Milligan. After running the final install command, click once on the wireless icon in the top of screen, and you should get a list of available routers.

I was planning on writing a more comprehensive guide based on this, but unfortunately it still doesn't work 100% for me. My pc loses the connection to the router after a while, but I suspect this may be a problem with the router...

I hope it helps!
Martin

---

### Post by revbin on 2009-06-23
Thanks very much for your feedback, Martin.  My only problem is I am so new to Linux, the page you recommended looks like a different language to me.  It talks about updating the 'kernel' which I have no idea about.  I've spent at least a week on this and I am no closer to understanding Linux.  'Fraid I'm going to uninstall Ubuntu and go back to XP.  Thanks anyway.

---

### Post by Rahulnlnz on 2009-06-23
Revbin...don't give up yet!!  Let me get mine working and I'll take you through step by step :-)

martinnjensen, thanks for those links, but I tried that already i think  actually and it didnt work - maybe its my particular card AR9285. But I tried that before updating my kernel...but I think this newer kernel should fix things (correct me people if Im wrong).

OK, just updating where I'm at..I feel Im so close...but just missing something small...I'd really like some help from some more experienced users than me please :-) I've updated the Kernel to the latest one, and that seems to have done a lot of good...but the problem still remains - I can not connect to my wireless...in fact Im not picking up any signals through network manager. Ethernet works perfectly. Here is an updated dump of what I gave in my initial post. 

[B]Check interface - 

[/B]```
rahul@rahul-netbook:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:23:5a:0b:df:5c   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:28 Base address:0xe000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:500 (500.0 B)  TX bytes:500 (500.0 B) 
 
wlan0     Link encap:Ethernet  HWaddr 00:23:08:7a:46:9e   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:7776 (7.7 KB) 
 
wlan0:avahi Link encap:Ethernet  HWaddr 00:23:08:7a:46:9e   
          inet addr:169.254.5.208  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-23-08-7A-46-9E-00-00-00-00-00-00-00-00-00-00   
          UP RUNNING  MTU:0  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

```

..and iwconfig...

```
rahul@rahul-netbook:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11bgn  ESSID:"Alchemist"   
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated    
          Tx-Power=20 dBm    
          Retry min limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
pan0      no wireless extensions. 

```

**check for modules**

```
rahul@rahul-netbook:~$ lsmod 
Module                  Size  Used by 
i915                  173032  2  
drm                   158368  3 i915 
i2c_algo_bit            5904  1 i915 
binfmt_misc             8212  1  
ppdev                   7568  0  
bridge                 48480  0  
stp                     2416  1 bridge 
bnep                   12108  2  
lp                      9060  0  
parport                35052  2 ppdev,lp 
snd_hda_codec_realtek   197168  1  
snd_hda_intel          26152  3  
snd_hda_codec          67532  2 snd_hda_codec_realtek,snd_hda_intel 
snd_pcm_oss            39008  0  
arc4                    1804  2  
snd_mixer_oss          15948  1 snd_pcm_oss 
ecb                     2732  2  
joydev                 10272  0  
snd_pcm                74896  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
snd_seq_dummy           2704  0  
snd_seq_oss            28320  0  
snd_seq_midi            6496  0  
snd_rawmidi            22112  1 snd_seq_midi 
ath9k                 309368  0  
snd_seq_midi_event      7148  2 snd_seq_oss,snd_seq_midi 
mac80211              210992  1 ath9k 
snd_seq                50000  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
uvcvideo               58680  0  
iTCO_wdt               10864  0  
iTCO_vendor_support     3600  1 iTCO_wdt 
snd_timer              21268  2 snd_pcm,snd_seq 
snd_seq_device          7064  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
cfg80211               63756  2 ath9k,mac80211 
videodev               36064  1 uvcvideo 
psmouse                55716  0  
intel_agp              26428  1  
v4l1_compat            14480  2 uvcvideo,videodev 
pcspkr                  2444  0  
serio_raw               5488  0  
video                  18432  1 i915 
input_polldev           3892  0  
snd                    58468  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
led_class               4240  1 ath9k 
agpgart                35084  3 drm,intel_agp 
output                  2988  1 video 
soundcore               7200  1 snd 
snd_page_alloc          8980  2 snd_hda_intel,snd_pcm 
r8169                  32592  0  
mii                     5260  1 r8169 

```

**Relevant Kernel boot messages - **

```

[    4.414747] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded 
[    4.414805] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[    4.414857] r8169 0000:04:00.0: setting latency timer to 64 
[    4.415174] r8169 0000:04:00.0: irq 28 for MSI/MSI-X 
[    4.417059] eth0: RTL8102e at 0xf802e000, 00:23:5a:0b:df:5c, XID 24c00000
```
```

[   12.241429] cfg80211: World regulatory domain updated: 
[   12.241437]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   12.241445]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.241451]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   12.241457]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   12.241463]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.241469]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   12.621319] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   12.621350] ath9k 0000:03:00.0: setting latency timer to 64 
[   12.734061] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input8 
[   12.780216] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9 
[   12.964702] phy0: Selected rate control algorithm 'ath9k_rate_control' 
[   12.966238] Registered led device: ath9k-phy0::radio 
[   12.966293] Registered led device: ath9k-phy0::assoc 
[   12.966357] Registered led device: ath9k-phy0::tx 
[   12.966414] Registered led device: ath9k-phy0::rx 
[   12.966452] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf8420000, irq=17 
[   13.058088] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22 
[   13.058152] HDA Intel 0000:00:1b.0: setting latency timer to 64 
[   13.181113] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS... 
[   13.431211] lp: driver loaded but no devices found 
[   13.578707] Adding 176672k swap on /dev/sda5.  Priority:-1 extents:1 across:176672k  
[   14.164268] EXT3 FS on sda4, internal journal 
[   18.667989] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
[   18.668000] Bluetooth: BNEP filters: protocol multicast 
[   18.756534] Bridge firewalling registered 
[   20.207239] ppdev: user-space parallel port driver 
[   21.554957] [drm] Initialized drm 1.1.0 20060810 
[   21.671777] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   21.671790] pci 0000:00:02.0: setting latency timer to 64 
[   21.675832] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0 
[   24.166882] r8169: eth0: link down 
[   24.167391] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   24.203092] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   35.576391] wlan0: authenticate with AP 00:21:63:20:ef:d4 
[   35.578579] wlan0: authenticated 
[   35.578590] wlan0: associate with AP 00:21:63:20:ef:d4 
[   35.581088] wlan0: RX AssocResp from 00:21:63:20:ef:d4 (capab=0x11 status=0 aid=3) 
[   35.581096] wlan0: associated 
[   35.582111] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
[   46.040077] wlan0: no IPv6 routers present 
[   46.180101] CE: hpet increasing min_delta_ns to 15000 nsec 
[   47.880102] CE: hpet increasing min_delta_ns to 22500 nsec 
[   81.376824] wlan0: disassociating by local choice (reason=3) 
[   82.628760] wlan0: authenticate with AP 00:21:63:20:ef:d4 
[   82.639060] wlan0: authenticate with AP 00:21:63:20:ef:d4 
[   82.642000] wlan0: authenticated 
[   82.642012] wlan0: associate with AP 00:21:63:20:ef:d4 
[   82.645397] wlan0: RX ReassocResp from 00:21:63:20:ef:d4 (capab=0x11 status=0 aid=3) 
[   82.645409] wlan0: associated 
[  128.378952] wlan0: disassociating by local choice (reason=3) 
[  129.633571] wlan0: authenticate with AP 00:21:63:20:ef:d4 
[  129.644137] wlan0: authenticate with AP 00:21:63:20:ef:d4 
[  129.650067] wlan0: authenticated 
[  129.650079] wlan0: associate with AP 00:21:63:20:ef:d4 
[  129.653221] wlan0: RX ReassocResp from 00:21:63:20:ef:d4 (capab=0x11 status=0 aid=3) 
[  129.653233] wlan0: associated 
[  175.381060] wlan0: disassociating by local choice (reason=3) 
[  176.640068] wlan0: authenticate with AP 00:21:63:20:ef:d4 
[  176.650404] wlan0: authenticate with AP 00:21:63:20:ef:d4 
[  176.652853] wlan0: authenticated 
[  176.652866] wlan0: associate with AP 00:21:63:20:ef:d4 
[  176.657138] wlan0: RX ReassocResp from 00:21:63:20:ef:d4 (capab=0x11 status=0 aid=3) 
[  176.657154] wlan0: associated 
[  222.398644] wlan0: direct probe to AP 00:21:63:20:ef:d4 try 1 
[  222.400894] wlan0 direct probe responded 
[  222.400906] wlan0: authenticate with AP 00:21:63:20:ef:d4 
[  222.403207] wlan0: authenticated 
[  222.403218] wlan0: associate with AP 00:21:63:20:ef:d4 
[  222.405971] wlan0: RX AssocResp from 00:21:63:20:ef:d4 (capab=0x11 status=12 aid=0) 
[  222.405984] wlan0: AP denied association (code=12) 
[  222.600092] wlan0: associate with AP 00:21:63:20:ef:d4 
[  222.602679] wlan0: RX AssocResp from 00:21:63:20:ef:d4 (capab=0x11 status=12 aid=0) 
[  222.602692] wlan0: AP denied association (code=12) 
[  222.800114] wlan0: associate with AP 00:21:63:20:ef:d4 
[  222.802640] wlan0: RX AssocResp from 00:21:63:20:ef:d4 (capab=0x11 status=12 aid=0) 
[  222.802653] wlan0: AP denied association (code=12) 
[  223.000102] wlan0: association with AP 00:21:63:20:ef:d4 timed out 
[ 1617.867774] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
```

**Network configuration **

```
*-network                
       description: Wireless interface 
       product: AR9285 Wireless Network Adapter (PCI-Express) 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wmaster0 
       version: 01 
       serial: 00:23:08:7a:46:9e 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn 
  *-network 
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:23:5a:0b:df:5c 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: a6:23:31:0c:75:b9 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
```

**Scan for networks**

 ```
lo        Interface doesn't support scanning.

 

 

eth0      Interface doesn't support scanning.

 

 

wmaster0  Interface doesn't support scanning.

 

 

wlan0     Scan completed :

          Cell 01 - Address: 00:21:63:20:EF:D4

                    Channel:10

                    Frequency:2.457 GHz (Channel 10)

                    Quality=24/70  Signal level=-86 dBm 

                    Encryption key:on

                    ESSID:"Alchemist"

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

                              24 Mb/s; 36 Mb/s; 54 Mb/s

                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s

                    Mode:Master

                    Extra:tsf=000000033ce7524e

                    Extra: Last beacon: 37776ms ago

                    IE: Unknown: 0009416C6368656D697374

                    IE: Unknown: 010882848B962430486C

                    IE: Unknown: 03010A

                    IE: Unknown: 2A0107

                    IE: Unknown: 2F0107

                    IE: Unknown: 32040C121860

                    IE: Unknown: DD06001018020100

 

 

pan0      Interface doesn't support scanning.

```

**Ubuntu version - 9.04, Kernel/Architecture - 2.6.30**


Thats where Im at guys. I feel its progressing, but really, I think I've taken it as far as my one week old linux hands can take it. I'd LOVE to get some help to get my wireless working...I dont want to have to go back to XP :-(

Any help appreciated. Thank you!

---

### Post by Rahulnlnz on 2009-06-23
Some in the kernel boot messages seems a bit suspicious.....

"
[  222.802653] wlan0: AP denied association (code=12) 
[  223.000102] wlan0: association with AP 00:21:63:20:ef:d4 timed out 
[ 1617.867774] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by Rahulnlnz on 2009-06-23
Is there anyone that can help? :s

---

### Post by cooper144 on 2009-06-24
> **Rahulnlnz said:**
> Some in the kernel boot messages seems a bit suspicious.....

"
[  222.802653] wlan0: AP denied association (code=12) 
[  223.000102] wlan0: association with AP 00:21:63:20:ef:d4 timed out 
[ 1617.867774] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Does it work using Windows, ie it's not from your AP? Let us know of your progress since I'm considering getting this netbook. :)

Thanks,
dave

---

### Post by revbin on 2009-06-24
Separate discussion I know, but I would get the NB200.  It's an absolute joy - although it quotes 9 hours of battery life, but I've only managed 6.5 hours with the lowest power settings and just surfing the net.
 
Rahulninz, Ubuntu is still living on my laptop by the skin of its teeth. :)  I tried installing Ubuntu Netbook Remix, thinking it would solve the problem, but no luck connecting to the internet.

---

### Post by Rahulnlnz on 2009-06-25
Yeah in the absence of any help through experienced users on these forums, I think I will be XP-ing again by the weekend. Seriously, Ive tried it all - ndiswrapper, backports-jaunty, tried uninstalling ndiswrapper and just doing the backports thing, reinstalled ubuntu and updated the kernel to 2.6.30 (see above) and STILL doesnt work. I think my one week old linux hands have taken things as far as I can go. 

cooper144, The netbook is VERY good...in XP everything works well actually. And yeah, 9 hours is pretty hard! I did get just past 7h 45min though (with 5 mins still remaining) without wireless and absolutely lowest settings on everything, just doing word processing.

But back on topic - I suspect ubuntu isnt ready to handle the new specs and hardware of the toshiba...the netbook is only out for a month or so now. Perhaps wait a month or so and perhaps our problems will be solved. Though I have noticed that other linux distributions (openSUSE, Fedora, etc) have a less active 'networking and wireless' forum with less user problems...hmmmm. Wonder if it's because these forums are more interactive and vibrant, or because ubuntu has more of these problems?

---

### Post by Taiebot65 on 2009-06-25
Hello following [http://ubuntuforums.org/showpost.php?p=7503123&postcount=9]("http://ubuntuforums.org/showpost.php?p=7503123&postcount=9")

You are really close to your nirvana.

Wireless is working now!!

So maybe you should delete all your configuration and restart by adding your configuration manually right clicking on the icon and modify connection.

there is now two kinds of problems you could be confronted that your drivers are not supporting very well wpa encryption by changing the security of your network to wep could solve your problem.

You could be as well too far from your wireless source some drivers are  not powerful enough.

And have you checked on your network if there is not a button to enable on your box before pairing a new wireless device.

Good luck thibaut

---

### Post by cooper144 on 2009-06-25
Maybe trying installing the newest versions of compat-wireless?!

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

Please let me know how it goes :P

Thanks,
Dave

---

### Post by revbin on 2009-06-25
Rahulnlnz, I'm right behind you.  Keep going!

---

### Post by Rahulnlnz on 2009-06-26
Hi Thibaut,  My security is WEP already, so thats not the issue, and secondly, distance is not the issue...the wireless card has no problem picking up an 'excellent' signal through Windows XP -  in fact it picks up 3 of my neighbours signals too! Oh and there's not button on the modem for that....and I dont think thats the issue as I used to own an ASUS eeepc901 Xandros and that worked fine here. 

Dave, Im not sure thats necessary any more - I did that originally, but the new kernel update I did does everything that compat would achieve (correct me if Im wrong people). 

Revbin, Im thinking we're on final lap territory now! Im going to (reluctantly) head back to windows XP pretty soon. Maybe we just need to be patient, wait a few weeks/months and our netbooks will be compatible.

---

### Post by salreus on 2009-06-26
Ok, not sure if you consider this a solution. But I have a Toshiba Qosmio F50-Q551 and it has a intel wifi link 5100 inside and works with Ubuntu using the ubuntu drivers in the install. What about spending the $30 buck and just swap out the Atheros card? And you can get the windows driver from Toshiba for the card. Below is the link for the vista driver for the 5100. Not sure if it will work on the Toshiba NB200 since it uses XP. I plan on swapping the card and giving this a try, but I can't seem to find a small enough torx tool to remove  the cover. Not sure why they picked torx over phillips like the memory bay door. I'll check out the hardware store tomorrow and hopefully report back tomorrow. Does anyone know what size torx driver I need? In case I need to order on online.

** If you try this... You want to get the 5100 pcie half mini not the pcie mini

[http://cdgenp01.csd.toshiba.com/content/support/downloads/driver_wifi_intel_27546C.exe](http://cdgenp01.csd.toshiba.com/content/support/downloads/driver_wifi_intel_27546C.exe)

---

### Post by Rahulnlnz on 2009-06-28
OK guys!  hmmm. Well, after a Sunday of frustration and googling, I am now using ....FEDORA 11. haha. Yup, Im writing this on a wireless network, setup in 1 minute, on Fedora 11. The weird thing is, its the GNOME version too...not the KDE desktop. So I can't understand why Ubuntu didnt work at all. Mind you, from what I understand it shouldn't matter what desktop it is anyway. 
The key was to access a program in system>Administration>Network Device Control  and tick the 'turn on the wireless card when computer starts' radio button, and a few other intuitive adjustments in the options. I've uninstalled ubuntu now, but if you guys above want to try find the 'Network Device Control' program and install that and then play with the options in that, you might have some luck I guess. 
For me, Fedora seems great right now, everything works (except a few function buttons), and Im running it off USB. 

So, there you have it!   If one of you guys DO manage to get it working through ubuntu, I'd love to know! 

best wishes
R

---

### Post by Rahulnlnz on 2009-06-28
oh and one more thing, I DID try going into the bios setup screen and turn on wireless card in there while troubleshooting the ubuntu install. It made no difference. 
So my recommendation - try find the Network Device Control program (you probably have to download and install it) and use that to fix things. I didnt know that program existed till I installed Fedora 11, and now Im a happy guy again :-)

---

### Post by mredub on 2009-06-29
> **Rahulnlnz said:**
> I forgot to point out that the netbook came with an OEM Windows XP home on it. I installed Ubuntu as a dual boot option, so now I think it uses GRUB boot loader? Anyway, the dual boot doesnt work for windows...takes me to a blue screen..but thats a different issue!

The point here, is that i DO have access to the Windows folder to find drivers to fix my problem above.

Hope to hear from someone out there soon!

This is pretty common.  the most straight forward way to fix the bluescreen issue is to remove the hard disk from the netbook [torx t9 :( ] and connect it to another windows machine.

start that machine from off (cold boot) and it should run through scandisk and it will fix the Windows MBR defects that the ubuntu repartitioner creates.  once you've done that, you can put it back in the netbook, and you won't get any more blue screens.

the *exact* same thing happened to me about 4 hours ago on my new toshiba nb205-n210.

-eric

---

### Post by Rahulnlnz on 2009-06-29
> **mredub said:**
> This is pretty common.  the most straight forward way to fix the bluescreen issue is to remove the hard disk from the netbook [torx t9 :( ] and connect it to another windows machine.

start that machine from off (cold boot) and it should run through scandisk and it will fix the Windows MBR defects that the ubuntu repartitioner creates.  once you've done that, you can put it back in the netbook, and you won't get any more blue screens.

the *exact* same thing happened to me about 4 hours ago on my new toshiba nb205-n210.

-eric


Yeah Thanks Eric, but I'm running Fedora now off USB. I think a way for folks to avoid the error is to 'manually' partition the drive beforehand through Windows and install ubuntu into that partition. In other words, don't let the ubuntu installer do things automatically.

---

### Post by revbin on 2009-07-01
[B]Rahulnlnz, I copied you and installed Fedora 11.  It wasn't easy - I had some problems with the installation from my SD Card, but guess what? I am typing this in Fedora - wireless works!!  Thanks so much for your help!

Revbin
[/B]

---

### Post by salreus on 2009-07-01
I must be doing something wrong. I don't see a " 'turn on the wireless card when computer starts' radio button". But then I tried the Fedora KDE. I have downloaded the gnome version as well, having issues getting it to boot up. But I had that issue with the KDE as well. and just loading it a few times on the stick seemed to get it to work.

---

### Post by kdroggy on 2009-07-04
Apparently if you have wireless switched off in windows before you install Ubuntu there is no way to enable the card. More here: [http://tjmcgrew.com/](http://tjmcgrew.com/)

I also have the NB200 and was able to get wireless working with backports, but I did have it switched on before I installed Jaunty.

---

### Post by Rahulnlnz on 2009-07-10
> **revbin said:**
> [B]Rahulnlnz, I copied you and installed Fedora 11.  It wasn't easy - I had some problems with the installation from my SD Card, but guess what? I am typing this in Fedora - wireless works!!  Thanks so much for your help!

Revbin
[/B]


Great! Yeah, probably not the best thing to admit on the ubuntu forums, but hey - it wasnt through lack of trying was it?!!

Good luck with your experience!

R

---

### Post by Rahulnlnz on 2009-07-10
> **salreus said:**
> I must be doing something wrong. I don't see a " 'turn on the wireless card when computer starts' radio button". But then I tried the Fedora KDE. I have downloaded the gnome version as well, having issues getting it to boot up. But I had that issue with the KDE as well. and just loading it a few times on the stick seemed to get it to work.


Hi, Im not quite sure what the problem is? You confused me with your final sentence. If it is a Fedora issue, I suggest maybe you take it to the Fedora forums instead (or PM me and I'll see what I can do)

R

---

### Post by calibre97 on 2009-07-16
Did the Fedora 11 install and sure enough, I got a blue screen from XP. Since I had the foresight to perform a full backup (using Acronis which comes as a bootable CD) to an external USB drive, all I had to do was restore from the .tib file, again booting to the Acronis CD and everything was back as it should be. However, I am experiencing the same disappearing wireless from Fedora. It's just gone and there doesn't appear to be any way to get it back. It and the Ethernet appear in the Common wireless profile as disabled but I can't figure out how to enable it.

---

### Post by jesseAnger on 2009-07-17
I just bought a Toshiba NB200 and right away i made the mistake of letting the netbook remix of ubuntu automate it's install. After it was installed wireless didn't work i couldn't update and i got non stop errors with any packages i tried to install. I figured id start from scratch and wanted to re-partition the HDD. This proved difficult to do with a windows XP cd because it kept giving me a fatal error blue screen telling me it stoped to protect my system. I decided to go get a CD-Rom drive and installed ubuntu 9.04 onto the whole drive, forget windows right! So after that was up and running i did all the updates and opened a terminal and typed sudo apt-get install linux-backports-modules-jaunty let that run and restarted. After it rebooted the wireless was enabled as a checkmark under the connections icon. So yet another example of how easy fixing the wireless is. Don't bother switching to another OS it can work with Ubuntu


but! now my audio doesn't work if you can help me with that I would greatly appreciate it.
I posted the issue here.
[http://ubuntuforums.org/showthread.php?p=7630296#post7630296](http://ubuntuforums.org/showthread.php?p=7630296#post7630296)

---

### Post by calibre97 on 2009-07-17
I've found the Linux Mint 7 live cd to be very useful for partition editing. Graphical and easy to use and it didn't destroy my XP partition like installing Fedora did. Also, you can install Rescue CD onto an SD card and put that in the slot on the front and boot to it. Follow the instructions on the Rescue CD site ([http://www.sysresccd.org/](http://www.sysresccd.org/)), including using DAEMON Tools (requires a system reboot when you install to XP) to get the files off the Rescue CD iso. Or, now that I think of it, you should be able to load the CD under XP and just copy everything there so long as view hidden/system files is enabled. Anyway, very simple process, and make sure you do the make SD card bootable step. The file is buried deep inside the ZIP file mentioned, but it's there. After creating the SD card, you've always got a bootable system, one that has a file browser, web browser, partition editor, the works. Great for troubleshooting.

As for sound on the NB205, I believe you are supposed to edit a config file in /etc to add yourself to the sound group. Have to Google that one. 

I'll be doing updates (Ethernet) and trying the backports install when I get home to get wireless working. Several people have reported it working so I'm hopeful.

---

### Post by dimeotane on 2009-07-17
I installed the latest daily build today of Ubuntu Netbook Remix 9.10 on a USB and booted it on the NB200 and wireless was up automatically!   From there I did try the adding the line to the alsa config that is recommended to get headphones working, which it did after reboot.  

It's got me wondering if we need to look at the intrepid 8.10 ALSA config file on this machine, because ALSA was working in that version.  Isn't there some way we can get the ALSA version or settings that worked in 8.10?   Or is it an issue with the kernel since 2.6.27 that this soundcard won't play through the speaker anymore?

---

### Post by calibre97 on 2009-07-18
Great, so Netbook Remix works for wireless. Dang it...but I like Mint!!!! I added myself to the pulse-audio group and enabled privileges for connecting to wireless networks and using audio devices, but it's still no go on wireless and sound. I even installed WiCD (got the .deb package from Package Manager), but it doesn't see any wireless either. Very frustrating but I'm willing to wait. I just like Mint. Would like sound, though, to watch Hulu, etc...all I need is a freakin' INF file to use Mint's ndiswrapper interface!!! 

Maybe Koala will make it all better?

---

### Post by Emiel7 on 2009-07-18
I have now also booted my Toshiba NB200 with Ubuntu 9.10 from USB, but still I do not have a wireless connection. When I type the command 'iwconfig', I get the following output:

```

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```So it looks like my network card is now recognized, but without any signal. By the way, this is the same output that I had when I had installed the jaunty backports module on 9.04. Does any of you who have managed to get wireless running an answer to the following questions:

1. Is the wireless light on the front of the notebook on? (On my computer it is off, and I do not know how to get it on)

2. Does the key combinate Fn/F8 work for you? Does it enable/disable wireless? (On my computer nothing happens when this combination is pressed)

3. Did you first run Windows XP before you tried wireless on Ubuntu? (I read that the network card must first be turned on using Windows, but first thing I did was getting rid of Windows)

4. Did you upgrade the bios?

---

### Post by dimeotane on 2009-07-18
I'm running the latest daily build of Ubuntu Netbook Remix.  Wireless starts as strong signal (68%) as my dell (which works well), but then drops to 40%.  I got a dropped WIFI connection and I couldn't re connect after.  Restarting networking didn't help. I had to reboot.  Sound works only through headphones. Webcam works well as does the SD reader on front.  No bluetooth yet.  I don't think the battery charge monitoring is accurate though it says, 100% in ubuntu and 78% in windows.  Suspend and resume seem to work well (fast too!). 



**1. Is the wireless light on the front of the notebook on? (On my computer it is off, and I do not know how to get it on)**
Yes the wireless light glows orange once I turned it on in windows the first time. 


**2. Does the key combinate Fn/F8 work for you? Does it enable/disable wireless? (On my computer nothing happens when this combination is pressed)**

Seems to do nothing for me in linux as well.  Haven't tried it in windows yet.


**3. Did you first run Windows XP before you tried wireless on Ubuntu? (I read that the network card must first be turned on using Windows, but first thing I did was getting rid of Windows)**
Yes, I was lucky to read about other people's experiences first.  I did a dd image of the drive first before booting windows, just in case I needed to restore.  Then booted windows (took forever to install!) then turned on the wireless.  I'm running ubuntu from a USB key and haven't decided yet if it works well enough to install. 


**4. Did you upgrade the bios?**
No, my unit has v 1.2 bios already which I think is the most current.

---

### Post by Emiel7 on 2009-07-19
Thank you for your answer. This gets me in the highly frustrating situation that I need windows to enable my wireless card, which I do not have. Does anyone have a good suggestion to activate the wireless card without Windows?

---

### Post by arda78 on 2009-07-19
I have installed ubuntu 9.04 two weeks ago on my Asus K50IN notebook. Wireless connection interface didn't work by defult. After a quick search I've found this package and installed on my machine.

apt-get install linux-backports-modules-jaunty

Then wlan0 inferface became visible and I was able to use wireless connection. But wireless connection is dopping many times and its strength looks lower then expected. My Linksys wireless router is quite close to my asus notebook and normally connection strength should be about %95 but it looks about %65-%70

Here is the kernel version,
cat /proc/version_signature
Ubuntu 2.6.28-13.45-generic

Wireless network adapter model,
lspci -k | grep -A3 "Network controller"
05:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
Kernel driver in use: ath9k
Kernel modules: ath9k

iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11bgn ESSID:"arda"
          Mode:Managed Frequency:2.462 GHz Access Point: 00:1A:70:95:D0:04
          Bit Rate=1 Mb/s Tx-Power=20 dBm
          Retry min limit:7 RTS thr:off Fragment thr=2352 B
          Encryption key:off
          Power Management:off
          Link Quality=57/70 Signal level=-53 dBm
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0

pan0 no wireless extensions.

```
dmesg | grep wlan0
[   23.836406] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.298221] wlan0: direct probe to AP f61006b8 try 1
[   25.496122] wlan0: direct probe to AP f61006b8 try 2
[   25.696122] wlan0: direct probe to AP f61006b8 try 3
[   25.896052] wlan0: direct probe to AP f61006b8 timed out
[   35.346903] wlan0: authenticate with AP f61006b8
[   35.348933] wlan0: authenticated
[   35.348937] wlan0: associate with AP f61006b8
[   35.351285] wlan0: RX AssocResp from f5eec04a (capab=0x401 status=0 aid=4)
[   35.351289] wlan0: associated
[   35.351570] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.036033] wlan0: no IPv6 routers present
[ 4208.136028] wlan0: beacon loss from AP f61006b8 - sending probe request
[ 4210.136032] wlan0: no probe response from AP f61006b8 - disassociating
[ 4217.795766] wlan0: authenticate with AP f61006b8
[ 4217.797656] wlan0: authenticated
[ 4217.797660] wlan0: associate with AP f61006b8
[ 4217.799875] wlan0: RX ReassocResp from f5f2804a (capab=0x401 status=0 aid=4)
[ 4217.799879] wlan0: associated
[ 7298.404029] wlan0: beacon loss from AP f61006b8 - sending probe request
[ 7300.404031] wlan0: no probe response from AP f61006b8 - disassociating
[28202.411719] wlan0: authenticate with AP f61006b8
[28202.421560] wlan0: authenticate with AP f61006b8
[28202.423417] wlan0: authenticated
[28202.423420] wlan0: associate with AP f61006b8
[28202.425812] wlan0: RX AssocResp from f49ea04a (capab=0x401 status=0 aid=4)
[28202.425816] wlan0: associated
[58808.724068] wlan0: beacon loss from AP f61006b8 - sending probe request
[58810.724061] wlan0: no probe response from AP f61006b8 - disassociating
[73293.847465] wlan0: direct probe to AP f61006b8 try 1
[73293.857097] wlan0: authenticate with AP f61006b8
[73293.858793] wlan0 direct probe responded
[73293.858796] wlan0: authenticate with AP f61006b8
[73293.860108] wlan0: authenticated
[73293.860113] wlan0: associate with AP f61006b8
[73293.863951] wlan0: RX AssocResp from f5fc804a (capab=0x401 status=0 aid=4)
[73293.863955] wlan0: associated
[78372.244035] wlan0: beacon loss from AP f61006b8 - sending probe request
[78374.244021] wlan0: no probe response from AP f61006b8 - disassociating
[78381.928315] wlan0: authenticate with AP f61006b8
[78381.930183] wlan0: authenticated
[78381.930187] wlan0: associate with AP f61006b8
[78381.932546] wlan0: RX ReassocResp from f582804a (capab=0x401 status=0 aid=4)
[78381.932550] wlan0: associated
[81280.516024] wlan0: beacon loss from AP f61006b8 - sending probe request
[81282.516033] wlan0: no probe response from AP f61006b8 - disassociating
[81290.194855] wlan0: authenticate with AP f61006b8
[81290.204671] wlan0: authenticate with AP f61006b8
[81290.206530] wlan0: authenticated
[81290.206534] wlan0: associate with AP f61006b8
[81290.208777] wlan0: RX ReassocResp from f59d804a (capab=0x401 status=0 aid=4)
[81290.208781] wlan0: associated
[99700.508041] wlan0: beacon loss from AP f61006b8 - sending probe request
[99702.508039] wlan0: no probe response from AP f61006b8 - disassociating
[99710.187409] wlan0: authenticate with AP f61006b8
[99710.189302] wlan0: authenticated
[99710.189306] wlan0: associate with AP f61006b8
[99710.191523] wlan0: RX ReassocResp from f492204a (capab=0x401 status=0 aid=4)
[99710.191527] wlan0: associated
[112180.516036] wlan0: beacon loss from AP f61006b8 - sending probe request
[112182.516025] wlan0: no probe response from AP f61006b8 - disassociating
[127140.333865] wlan0: direct probe to AP f61006b8 try 1
[127140.352752] wlan0: authenticate with AP f61006b8
[127140.356524] wlan0: authenticated
[127140.356529] wlan0: associate with AP f61006b8
[127140.358895] wlan0: RX AssocResp from f4af604a (capab=0x401 status=0 aid=1)
[127140.358899] wlan0: associated
[187392.608031] wlan0: beacon loss from AP f61006b8 - sending probe request
[187394.608030] wlan0: no probe response from AP f61006b8 - disassociating
[202340.155994] wlan0: direct probe to AP f61006b8 try 1
[202340.165625] wlan0: authenticate with AP f61006b8
[202340.175666] wlan0: authenticate with AP f61006b8
[202340.177544] wlan0: authenticated
[202340.177547] wlan0: associate with AP f61006b8
[202340.179894] wlan0: RX AssocResp from f4b5804a (capab=0x401 status=0 aid=1)
[202340.179897] wlan0: associated
[204675.116038] wlan0: beacon loss from AP f61006b8 - sending probe request
[204677.116030] wlan0: no probe response from AP f61006b8 - disassociating
[204684.803996] wlan0: authenticate with AP f61006b8
[204684.813832] wlan0: authenticate with AP f61006b8
[204684.815709] wlan0: authenticated
[204684.815713] wlan0: associate with AP f61006b8
[204684.817926] wlan0: RX ReassocResp from f630004a (capab=0x401 status=0 aid=1)
[204684.817930] wlan0: associated
[230385.228029] wlan0: beacon loss from AP f61006b8 - sending probe request
[230387.228027] wlan0: no probe response from AP f61006b8 - disassociating
[243370.649896] wlan0: direct probe to AP f61006b8 try 1
[243370.668560] wlan0: authenticate with AP f61006b8
[243370.671508] wlan0: authenticated
[243370.671512] wlan0: associate with AP f61006b8
[243370.673879] wlan0: RX AssocResp from f4b4c04a (capab=0x401 status=0 aid=1)
[243370.673884] wlan0: associated
[257624.264026] wlan0: beacon loss from AP f61006b8 - sending probe request
[257626.264026] wlan0: no probe response from AP f61006b8 - disassociating
[257633.924422] wlan0: authenticate with AP f61006b8
[257633.926284] wlan0: authenticated
[257633.926287] wlan0: associate with AP f61006b8
[257633.928610] wlan0: RX ReassocResp from ef2be04a (capab=0x401 status=0 aid=1)
[257633.928614] wlan0: associated
[270466.008032] wlan0: beacon loss from AP f61006b8 - sending probe request
[270468.008027] wlan0: no probe response from AP f61006b8 - disassociating
[270483.492684] wlan0: direct probe to AP f61006b8 try 1
[270483.692028] wlan0: direct probe to AP f61006b8 try 2
[270483.892025] wlan0: direct probe to AP f61006b8 try 3
[270484.092024] wlan0: direct probe to AP f61006b8 timed out
[270488.203559] wlan0: authenticate with AP f61006b8
[270488.205582] wlan0: authenticated
[270488.205586] wlan0: associate with AP f61006b8
[270488.207932] wlan0: RX AssocResp from f58a604a (capab=0x401 status=0 aid=1)
[270488.207936] wlan0: associated
[317116.504031] wlan0: beacon loss from AP f61006b8 - sending probe request
[317118.504033] wlan0: no probe response from AP f61006b8 - disassociating
[317551.977962] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[317576.156125] wlan0: authenticate with AP f61006b8
[317576.166235] wlan0: authenticate with AP f61006b8
[317576.168783] wlan0: authenticated
[317576.168789] wlan0: associate with AP f61006b8
[317576.172641] wlan0: RX AssocResp from f49f004a (capab=0x401 status=0 aid=1)
[317576.172646] wlan0: associated
[317576.197894] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[317586.468018] wlan0: no IPv6 routers present
[318028.732029] wlan0: beacon loss from AP f61006b8 - sending probe request
[318030.732036] wlan0: no probe response from AP f61006b8 - disassociating
[318909.457429] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[318969.463504] wlan0: authenticate with AP f61006b8
[318969.465523] wlan0: authenticated
[318969.465527] wlan0: associate with AP f61006b8
[318969.468915] wlan0: RX AssocResp from f5f7e04a (capab=0x401 status=0 aid=1)
[318969.468919] wlan0: associated
[318969.469292] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[318979.896028] wlan0: no IPv6 routers present
```
The bad thing is when the connection drops it can not reconnect to network. It's not possible to connect my notebook remotely in that case.

Wireless network connection is very unstable. Please tell me a solution, what should I do to make my wireless connection working properly.


I have ported all my data, exported email data from outlook to evolution etc. from windows to ubuntu. But this unstable wireless network connection frustrating me a lot and I've spent a lot of time just for get it worked. 

Somebody should provide a working stable solution such a simple and basic feature which has to be normally working on ubuntu. I can provide logs or any information you need. 


I don't want to go back to windows and need your help. 


regards

---

### Post by calibre97 on 2009-07-20
Well, arda78, you got further than I did with the backports module install. I never did see anything under Mint 7 (Ubuntu 9.04-based). I installed from the Live CD, ran updates with Ethernet, and installed the backports. I even tried installing WiCD. Nada. Never did see wireless. Never say wlan0 alive or even possible anywhere. This Atheros chip is just too new. The Fedora 11 Live CD is able to use the chip and get me onto my WPA2 network (Airport Extreme), but when I installed it to disk, wireless stopped after a couple reboots.

Looks like we'll have to wait for October for the 2.6.29 kernel and better support for Atheros, or an INF file from the Windows driver (if it's even possible to obtain it) to use with ndiswrapper.

---

### Post by jedifarfy on 2009-08-02
Hello! I'm new to Linux, and have the exact same problem on a different computer. I'm using an Asus EEE 1005HA. All of my configurations pop up nearly the same as everyone else. I did a dual boot with preinstalled Windows XP. both wired and wireless work perfect on XP, and not a thing on Ubuntu 9.04.

Is there any hope to getting wireless? Has anyone made any progress? I've tried, and failed at, everything except reinstall over Windows, which I don't want to do just in case it doesn't work (I'm paranoid).

JF

---

### Post by tzirtzi on 2009-08-14
I recently bought an NB200 and foolishly installed Ubuntu on it before reading this thread - as a result I'm having various problems, one of which is that Windows XP won't boot. I understand that running the chkdsk utility from a working Windows installation should fix this problem, but I don't have the torx screwdriver necessary to take the hard disk out of the netbook. The chkdsk utility is also available on the XP installation CD (I think) but obviously the netbook doesn't have a CD drive. I've been trying to copy  an image of the CD onto a usb key or hard disk partition and boot from it, but without any success. Should this be possible, or am I wasting my time?

Thanks,
tzirtzi

---

### Post by Nick255 on 2009-08-18
You can enable wireless (and bluetooth) without Windows by using the omnibook module with ectype=12.  Once you compile and install the omnibook driver, you must load it with modprobe omnibook ectype=12, then you can use 'echo 1 >/proc/omnibook/wifi' to turn it on.  Note that some NB200/NB205 guides will tell you to use ectype=14, ignore that and use ectype=12 instead.  Also, be sure you do NOT use btcoex_enable=1 with the ath9k module or wifi won't work.  Wifi and bluetooth coexist perfectly without enabling bluetooth coexistance in the ath9k driver.

---

### Post by Emiel7 on 2009-08-30
Thank you Nick, I managed to enable the wireless card with Omnibook, just like you wrote.

---

### Post by bigkevracer on 2009-08-30
> **tzirtzi said:**
> I recently bought an NB200 and foolishly installed Ubuntu on it before reading this thread - as a result I'm having various problems, one of which is that Windows XP won't boot. I understand that running the chkdsk utility from a working Windows installation should fix this problem, but I don't have the torx screwdriver necessary to take the hard disk out of the netbook. The chkdsk utility is also available on the XP installation CD (I think) but obviously the netbook doesn't have a CD drive. I've been trying to copy  an image of the CD onto a usb key or hard disk partition and boot from it, but without any success. Should this be possible, or am I wasting my time?

Thanks,
tzirtzi

I'm in a similar boat... I'm experiencing the same problem but I'm not able to remove the HD and put it in another machine. Is there another way to fix this problem?

Thanks!

---

### Post by XLnxNewbX on 2010-01-22
could ne body help me i have somewhat of the same problems as everyone else only my iwconfig gives me l0 pan0 but no Eth0... i know im a newb but alot of other  linux masters couldnt help me... someone plzzz help!!!!!!!!!!

---

