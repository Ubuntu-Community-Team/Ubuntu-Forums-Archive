---
title: "Ralink rt2800pci - can't make wireless work"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by rocsco on 2011-11-17
I see this isn't a new problem. I've tried all 'solutions' and none have resolved my issue.

System: HP Probook 4730s Laptop / Ubuntu 11.10 / 64 bit

Wireless worked out of the box with Windows 7 installed, prior to installing Ubuntu fresh.

After installing Ubuntu - doesn't work.

Driver from Ralink has been downloaded, compiled and installed - no joy.

I've blacklisted - no joy.

Don't know where else to go.

Hope someone can help.

Ross

Output of:
lspci -nnk; lsmod; uname -a; rfkill list; ifconfig -a; cat /etc/network/interfaces

lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: agpgart-intel
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
        Subsystem: Hewlett-Packard Company Device [103c:167d]
        Kernel driver in use: i915
        Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: mei
        Kernel modules: mei
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 [8086:1c14] (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp                                                           
00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b4)                                                     
        Kernel driver in use: pcieport                                                   
        Kernel modules: shpchp                                                           
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b4)                                                     
        Kernel driver in use: pcieport                                                   
        Kernel modules: shpchp
00:1c.7 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 [8086:1c1e] (rev b4)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: ahci
        Kernel modules: ahci
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] [1002:6760]
        Subsystem: Hewlett-Packard Company Device [103c:167d]
        Kernel driver in use: radeon
        Kernel modules: radeon
24:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2392] (rev 30)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci
24:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2391] (rev 30)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel modules: sdhci-pci
24:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2393] (rev 30)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: jmb38x_ms
        Kernel modules: jmb38x_ms
25:00.0 Network controller [0280]: Ralink corp. Device [1814:3592]
        Subsystem: Hewlett-Packard Company Device [103c:1638]
        Kernel driver in use: rt2800pci
        Kernel modules: rt3562sta, rt2800pci
26:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: r8169
        Kernel modules: r8169
27:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
        Subsystem: Hewlett-Packard Company Device [103c:167c]
        Kernel driver in use: xhci_hcd
        Kernel modules: xhci-hcd

anish@anish-1:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  12 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
rt3562sta             990799  0 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
hp_accel               21880  0 
lis3lv02d              19888  1 hp_accel
input_polldev          13896  1 lis3lv02d
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rt2800pci              18715  0 
rt2800lib              54306  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              310872  3 rt2800lib,rt2x00pci,rt2x00lib
jmb38x_ms              17646  0 
memstick               16569  1 jmb38x_ms
mei                    41480  0 
psmouse                73882  0 
cfg80211              199587  2 rt2x00lib,mac80211
serio_raw              13166  0 
soundcore              12680  1 snd
eeprom_93cx6           12725  1 rt2800pci
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
wmi                    19256  1 hp_wmi
xhci_hcd               78641  0 
radeon               1015995  0 
r8169                  52788  0 
ttm                    76805  1 radeon
i915                  566711  4 
video                  19412  1 i915
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci
ahci                   26002  2 
drm_kms_helper         42558  2 radeon,i915
libahci                26861  1 ahci
drm                   236330  7 radeon,i915,ttm,drm_kms_helper
i2c_algo_bit           13423  2 radeon,i915

anish@anish-1:~$ uname -a
Linux anish-1 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
anish@anish-1:~$ rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: hp-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: hp-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
4: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
anish@anish-1:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
anish@anish-1:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 10:1f:74:eb:af:9d  
          inet addr:192.168.38.83  Bcast:192.168.38.255  Mask:255.255.255.0
          inet6 addr: fe80::121f:74ff:feeb:af9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:990 errors:0 dropped:0 overruns:0 frame:0
          TX packets:562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:375200 (375.2 KB)  TX bytes:69047 (69.0 KB)
          Interrupt:48 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13364 (13.3 KB)  TX bytes:13364 (13.3 KB)

wlan0     Link encap:Ethernet  HWaddr d0:df:9a:e0:41:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

anish@anish-1:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by marinara on 2011-11-17
probably won't work, but make sure wireless off switch isn't set, make sure thin ethernet cable is unplugged

**edit**  can you ping your router?  I'm asking b/c you look like you have an IP address. You wouldn't have a IP address if something wasn't working

**edit 2** never mind above... the ip address is on your non-wireless ethernet.  but still I've heard wireless doesn't work when it's plugged in.  I swear to god i heard that.

---

