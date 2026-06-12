---
title: "What type of Router should I buy?"
date: 2012-02-03
forum: Networking &amp; Wireless
---

### Post by Sxynerd on 2012-02-03
My router is acting up lately and I want to buy a new one.  I've had people reference that a lot of my connection issues is because of the WPA2 encryption.   I really have no idea what this mean or what I should look for in a Router so I thought I'd ask the crowd.

Right now I have 2 Ubuntu machines, 1 Windows PC and a few tablets all connecting to a standard home network.  (None of the computers are connected together.

Here is some info from my main laptop, I think it will show the kind of Linxus router I have now but I'm not for sure.

```
**wolvee@wolvee--dv7:~$ lspci -nnk**
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: mei
	Kernel modules: mei
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] [1002:6760]
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: radeon
	Kernel modules: radeon
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: r8169
	Kernel modules: r8169
0d:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0886] (rev 67)
	Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1315]
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader [10ec:5209] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: rts_pstor
	Kernel modules: rts_pstor
19:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd


**wolvee@wolvee--dv7:~$ lsmod**
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
binfmt_misc            17540  1 
joydev                 17693  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
arc4                   12529  2 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
serio_raw              13166  0 
hp_accel               21880  0 
wmi                    19256  1 hp_wmi
lis3lv02d              19888  1 hp_accel
input_polldev          13896  1 lis3lv02d
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
radeon               1016226  0 
ttm                    76805  1 radeon
iwlagn                314213  0 
mac80211              462092  1 iwlagn
rts_pstor             445246  0 
i915                  566827  3 
cfg80211              199587  2 iwlagn,mac80211
mei                    41480  0 
drm_kms_helper         42558  2 radeon,i915
drm                   236290  6 radeon,ttm,i915,drm_kms_helper
i2c_algo_bit           13423  2 radeon,i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            57901  1 
uas                    18027  0 
ahci                   26002  2 
xhci_hcd               82820  0 
libahci                26861  1 ahci
r8169                  52788  0 


**wolvee@wolvee--dv7:~$ uname -a**
Linux wolvee--dv7 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

**wolvee@wolvee--dv7:~$ rfkill list**
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

**wolvee@wolvee--dv7:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Mike_Jess"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:F2:18:B7:F8   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7121   Missed beacon:0

wolvee@wolvee--dv7:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Mike_Jess"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:F2:18:B7:F8   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7121   Missed beacon:0

**wolvee@wolvee--dv7:~$ ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 2c:27:d7:ab:71:2e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44700 (44.7 KB)  TX bytes:44700 (44.7 KB)

wlan0     Link encap:Ethernet  HWaddr 40:25:c2:33:02:4c  
          inet addr:192.168.1.18  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4225:c2ff:fe33:24c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1029987 errors:0 dropped:0 overruns:0 frame:0
          TX packets:731211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1340986351 (1.3 GB)  TX bytes:93777965 (93.7 MB)


**wolvee@wolvee--dv7:~$ cat /etc/network/interfaces**
auto lo
iface lo inet loopback

```

---

### Post by Derek Karpinski on 2012-02-03
I would NOT buy a D-Link DIR-615. It sporatically will drop all wireless connections and require a reboot. Never been able to figure it out. It was cheap though. :)
 
Also, if I were to buy a new router, I would most definately flash it with DD-WRT right away.  I'd look on their website to find a compatible router, and preferably a router with enough memory to run a VPN service (if you need one).  DD-WRT is great, and you'll feel at home if you use linux.

---

### Post by Dangertux on 2012-02-03
Conversely I've had a good experience with my DIR-615

That being said most routers in the 30-150 dollar range have pretty much the same features

---

### Post by hvanzile on 2012-02-03
I had a similar experience to Derek's, but finally figured out that it was related to buggy DHCP leasing.  Once I put everything on static IPs it worked fine.  I recently flashed the router to DD-WRT (and then Gargoyle) and since then everything is working fine, including DHCP connections.  

Careful with that approach, though - not all hardware revisions of the DIR-615 work with alternate firmwares.

---

