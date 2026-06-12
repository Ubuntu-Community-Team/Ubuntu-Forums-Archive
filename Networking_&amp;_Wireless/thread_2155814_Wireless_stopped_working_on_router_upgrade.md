---
title: "Wireless stopped working on router upgrade"
date: 2013-06-19
forum: Networking &amp; Wireless
---

### Post by SMButler on 2013-06-19
Using Ubuntu 13.04.  All was going great until I updated the house router.  I used the same SSID and passphrase.  All other wireless devices continue to work (cell phone, printer, wife's windows laptop).  However, my Ubuntu laptop can't reach the router.  It shows up in the router's client table and the router is able to open the default web on the laptop.

At least the Windows 7 wired box is getting decent download speeds (60 Mbit/s from Comcast).

On Ubuntu a ping to 192.168.1.1 (which is the address of the router) either has 90+% packet loss or I get the message "192.168.1.1 host unreachable".

It must be something about the new bands/capabilities of the router that Ubuntu isn't handling correctly?

Below are the steps requested in the sticky.  However, the filter statements returned zero lines.  So, the verbose listings are below. sorry for being so big.

By the way, I'm at work now and the box is working fine with that (unknown type) wireless network.  Lends me more to think an incompatibility between the PC and the new house router.


Step 1:
Old router:  Asus WL-520GU (100 Mbit)   (802.11b,g)
New router:  Asus RT-AC66U ( 1 Gbit)    (802.11a,b,g,n,ac; 802.3u
Wireless Laptop:  Asus UX32V Notebook PC (802.11a,b,g,n)

Step 2:
```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
00:04.0 Signal processing controller [1180]: Intel Corporation 3rd Gen Core Processor Thermal Subsystem [8086:0153] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
00:1f.6 Signal processing controller [1180]: Intel Corporation 7 Series/C210 Series Chipset Family Thermal Management Controller [8086:1e24] (rev 04)
01:00.0 3D controller [0302]: NVIDIA Corporation GF117M [GeForce 610M/710M / GT 620M/625M/630M/720M] [10de:1140] (rev a1)
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)

lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. Card reader
Bus 002 Device 003: ID 04f2:b330 Chicony Electronics Co., Ltd 

Step 3:
ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5244 (5.2 KB)  TX bytes:5244 (5.2 KB)

wlan0     Link encap:Ethernet  HWaddr c4:85:08:36:65:cd  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:187743 (187.7 KB)  TX bytes:21123 (21.1 KB)

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"SMBWMFB"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 74:D0:2B:41:B8:C8   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-24 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:70   Missed beacon:0

Step 4:
lsmod
Module                  Size  Used by
usb_storage            57204  1 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
binfmt_misc            17500  1 
joydev                 17377  0 
arc4                   12615  2 
iwldvm                241872  0 
mac80211              606457  1 iwldvm
nls_iso8859_1          12713  2 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  2 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
asus_nb_wmi            12854  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
asus_wmi               24213  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
nouveau               939088  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
i915                  600396  3 
mxm_wmi                13021  1 nouveau
wmi                    19070  3 mxm_wmi,nouveau,asus_wmi
videobuf2_memops       13202  1 videobuf2_vmalloc
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
video                  19390  3 i915,nouveau,asus_wmi
ttm                    83187  1 nouveau
iwlwifi               173477  1 iwldvm
videobuf2_core         40513  1 uvcvideo
mac_hid                13205  0 
rts5139               352481  0 
videodev              129260  2 uvcvideo,videobuf2_core
drm_kms_helper         49394  2 i915,nouveau
soundcore              12680  1 snd
mei                    41158  0 
microcode              22881  0 
cfg80211              510937  3 iwlwifi,mac80211,iwldvm
drm                   286028  6 ttm,i915,drm_kms_helper,nouveau
lpc_ich                17061  0 
btusb                  22474  0 
bluetooth             228619  11 bnep,btusb,rfcomm
i2c_algo_bit           13413  2 i915,nouveau
psmouse                95870  0 
serio_raw              13215  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
ahci                   25731  4 
libahci                31364  1 ahci

Step 5:  long listing
Note:  I do see a message flash at first boot up.  Got the camera and transcribed the following:
[17.376241] nouveau ![ DEVICE] [0000:01:00:00] unknown Fermi chipset
[17.376284] nouveau E[ DEVICE] [0000:01:00:00] unknown chipset, 0x0d7000a2
[17.376322] nouveau E[    DRM] failed to create 0x80000080, -22


dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-25-generic (buildd@roseapple) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #37-Ubuntu SMP Thu Jun 6 20:47:07 UTC 2013 (Ubuntu 3.8.0-25.37-generic 3.8.13)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.8.0-25-generic root=UUID=5de0bfd2-f4fa-4eb2-967b-ae0eb530d798 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000c9728fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9729000-0x00000000c9d29fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000c9d2a000-0x00000000c9d2cfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9d2d000-0x00000000c9d43fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9d44000-0x00000000c9d49fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9d4a000-0x00000000c9d4bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9d4c000-0x00000000c9d50fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9d51000-0x00000000c9ee5fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9ee6000-0x00000000c9ee9fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9eea000-0x00000000c9f33fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9f34000-0x00000000c9f3afff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9f3b000-0x00000000c9f3cfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9f3d000-0x00000000c9f5afff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9f5b000-0x00000000c9f5dfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9f5e000-0x00000000c9f5ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9f60000-0x00000000c9f76fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9f77000-0x00000000c9f7cfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9f7d000-0x00000000c9f84fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9f85000-0x00000000c9f85fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9f86000-0x00000000c9f94fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9f95000-0x00000000c9f95fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9f96000-0x00000000c9fa0fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9fa1000-0x00000000c9fa5fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9fa6000-0x00000000c9fc4fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9fc5000-0x00000000c9fc6fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9fc7000-0x00000000c9fdbfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9fdc000-0x00000000c9fdcfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c9fdd000-0x00000000c9feefff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c9fef000-0x00000000ca015fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ca016000-0x00000000ca029fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ca02a000-0x00000000ca02afff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ca02b000-0x00000000ca02bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ca02c000-0x00000000ca02dfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ca02e000-0x00000000ca02efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ca02f000-0x00000000ca033fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ca034000-0x00000000ca04bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ca04c000-0x00000000ca610fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ca611000-0x00000000ca890fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ca891000-0x00000000ca895fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000ca896000-0x00000000ca896fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ca897000-0x00000000ca8d9fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ca8da000-0x00000000cacecfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000caced000-0x00000000caff3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000caff4000-0x00000000caffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cbc00000-0x00000000cfdfffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000002af1fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by American Megatrends
[    0.000000] efi:  ACPI=0xca85f000  ACPI 2.0=0xca85f000  SMBIOS=0xf04c0  MPS=0xfd4c0 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x000000000005e000) (0MB)
[    0.000000] efi: mem02: type=4, attr=0xf, range=[0x000000000005e000-0x0000000000060000) (0MB)
[    0.000000] efi: mem03: type=3, attr=0xf, range=[0x0000000000060000-0x000000000009f000) (0MB)
[    0.000000] efi: mem04: type=6, attr=0x800000000000000f, range=[0x000000000009f000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem05: type=7, attr=0xf, range=[0x0000000000100000-0x0000000001000000) (15MB)
[    0.000000] efi: mem06: type=2, attr=0xf, range=[0x0000000001000000-0x0000000002444000) (20MB)
[    0.000000] efi: mem07: type=7, attr=0xf, range=[0x0000000002444000-0x0000000020000000) (475MB)
[    0.000000] efi: mem08: type=0, attr=0xf, range=[0x0000000020000000-0x0000000020200000) (2MB)
[    0.000000] efi: mem09: type=7, attr=0xf, range=[0x0000000020200000-0x000000003611a000) (351MB)
[    0.000000] efi: mem10: type=2, attr=0xf, range=[0x000000003611a000-0x0000000037085000) (15MB)
[    0.000000] efi: mem11: type=7, attr=0xf, range=[0x0000000037085000-0x0000000040004000) (143MB)
[    0.000000] efi: mem12: type=0, attr=0xf, range=[0x0000000040004000-0x0000000040005000) (0MB)
[    0.000000] efi: mem13: type=7, attr=0xf, range=[0x0000000040005000-0x000000008ecc0000) (1260MB)
[    0.000000] efi: mem14: type=2, attr=0xf, range=[0x000000008ecc0000-0x00000000be729000) (762MB)
[    0.000000] efi: mem15: type=1, attr=0xf, range=[0x00000000be729000-0x00000000be747000) (0MB)
[    0.000000] efi: mem16: type=7, attr=0xf, range=[0x00000000be747000-0x00000000be765000) (0MB)
[    0.000000] efi: mem17: type=4, attr=0xf, range=[0x00000000be765000-0x00000000be77e000) (0MB)
[    0.000000] efi: mem18: type=7, attr=0xf, range=[0x00000000be77e000-0x00000000be787000) (0MB)
[    0.000000] efi: mem19: type=4, attr=0xf, range=[0x00000000be787000-0x00000000be93e000) (1MB)
[    0.000000] efi: mem20: type=7, attr=0xf, range=[0x00000000be93e000-0x00000000be946000) (0MB)
[    0.000000] efi: mem21: type=4, attr=0xf, range=[0x00000000be946000-0x00000000c90ad000) (167MB)
[    0.000000] efi: mem22: type=7, attr=0xf, range=[0x00000000c90ad000-0x00000000c96f7000) (6MB)
[    0.000000] efi: mem23: type=2, attr=0xf, range=[0x00000000c96f7000-0x00000000c9703000) (0MB)
[    0.000000] efi: mem24: type=3, attr=0xf, range=[0x00000000c9703000-0x00000000c9729000) (0MB)
[    0.000000] efi: mem25: type=10, attr=0xf, range=[0x00000000c9729000-0x00000000c9d2a000) (6MB)
[    0.000000] efi: mem26: type=5, attr=0x800000000000000f, range=[0x00000000c9d2a000-0x00000000c9d2d000) (0MB)
[    0.000000] efi: mem27: type=3, attr=0xf, range=[0x00000000c9d2d000-0x00000000c9d44000) (0MB)
[    0.000000] efi: mem28: type=5, attr=0x800000000000000f, range=[0x00000000c9d44000-0x00000000c9d4a000) (0MB)
[    0.000000] efi: mem29: type=3, attr=0xf, range=[0x00000000c9d4a000-0x00000000c9d4c000) (0MB)
[    0.000000] efi: mem30: type=5, attr=0x800000000000000f, range=[0x00000000c9d4c000-0x00000000c9d51000) (0MB)
[    0.000000] efi: mem31: type=3, attr=0xf, range=[0x00000000c9d51000-0x00000000c9ee6000) (1MB)
[    0.000000] efi: mem32: type=5, attr=0x800000000000000f, range=[0x00000000c9ee6000-0x00000000c9eea000) (0MB)
[    0.000000] efi: mem33: type=3, attr=0xf, range=[0x00000000c9eea000-0x00000000c9f34000) (0MB)
[    0.000000] efi: mem34: type=5, attr=0x800000000000000f, range=[0x00000000c9f34000-0x00000000c9f3b000) (0MB)
[    0.000000] efi: mem35: type=3, attr=0xf, range=[0x00000000c9f3b000-0x00000000c9f3d000) (0MB)
[    0.000000] efi: mem36: type=6, attr=0x800000000000000f, range=[0x00000000c9f3d000-0x00000000c9f4a000) (0MB)
[    0.000000] efi: mem37: type=5, attr=0x800000000000000f, range=[0x00000000c9f4a000-0x00000000c9f5b000) (0MB)
[    0.000000] efi: mem38: type=3, attr=0xf, range=[0x00000000c9f5b000-0x00000000c9f5e000) (0MB)
[    0.000000] efi: mem39: type=5, attr=0x800000000000000f, range=[0x00000000c9f5e000-0x00000000c9f60000) (0MB)
[    0.000000] efi: mem40: type=3, attr=0xf, range=[0x00000000c9f60000-0x00000000c9f77000) (0MB)
[    0.000000] efi: mem41: type=5, attr=0x800000000000000f, range=[0x00000000c9f77000-0x00000000c9f7d000) (0MB)
[    0.000000] efi: mem42: type=3, attr=0xf, range=[0x00000000c9f7d000-0x00000000c9f85000) (0MB)
[    0.000000] efi: mem43: type=5, attr=0x800000000000000f, range=[0x00000000c9f85000-0x00000000c9f86000) (0MB)
[    0.000000] efi: mem44: type=3, attr=0xf, range=[0x00000000c9f86000-0x00000000c9f95000) (0MB)
[    0.000000] efi: mem45: type=5, attr=0x800000000000000f, range=[0x00000000c9f95000-0x00000000c9f96000) (0MB)
[    0.000000] efi: mem46: type=3, attr=0xf, range=[0x00000000c9f96000-0x00000000c9fa1000) (0MB)
[    0.000000] efi: mem47: type=5, attr=0x800000000000000f, range=[0x00000000c9fa1000-0x00000000c9fa6000) (0MB)
[    0.000000] efi: mem48: type=3, attr=0xf, range=[0x00000000c9fa6000-0x00000000c9fc5000) (0MB)
[    0.000000] efi: mem49: type=5, attr=0x800000000000000f, range=[0x00000000c9fc5000-0x00000000c9fc7000) (0MB)
[    0.000000] efi: mem50: type=3, attr=0xf, range=[0x00000000c9fc7000-0x00000000c9fdc000) (0MB)
[    0.000000] efi: mem51: type=5, attr=0x800000000000000f, range=[0x00000000c9fdc000-0x00000000c9fdd000) (0MB)
[    0.000000] efi: mem52: type=3, attr=0xf, range=[0x00000000c9fdd000-0x00000000c9fef000) (0MB)
[    0.000000] efi: mem53: type=5, attr=0x800000000000000f, range=[0x00000000c9fef000-0x00000000ca016000) (0MB)
[    0.000000] efi: mem54: type=3, attr=0xf, range=[0x00000000ca016000-0x00000000ca02a000) (0MB)
[    0.000000] efi: mem55: type=5, attr=0x800000000000000f, range=[0x00000000ca02a000-0x00000000ca02b000) (0MB)
[    0.000000] efi: mem56: type=3, attr=0xf, range=[0x00000000ca02b000-0x00000000ca02c000) (0MB)
[    0.000000] efi: mem57: type=5, attr=0x800000000000000f, range=[0x00000000ca02c000-0x00000000ca02e000) (0MB)
[    0.000000] efi: mem58: type=3, attr=0xf, range=[0x00000000ca02e000-0x00000000ca02f000) (0MB)
[    0.000000] efi: mem59: type=5, attr=0x800000000000000f, range=[0x00000000ca02f000-0x00000000ca034000) (0MB)
[    0.000000] efi: mem60: type=3, attr=0xf, range=[0x00000000ca034000-0x00000000ca04c000) (0MB)
[    0.000000] efi: mem61: type=6, attr=0x800000000000000f, range=[0x00000000ca04c000-0x00000000ca0cd000) (0MB)
[    0.000000] efi: mem62: type=5, attr=0x800000000000000f, range=[0x00000000ca0cd000-0x00000000ca0e7000) (0MB)
[    0.000000] efi: mem63: type=6, attr=0x800000000000000f, range=[0x00000000ca0e7000-0x00000000ca0eb000) (0MB)
[    0.000000] efi: mem64: type=6, attr=0x800000000000000f, range=[0x00000000ca0eb000-0x00000000ca0f1000) (0MB)
[    0.000000] efi: mem65: type=6, attr=0x800000000000000f, range=[0x00000000ca0f1000-0x00000000ca0f3000) (0MB)
[    0.000000] efi: mem66: type=6, attr=0x800000000000000f, range=[0x00000000ca0f3000-0x00000000ca111000) (0MB)
[    0.000000] efi: mem67: type=0, attr=0xf, range=[0x00000000ca111000-0x00000000ca20e000) (0MB)
[    0.000000] efi: mem68: type=0, attr=0xf, range=[0x00000000ca20e000-0x00000000ca5a6000) (3MB)
[    0.000000] efi: mem69: type=0, attr=0xf, range=[0x00000000ca5a6000-0x00000000ca5ac000) (0MB)
[    0.000000] efi: mem70: type=0, attr=0xf, range=[0x00000000ca5ac000-0x00000000ca611000) (0MB)
[    0.000000] efi: mem71: type=10, attr=0xf, range=[0x00000000ca611000-0x00000000ca6cd000) (0MB)
[    0.000000] efi: mem72: type=10, attr=0xf, range=[0x00000000ca6cd000-0x00000000ca879000) (1MB)
[    0.000000] efi: mem73: type=10, attr=0xf, range=[0x00000000ca879000-0x00000000ca87c000) (0MB)
[    0.000000] efi: mem74: type=10, attr=0xf, range=[0x00000000ca87c000-0x00000000ca891000) (0MB)
[    0.000000] efi: mem75: type=9, attr=0xf, range=[0x00000000ca891000-0x00000000ca896000) (0MB)
[    0.000000] efi: mem76: type=4, attr=0xf, range=[0x00000000ca896000-0x00000000ca897000) (0MB)
[    0.000000] efi: mem77: type=10, attr=0xf, range=[0x00000000ca897000-0x00000000ca8da000) (0MB)
[    0.000000] efi: mem78: type=4, attr=0xf, range=[0x00000000ca8da000-0x00000000caa26000) (1MB)
[    0.000000] efi: mem79: type=3, attr=0xf, range=[0x00000000caa26000-0x00000000cacbe000) (2MB)
[    0.000000] efi: mem80: type=4, attr=0xf, range=[0x00000000cacbe000-0x00000000cacc3000) (0MB)
[    0.000000] efi: mem81: type=3, attr=0xf, range=[0x00000000cacc3000-0x00000000cacc7000) (0MB)
[    0.000000] efi: mem82: type=4, attr=0xf, range=[0x00000000cacc7000-0x00000000cacd4000) (0MB)
[    0.000000] efi: mem83: type=3, attr=0xf, range=[0x00000000cacd4000-0x00000000cace6000) (0MB)
[    0.000000] efi: mem84: type=4, attr=0xf, range=[0x00000000cace6000-0x00000000caced000) (0MB)
[    0.000000] efi: mem85: type=6, attr=0x800000000000000f, range=[0x00000000caced000-0x00000000caff4000) (3MB)
[    0.000000] efi: mem86: type=4, attr=0xf, range=[0x00000000caff4000-0x00000000cb000000) (0MB)
[    0.000000] efi: mem87: type=7, attr=0xf, range=[0x0000000100000000-0x00000002af200000) (6898MB)
[    0.000000] efi: mem88: type=0, attr=0x8000000000000000, range=[0x00000000cbc00000-0x00000000cfe00000) (66MB)
[    0.000000] efi: mem89: type=11, attr=0x8000000000000001, range=[0x00000000f8000000-0x00000000fc000000) (64MB)
[    0.000000] efi: mem90: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem91: type=11, attr=0x8000000000000001, range=[0x00000000fed00000-0x00000000fed04000) (0MB)
[    0.000000] efi: mem92: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem93: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem94: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: ASUSTeK COMPUTER INC. UX32VD/UX32VD, BIOS UX32VD.212 09/17/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x2af200 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask F80000000 write-back
[    0.000000]   2 base 280000000 mask FC0000000 write-back
[    0.000000]   3 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   4 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   5 base 0CC000000 mask FFC000000 uncachable
[    0.000000]   6 base 0CBC00000 mask FFFC00000 uncachable
[    0.000000]   7 base 2B0000000 mask FF0000000 uncachable
[    0.000000]   8 base 2AF800000 mask FFF800000 uncachable
[    0.000000]   9 base 2AF400000 mask FFFC00000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 2GB, type WB
[    0.000000] reg 2, base: 10GB, range: 1GB, type WB
[    0.000000] reg 3, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 4, base: 3328MB, range: 256MB, type UC
[    0.000000] reg 5, base: 3264MB, range: 64MB, type UC
[    0.000000] reg 6, base: 3260MB, range: 4MB, type UC
[    0.000000] reg 7, base: 11008MB, range: 256MB, type UC
[    0.000000] reg 8, base: 11000MB, range: 8MB, type UC
[    0.000000] reg 9, base: 10996MB, range: 4MB, type UC
[    0.000000] total RAM covered: 10160M
[    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 64K     chunk_size: 128K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 64K     chunk_size: 256K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 64K     chunk_size: 512K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 64K     chunk_size: 1M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 64K     chunk_size: 2M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 64K     chunk_size: 4M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 64K     chunk_size: 8M     num_reg: 10      lose cover RAM: 52M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 128M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 256M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 512M     num_reg: 10      lose cover RAM: -264M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 1G     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 64K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 128K     chunk_size: 128K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 128K     chunk_size: 256K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 128K     chunk_size: 512K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 128K     chunk_size: 1M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 128K     chunk_size: 2M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 128K     chunk_size: 4M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 128K     chunk_size: 8M     num_reg: 10      lose cover RAM: 52M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 128M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 256M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 512M     num_reg: 10      lose cover RAM: -264M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 1G     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 128K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 256K     chunk_size: 256K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 256K     chunk_size: 512K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 256K     chunk_size: 1M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 256K     chunk_size: 2M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 256K     chunk_size: 4M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 256K     chunk_size: 8M     num_reg: 10      lose cover RAM: 52M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 128M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 256M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 512M     num_reg: 10      lose cover RAM: -264M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 1G     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 256K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 512K     chunk_size: 512K     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 512K     chunk_size: 1M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 512K     chunk_size: 2M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 512K     chunk_size: 4M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 512K     chunk_size: 8M     num_reg: 10      lose cover RAM: 52M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 128M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 256M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 512M     num_reg: 10      lose cover RAM: -264M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 1G     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 512K     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 1M     chunk_size: 1M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 1M     chunk_size: 2M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 1M     chunk_size: 4M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 1M     chunk_size: 8M     num_reg: 10      lose cover RAM: 52M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 128M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 256M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 512M     num_reg: 10      lose cover RAM: -264M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 1G     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 1M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 2M     chunk_size: 2M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 2M     chunk_size: 4M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 2M     chunk_size: 8M     num_reg: 10      lose cover RAM: 52M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 128M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 256M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 512M     num_reg: 10      lose cover RAM: -264M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 1G     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 2M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 4M     chunk_size: 4M     num_reg: 10      lose cover RAM: 244M
[    0.000000]  gran_size: 4M     chunk_size: 8M     num_reg: 10      lose cover RAM: 52M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 16M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 32M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 64M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 128M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 256M     num_reg: 10      lose cover RAM: -8M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 512M     num_reg: 10      lose cover RAM: -264M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 1G     num_reg: 10      lose cover RAM: -256M
[    0.000000] *BAD*gran_size: 4M     chunk_size: 2G     num_reg: 10      lose cover RAM: -1G
[    0.000000]  gran_size: 8M     chunk_size: 8M     num_reg: 10      lose cover RAM: 120M
[    0.000000]  gran_size: 8M     chunk_size: 16M     num_reg: 10      lose cover RAM: 56M
[    0.000000]  gran_size: 8M     chunk_size: 32M     num_reg: 10      lose cover RAM: 8M
[    0.000000]  gran_size: 8M     chunk_size: 64M     num_reg: 10      lose cover RAM: 8M
[    0.000000]  gran_size: 8M     chunk_size: 128M     num_reg: 10      lose cover RAM: 8M
[    0.000000]  gran_size: 8M     chunk_size: 256M     num_reg: 10      lose cover RAM: 8M
[    0.000000] *BAD*gran_size: 8M     chunk_size: 512M     num_reg: 10      lose cover RAM: -248M
[    0.000000]  gran_size: 8M     chunk_size: 1G     num_reg: 10      lose cover RAM: 8M
[    0.000000]  gran_size: 8M     chunk_size: 2G     num_reg: 10      lose cover RAM: 8M
[    0.000000]  gran_size: 16M     chunk_size: 16M     num_reg: 10      lose cover RAM: 64M
[    0.000000]  gran_size: 16M     chunk_size: 32M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 16M     chunk_size: 64M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 16M     chunk_size: 128M     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 16M     chunk_size: 256M     num_reg: 10      lose cover RAM: 16M
[    0.000000] *BAD*gran_size: 16M     chunk_size: 512M     num_reg: 10      lose cover RAM: -240M
[    0.000000]  gran_size: 16M     chunk_size: 1G     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 16M     chunk_size: 2G     num_reg: 10      lose cover RAM: 16M
[    0.000000]  gran_size: 32M     chunk_size: 32M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 32M     chunk_size: 64M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 32M     chunk_size: 128M     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 32M     chunk_size: 256M     num_reg: 10      lose cover RAM: 48M
[    0.000000] *BAD*gran_size: 32M     chunk_size: 512M     num_reg: 10      lose cover RAM: -208M
[    0.000000]  gran_size: 32M     chunk_size: 1G     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 32M     chunk_size: 2G     num_reg: 10      lose cover RAM: 48M
[    0.000000]  gran_size: 64M     chunk_size: 64M     num_reg: 8      lose cover RAM: 112M
[    0.000000]  gran_size: 64M     chunk_size: 128M     num_reg: 8      lose cover RAM: 112M
[    0.000000]  gran_size: 64M     chunk_size: 256M     num_reg: 9      lose cover RAM: 112M
[    0.000000]  gran_size: 64M     chunk_size: 512M     num_reg: 10      lose cover RAM: 112M
[    0.000000]  gran_size: 64M     chunk_size: 1G     num_reg: 9      lose cover RAM: 112M
[    0.000000]  gran_size: 64M     chunk_size: 2G     num_reg: 9      lose cover RAM: 112M
[    0.000000]  gran_size: 128M     chunk_size: 128M     num_reg: 7      lose cover RAM: 176M
[    0.000000]  gran_size: 128M     chunk_size: 256M     num_reg: 9      lose cover RAM: 176M
[    0.000000]  gran_size: 128M     chunk_size: 512M     num_reg: 10      lose cover RAM: 176M
[    0.000000]  gran_size: 128M     chunk_size: 1G     num_reg: 9      lose cover RAM: 176M
[    0.000000]  gran_size: 128M     chunk_size: 2G     num_reg: 9      lose cover RAM: 176M
[    0.000000]  gran_size: 256M     chunk_size: 256M     num_reg: 5      lose cover RAM: 432M
[    0.000000]  gran_size: 256M     chunk_size: 512M     num_reg: 5      lose cover RAM: 432M
[    0.000000]  gran_size: 256M     chunk_size: 1G     num_reg: 6      lose cover RAM: 432M
[    0.000000]  gran_size: 256M     chunk_size: 2G     num_reg: 6      lose cover RAM: 432M
[    0.000000]  gran_size: 512M     chunk_size: 512M     num_reg: 5      lose cover RAM: 432M
[    0.000000]  gran_size: 512M     chunk_size: 1G     num_reg: 6      lose cover RAM: 432M
[    0.000000]  gran_size: 512M     chunk_size: 2G     num_reg: 6      lose cover RAM: 432M
[    0.000000]  gran_size: 1G     chunk_size: 1G     num_reg: 4      lose cover RAM: 944M
[    0.000000]  gran_size: 1G     chunk_size: 2G     num_reg: 4      lose cover RAM: 944M
[    0.000000]  gran_size: 2G     chunk_size: 2G     num_reg: 3      lose cover RAM: 1968M
[    0.000000] mtrr_cleanup: can not find optimal value
[    0.000000] please specify mtrr_gran_size/mtrr_chunk_size
[    0.000000] e820: update [mem 0xcbc00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcb000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd7b0-0x000fd7bf] mapped at [ffff8800000fd7b0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xcaffffff]
[    0.000000]  [mem 0x00000000-0xcaffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xcaffffff @ [mem 0x1fffb000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x2af1fffff]
[    0.000000]  [mem 0x100000000-0x2af1fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x2af1fffff @ [mem 0xc96fb000-0xc9702fff]
[    0.000000] RAMDISK: [mem 0x3611a000-0x37084fff]
[    0.000000] ACPI: RSDP 00000000ca85f000 00024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 00000000ca85f090 000A4 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000ca8732e8 0010C (v05 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000ca85f1c0 14126 (v02 _ASUS_ Notebook 00000013 INTL 20091112)
[    0.000000] ACPI: FACS 00000000ca88e080 00040
[    0.000000] ACPI: APIC 00000000ca8733f8 00072 (v03 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000ca873470 00044 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: ECDT 00000000ca8734b8 000C1 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
[    0.000000] ACPI: MCFG 00000000ca873580 0003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000ca8735c0 00A3C (v01 DptfTa  DptfTab 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000ca874000 00CA5 (v01 SADptf  SADptf_ 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000ca874ca8 00098 (v01 PchDpt  PchDptf 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000ca874d40 0091C (v01 CfgTDP  CfgTDP_ 00001000 INTL 20091112)
[    0.000000] ACPI: HPET 00000000ca875660 00038 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000ca875698 0049A (v01 AhciR1 AhciTab1 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000ca875b38 0049E (v01 AhciR2 AhciTab2 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000ca875fd8 009D0 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000ca8769a8 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: DMAR 00000000ca877440 000B8 (v01 INTEL      SNB  00000001 INTL 00000001)
[    0.000000] ACPI: MSDM 00000000ca610e18 00055 (v03 _ASUS_ Notebook 00000000 ASUS 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000002af1fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x2af1fffff]
[    0.000000]   NODE_DATA [mem 0x2af1fb000-0x2af1fffff]
[    0.000000]  [ffffea0000000000-ffffea000abfffff] PMD -> [ffff8802a4800000-ffff8802ae7fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x2af1fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xc9728fff]
[    0.000000]   node   0: [mem 0xc9d2d000-0xc9d43fff]
[    0.000000]   node   0: [mem 0xc9d4a000-0xc9d4bfff]
[    0.000000]   node   0: [mem 0xc9d51000-0xc9ee5fff]
[    0.000000]   node   0: [mem 0xc9eea000-0xc9f33fff]
[    0.000000]   node   0: [mem 0xc9f3b000-0xc9f3cfff]
[    0.000000]   node   0: [mem 0xc9f5b000-0xc9f5dfff]
[    0.000000]   node   0: [mem 0xc9f60000-0xc9f76fff]
[    0.000000]   node   0: [mem 0xc9f7d000-0xc9f84fff]
[    0.000000]   node   0: [mem 0xc9f86000-0xc9f94fff]
[    0.000000]   node   0: [mem 0xc9f96000-0xc9fa0fff]
[    0.000000]   node   0: [mem 0xc9fa6000-0xc9fc4fff]
[    0.000000]   node   0: [mem 0xc9fc7000-0xc9fdbfff]
[    0.000000]   node   0: [mem 0xc9fdd000-0xc9feefff]
[    0.000000]   node   0: [mem 0xca016000-0xca029fff]
[    0.000000]   node   0: [mem 0xca02b000-0xca02bfff]
[    0.000000]   node   0: [mem 0xca02e000-0xca02efff]
[    0.000000]   node   0: [mem 0xca034000-0xca04bfff]
[    0.000000]   node   0: [mem 0xca896000-0xca896fff]
[    0.000000]   node   0: [mem 0xca8da000-0xcacecfff]
[    0.000000]   node   0: [mem 0xcaff4000-0xcaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x2af1fffff]
[    0.000000] On node 0 totalpages: 2592129
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 12 pages reserved
[    0.000000]   DMA zone: 3907 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12848 pages used for memmap
[    0.000000]   DMA32 zone: 809410 pages, LIFO batch:31
[    0.000000]   Normal zone: 27592 pages used for memmap
[    0.000000]   Normal zone: 1738296 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
[    0.000000] PM: Registered nosave memory: 00000000c9729000 - 00000000c9d2a000
[    0.000000] PM: Registered nosave memory: 00000000c9d2a000 - 00000000c9d2d000
[    0.000000] PM: Registered nosave memory: 00000000c9d44000 - 00000000c9d4a000
[    0.000000] PM: Registered nosave memory: 00000000c9d4c000 - 00000000c9d51000
[    0.000000] PM: Registered nosave memory: 00000000c9ee6000 - 00000000c9eea000
[    0.000000] PM: Registered nosave memory: 00000000c9f34000 - 00000000c9f3b000
[    0.000000] PM: Registered nosave memory: 00000000c9f3d000 - 00000000c9f5b000
[    0.000000] PM: Registered nosave memory: 00000000c9f5e000 - 00000000c9f60000
[    0.000000] PM: Registered nosave memory: 00000000c9f77000 - 00000000c9f7d000
[    0.000000] PM: Registered nosave memory: 00000000c9f85000 - 00000000c9f86000
[    0.000000] PM: Registered nosave memory: 00000000c9f95000 - 00000000c9f96000
[    0.000000] PM: Registered nosave memory: 00000000c9fa1000 - 00000000c9fa6000
[    0.000000] PM: Registered nosave memory: 00000000c9fc5000 - 00000000c9fc7000
[    0.000000] PM: Registered nosave memory: 00000000c9fdc000 - 00000000c9fdd000
[    0.000000] PM: Registered nosave memory: 00000000c9fef000 - 00000000ca016000
[    0.000000] PM: Registered nosave memory: 00000000ca02a000 - 00000000ca02b000
[    0.000000] PM: Registered nosave memory: 00000000ca02c000 - 00000000ca02e000
[    0.000000] PM: Registered nosave memory: 00000000ca02f000 - 00000000ca034000
[    0.000000] PM: Registered nosave memory: 00000000ca04c000 - 00000000ca611000
[    0.000000] PM: Registered nosave memory: 00000000ca611000 - 00000000ca891000
[    0.000000] PM: Registered nosave memory: 00000000ca891000 - 00000000ca896000
[    0.000000] PM: Registered nosave memory: 00000000ca897000 - 00000000ca8da000
[    0.000000] PM: Registered nosave memory: 00000000caced000 - 00000000caff4000
[    0.000000] PM: Registered nosave memory: 00000000cb000000 - 00000000cbc00000
[    0.000000] PM: Registered nosave memory: 00000000cbc00000 - 00000000cfe00000
[    0.000000] PM: Registered nosave memory: 00000000cfe00000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000
[    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] e820: [mem 0xcfe00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8802aee00000 s85056 r8192 d21440 u524288
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2551613
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-25-generic root=UUID=5de0bfd2-f4fa-4eb2-967b-ae0eb530d798 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 9926120k/11257856k available (7008k kernel code, 889340k absent, 442396k reserved, 6234k data, 996k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2394.534 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4789.06 BogoMIPS (lpj=9578136)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000025] init_memory_mapping: [mem 0xcbc00000-0xcfdfffff]
[    0.000028]  [mem 0xcbc00000-0xcfdfffff] page 2M
[    0.050796] Security Framework initialized
[    0.050805] AppArmor: AppArmor initialized
[    0.050807] Yama: becoming mindful.
[    0.052010] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.057364] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.059754] Mount-cache hash table entries: 256
[    0.059964] Initializing cgroup subsys cpuacct
[    0.059967] Initializing cgroup subsys memory
[    0.059974] Initializing cgroup subsys devices
[    0.059975] Initializing cgroup subsys freezer
[    0.059977] Initializing cgroup subsys blkio
[    0.059979] Initializing cgroup subsys perf_event
[    0.059981] Initializing cgroup subsys hugetlb
[    0.060009] CPU: Physical Processor ID: 0
[    0.060011] CPU: Processor Core ID: 0
[    0.060016] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.060016] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.060512] mce: CPU supports 7 MCE banks
[    0.060526] CPU0: Thermal monitoring enabled (TM1)
[    0.060535] process: using mwait in idle threads
[    0.060539] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.060539] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.060539] tlb_flushall_shift: 1
[    0.060741] Freeing SMP alternatives: 24k freed
[    0.063415] ACPI: Core revision 20121018
[    0.087863] ftrace: allocating 26695 entries in 105 pages
[    0.104000] dmar: Host address width 36
[    0.104003] dmar: DRHD base: 0x000000fed90000 flags: 0x0
[    0.104020] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c0000020e60262 ecap f0101a
[    0.104021] dmar: DRHD base: 0x000000fed91000 flags: 0x1
[    0.104029] dmar: IOMMU 1: reg_base_addr fed91000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.104030] dmar: RMRR base: 0x000000ca331000 end: 0x000000ca34dfff
[    0.104032] dmar: RMRR base: 0x000000cbc00000 end: 0x000000cfdfffff
[    0.104106] IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.104108] HPET id 0 under DRHD base 0xfed91000
[    0.104289] Enabled IRQ remapping in x2apic mode
[    0.104291] Enabling x2apic
[    0.104292] Enabled x2apic
[    0.104301] Switched APIC routing to cluster x2apic.
[    0.104766] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.144392] smpboot: CPU0: Intel(R) Core(TM) i7-3517U CPU @ 1.90GHz (fam: 06, model: 3a, stepping: 09)
[    0.144403] TSC deadline timer enabled
[    0.144406] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, Intel PMU driver.
[    0.144413] ... version:                3
[    0.144415] ... bit width:              48
[    0.144416] ... generic registers:      4
[    0.144417] ... value mask:             0000ffffffffffff
[    0.144418] ... max period:             000000007fffffff
[    0.144419] ... fixed-purpose events:   3
[    0.144420] ... event mask:             000000070000000f
[    0.159222] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.145643] smpboot: Booting Node   0, Processors  #1 #2 #3 OK
[    0.186607] Brought up 4 CPUs
[    0.186612] smpboot: Total of 4 processors activated (19156.27 BogoMIPS)
[    0.191517] devtmpfs: initialized
[    0.192835] EVM: security.selinux
[    0.192837] EVM: security.SMACK64
[    0.192838] EVM: security.capability
[    0.192890] PM: Registering ACPI NVS region [mem 0xc9729000-0xc9d29fff] (6295552 bytes)
[    0.192990] PM: Registering ACPI NVS region [mem 0xca611000-0xca890fff] (2621440 bytes)
[    0.193031] PM: Registering ACPI NVS region [mem 0xca897000-0xca8d9fff] (274432 bytes)
[    0.193904] regulator-dummy: no parameters
[    0.193954] NET: Registered protocol family 16
[    0.194122] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.194124] ACPI: bus type pci registered
[    0.194185] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.194188] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.216697] PCI: Using configuration type 1 for base access
[    0.217690] bio: create slab <bio-0> at 0
[    0.217785] ACPI: Added _OSI(Module Device)
[    0.217787] ACPI: Added _OSI(Processor Device)
[    0.217789] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.217790] ACPI: Added _OSI(Processor Aggregator Device)
[    0.220839] ACPI: EC: EC description table is found, configuring boot EC
[    0.224017] ACPI: Executed 1 blocks of module-level executable AML code
[    0.339248] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.339914] ACPI: SSDT 00000000ca5be018 00853 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.340679] ACPI: Dynamic OEM Table Load:
[    0.340681] ACPI: SSDT           (null) 00853 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.341011] ACPI: SSDT 00000000ca5bfa98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.341808] ACPI: Dynamic OEM Table Load:
[    0.341810] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.341965] ACPI: SSDT 00000000ca5c0c18 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.342721] ACPI: Dynamic OEM Table Load:
[    0.342723] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.343560] ACPI: Interpreter enabled
[    0.343565] ACPI: (supports S0 S3 S4 S5)
[    0.343590] ACPI: Using IOAPIC for interrupt routing
[    0.453702] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.453901] ACPI: No dock devices found.
[    0.453906] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.454193] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.454196] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.455066] PCI host bridge to bus 0000:00
[    0.455070] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.455073] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.455075] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.455077] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.455079] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.455081] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.455083] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.455085] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.455087] pci_bus 0000:00: root bus resource [mem 0xcfe00000-0xfeafffff]
[    0.455097] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[    0.455144] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.455183] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.455207] pci 0000:00:02.0: [8086:0166] type 00 class 0x030000
[    0.455221] pci 0000:00:02.0: reg 10: [mem 0xf7400000-0xf77fffff 64bit]
[    0.455229] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.455235] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    0.455278] pci 0000:00:04.0: [8086:0153] type 00 class 0x118000
[    0.455291] pci 0000:00:04.0: reg 10: [mem 0xfed98000-0xfed9ffff 64bit]
[    0.455366] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.455393] pci 0000:00:14.0: reg 10: [mem 0xf7900000-0xf790ffff 64bit]
[    0.455473] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.455501] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.455527] pci 0000:00:16.0: reg 10: [mem 0xf7922000-0xf792200f 64bit]
[    0.455613] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.455657] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.455681] pci 0000:00:1a.0: reg 10: [mem 0xf7920000-0xf79203ff]
[    0.455783] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.455815] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.455833] pci 0000:00:1b.0: reg 10: [mem 0xf7918000-0xf791bfff 64bit]
[    0.455910] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.455939] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.456070] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.456110] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[    0.456240] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.456295] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.456319] pci 0000:00:1d.0: reg 10: [mem 0xf791f000-0xf791f3ff]
[    0.456421] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.456449] pci 0000:00:1f.0: [8086:1e59] type 00 class 0x060100
[    0.456588] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[    0.456610] pci 0000:00:1f.2: reg 10: [io  0xf0b0-0xf0b7]
[    0.456620] pci 0000:00:1f.2: reg 14: [io  0xf0a0-0xf0a3]
[    0.456631] pci 0000:00:1f.2: reg 18: [io  0xf090-0xf097]
[    0.456641] pci 0000:00:1f.2: reg 1c: [io  0xf080-0xf083]
[    0.456652] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
[    0.456663] pci 0000:00:1f.2: reg 24: [mem 0xf791e000-0xf791e7ff]
[    0.456716] pci 0000:00:1f.2: PME# supported from D3hot
[    0.456737] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.456756] pci 0000:00:1f.3: reg 10: [mem 0xf791d000-0xf791d0ff 64bit]
[    0.456780] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    0.456823] pci 0000:00:1f.6: [8086:1e24] type 00 class 0x118000
[    0.456848] pci 0000:00:1f.6: reg 10: [mem 0xf791c000-0xf791cfff 64bit]
[    0.456965] pci 0000:01:00.0: [10de:1140] type 00 class 0x030200
[    0.456980] pci 0000:01:00.0: reg 10: [mem 0xf6000000-0xf6ffffff]
[    0.456996] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.457012] pci 0000:01:00.0: reg 1c: [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.457023] pci 0000:01:00.0: reg 24: [io  0xe000-0xe07f]
[    0.457033] pci 0000:01:00.0: reg 30: [mem 0xf7000000-0xf707ffff pref]
[    0.467081] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.467084] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.467087] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.467092] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.467168] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.467416] pci 0000:03:00.0: [8086:088e] type 00 class 0x028000
[    0.467599] pci 0000:03:00.0: reg 10: [mem 0xf7800000-0xf7801fff 64bit]
[    0.468332] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.479179] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.479189] pci 0000:00:1c.1:   bridge window [mem 0xf7800000-0xf78fffff]
[    0.479229] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.479301] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.479362] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.479502]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.479753]  pci0000:00: ACPI _OSC control (0x18) granted
[    0.480674] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12)
[    0.480724] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 12)
[    0.480769] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 12)
[    0.480813] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 12)
[    0.480860] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.480907] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.480957] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 12)
[    0.481002] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 10 12)
[    0.481101] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.481105] vgaarb: loaded
[    0.481106] vgaarb: bridge control possible 0000:00:02.0
[    0.481279] SCSI subsystem initialized
[    0.481281] ACPI: bus type scsi registered
[    0.481323] libata version 3.00 loaded.
[    0.481340] ACPI: bus type usb registered
[    0.481359] usbcore: registered new interface driver usbfs
[    0.481368] usbcore: registered new interface driver hub
[    0.481393] usbcore: registered new device driver usb
[    0.481480] PCI: Using ACPI for IRQ routing
[    0.483192] PCI: pci_cache_line_size set to 64 bytes
[    0.483202] pci 0000:00:04.0: no compatible bridge window for [mem 0xfed98000-0xfed9ffff 64bit]
[    0.483272] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.483274] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.483276] e820: reserve RAM buffer [mem 0xc9729000-0xcbffffff]
[    0.483284] e820: reserve RAM buffer [mem 0xc9d44000-0xcbffffff]
[    0.483292] e820: reserve RAM buffer [mem 0xc9d4c000-0xcbffffff]
[    0.483299] e820: reserve RAM buffer [mem 0xc9ee6000-0xcbffffff]
[    0.483307] e820: reserve RAM buffer [mem 0xc9f34000-0xcbffffff]
[    0.483314] e820: reserve RAM buffer [mem 0xc9f3d000-0xcbffffff]
[    0.483320] e820: reserve RAM buffer [mem 0xc9f5e000-0xcbffffff]
[    0.483327] e820: reserve RAM buffer [mem 0xc9f77000-0xcbffffff]
[    0.483334] e820: reserve RAM buffer [mem 0xc9f85000-0xcbffffff]
[    0.483340] e820: reserve RAM buffer [mem 0xc9f95000-0xcbffffff]
[    0.483346] e820: reserve RAM buffer [mem 0xc9fa1000-0xcbffffff]
[    0.483352] e820: reserve RAM buffer [mem 0xc9fc5000-0xcbffffff]
[    0.483357] e820: reserve RAM buffer [mem 0xc9fdc000-0xcbffffff]
[    0.483362] e820: reserve RAM buffer [mem 0xc9fef000-0xcbffffff]
[    0.483367] e820: reserve RAM buffer [mem 0xca02a000-0xcbffffff]
[    0.483372] e820: reserve RAM buffer [mem 0xca02c000-0xcbffffff]
[    0.483376] e820: reserve RAM buffer [mem 0xca02f000-0xcbffffff]
[    0.483379] e820: reserve RAM buffer [mem 0xca04c000-0xcbffffff]
[    0.483383] e820: reserve RAM buffer [mem 0xca897000-0xcbffffff]
[    0.483386] e820: reserve RAM buffer [mem 0xcaced000-0xcbffffff]
[    0.483388] e820: reserve RAM buffer [mem 0xcb000000-0xcbffffff]
[    0.483390] e820: reserve RAM buffer [mem 0x2af200000-0x2afffffff]
[    0.483471] NetLabel: Initializing
[    0.483473] NetLabel:  domain hash size = 128
[    0.483474] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.483483] NetLabel:  unlabeled traffic allowed by default
[    0.483538] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.483544] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.485553] Switching to clocksource hpet
[    0.490854] AppArmor: AppArmor Filesystem Enabled
[    0.490879] pnp: PnP ACPI init
[    0.490892] ACPI: bus type pnp registered
[    0.490985] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.490989] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.541594] pnp 00:01: [dma 4]
[    0.541612] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.541635] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.541746] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.541789] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.541792] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.541794] system 00:04: [io  0xffff] has been reserved
[    0.541796] system 00:04: [io  0xffff] has been reserved
[    0.541799] system 00:04: [io  0x0400-0x0453] has been reserved
[    0.541801] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.541803] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.541805] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.541808] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.541845] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.541894] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.541898] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.541949] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    0.541952] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.541979] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.542047] pnp 00:09: Plug and Play ACPI device, IDs ETD0105 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.542091] pnp 00:0a: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.542331] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.542334] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.542336] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.542338] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.542341] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.542344] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.542346] system 00:0b: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.542349] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.542351] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    0.542354] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.542356] system 00:0b: [mem 0xcfe00000-0xcfe00fff] has been reserved
[    0.542359] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.542454] system 00:0c: [mem 0xcfe00000-0xcfe00fff] has been reserved
[    0.542458] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.542628] system 00:0d: [mem 0x20000000-0x201fffff] has been reserved
[    0.542631] system 00:0d: [mem 0x40004000-0x40004fff] has been reserved
[    0.542633] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.542685] pnp: PnP ACPI: found 14 devices
[    0.542686] ACPI: ACPI bus type pnp unregistered
[    0.548925] pci 0000:00:04.0: BAR 0: assigned [mem 0xcfe08000-0xcfe0ffff 64bit]
[    0.548933] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.548936] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.548939] pci 0000:00:01.0:   bridge window [mem 0xf6000000-0xf70fffff]
[    0.548943] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.548947] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.548962] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.548968] pci 0000:00:1c.1:   bridge window [mem 0xf7800000-0xf78fffff]
[    0.549009] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.549011] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.549013] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.549016] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.549018] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.549020] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.549022] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.549024] pci_bus 0000:00: resource 11 [mem 0xcfe00000-0xfeafffff]
[    0.549026] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.549028] pci_bus 0000:01: resource 1 [mem 0xf6000000-0xf70fffff]
[    0.549031] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.549033] pci_bus 0000:03: resource 1 [mem 0xf7800000-0xf78fffff]
[    0.549064] NET: Registered protocol family 2
[    0.549322] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.549713] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.549853] TCP: Hash tables configured (established 131072 bind 65536)
[    0.549872] TCP: reno registered
[    0.549894] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.549953] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.550045] NET: Registered protocol family 1
[    0.550058] pci 0000:00:02.0: Boot video device
[    0.589484] PCI: CLS 64 bytes, default 64
[    0.589528] Trying to unpack rootfs image as initramfs...
[    0.898311] Freeing initrd memory: 15788k freed
[    0.900554] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.900559] software IO TLB [mem 0xba765000-0xbe765000] (64MB) mapped at [ffff8800ba765000-ffff8800be764fff]
[    0.900998] Initialise module verification
[    0.901039] audit: initializing netlink socket (disabled)
[    0.901054] type=2000 audit(1371616535.892:1): initialized
[    0.935792] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.937400] VFS: Disk quotas dquot_6.5.2
[    0.937441] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.937908] fuse init (API version 7.20)
[    0.937986] msgmni has been set to 19770
[    0.938389] Key type asymmetric registered
[    0.938391] Asymmetric key parser 'x509' registered
[    0.938426] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.938453] io scheduler noop registered
[    0.938456] io scheduler deadline registered (default)
[    0.938462] io scheduler cfq registered
[    0.938571] pcieport 0000:00:01.0: irq 42 for MSI/MSI-X
[    0.938714] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.938727] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.938783] efifb: probing for efifb
[    0.939938] efifb: framebuffer at 0xd0000000, mapped to 0xffffc9000ad00000, using 3072k, total 3072k
[    0.939939] efifb: mode is 1024x768x32, linelength=4096, pages=1
[    0.939940] efifb: scrolling: redraw
[    0.939943] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.942023] Console: switching to colour frame buffer device 128x48
[    0.943988] fb0: EFI VGA frame buffer device
[    0.943995] intel_idle: MWAIT substates: 0x21120
[    0.943996] intel_idle: v0.4 model 0x3A
[    0.943997] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.944210] ACPI: AC Adapter [AC0] (off-line)
[    0.944327] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.957032] ACPI: Lid Switch [LID]
[    0.957069] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.957073] ACPI: Power Button [PWRB]
[    0.957102] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.957105] ACPI: Sleep Button [SLPB]
[    0.957197] ACPI: Requesting acpi_cpufreq
[    1.062835] thermal LNXTHERM:00: registered as thermal_zone0
[    1.062838] ACPI: Thermal Zone [THRM] (40 C)
[    1.062868] GHES: HEST is not enabled!
[    1.062943] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.064514] Linux agpgart interface v0.103
[    1.065863] brd: module loaded
[    1.066572] loop: module loaded
[    1.066868] libphy: Fixed MDIO Bus: probed
[    1.066923] tun: Universal TUN/TAP device driver, 1.6
[    1.066924] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.066969] PPP generic driver version 2.4.2
[    1.067024] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.067026] ehci-pci: EHCI PCI platform driver
[    1.067081] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    1.067086] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.067092] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.067110] ehci-pci 0000:00:1a.0: debug port 2
[    1.071015] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.071033] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7920000
[    1.080718] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.080738] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.080740] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.080742] usb usb1: Product: EHCI Host Controller
[    1.080744] usb usb1: Manufacturer: Linux 3.8.0-25-generic ehci_hcd
[    1.080746] usb usb1: SerialNumber: 0000:00:1a.0
[    1.080873] hub 1-0:1.0: USB hub found
[    1.080877] hub 1-0:1.0: 2 ports detected
[    1.080973] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    1.080977] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.080982] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.080996] ehci-pci 0000:00:1d.0: debug port 2
[    1.084880] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.084897] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf791f000
[    1.088956] ACPI: Battery Slot [BAT0] (battery present)
[    1.096695] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.096709] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.096711] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.096713] usb usb2: Product: EHCI Host Controller
[    1.096715] usb usb2: Manufacturer: Linux 3.8.0-25-generic ehci_hcd
[    1.096717] usb usb2: SerialNumber: 0000:00:1d.0
[    1.096804] hub 2-0:1.0: USB hub found
[    1.096809] hub 2-0:1.0: 2 ports detected
[    1.096870] ehci-platform: EHCI generic platform driver
[    1.096879] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.096891] uhci_hcd: USB Universal Host Controller Interface driver
[    1.096953] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.096957] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.096962] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.097055] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.097105] xhci_hcd 0000:00:14.0: irq 43 for MSI/MSI-X
[    1.097153] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.097155] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.097157] usb usb3: Product: xHCI Host Controller
[    1.097159] usb usb3: Manufacturer: Linux 3.8.0-25-generic xhci_hcd
[    1.097161] usb usb3: SerialNumber: 0000:00:14.0
[    1.097221] xHCI xhci_add_endpoint called for root hub
[    1.097223] xHCI xhci_check_bandwidth called for root hub
[    1.097240] hub 3-0:1.0: USB hub found
[    1.097248] hub 3-0:1.0: 4 ports detected
[    1.097319] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.097322] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.097342] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.097344] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.097346] usb usb4: Product: xHCI Host Controller
[    1.097348] usb usb4: Manufacturer: Linux 3.8.0-25-generic xhci_hcd
[    1.097350] usb usb4: SerialNumber: 0000:00:14.0
[    1.097404] xHCI xhci_add_endpoint called for root hub
[    1.097405] xHCI xhci_check_bandwidth called for root hub
[    1.097422] hub 4-0:1.0: USB hub found
[    1.097428] hub 4-0:1.0: 4 ports detected
[    1.097605] i8042: PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.099263] i8042: Detected active multiplexing controller, rev 1.1
[    1.100251] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.100256] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.100278] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.100294] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.100310] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.100410] mousedev: PS/2 mouse device common for all mice
[    1.100567] rtc_cmos 00:05: RTC can wake from S4
[    1.100709] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.100740] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.100821] device-mapper: uevent: version 1.0.3
[    1.100879] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.100958] cpuidle: using governor ladder
[    1.101059] cpuidle: using governor menu
[    1.101063] ledtrig-cpu: registered to indicate activity on CPUs
[    1.101065] EFI Variables Facility v0.08 2004-May-17
[    1.104297] ashmem: initialized
[    1.104431] TCP: cubic registered
[    1.104519] NET: Registered protocol family 10
[    1.104693] NET: Registered protocol family 17
[    1.104704] Key type dns_resolver registered
[    1.105075] Loading module verification certificates
[    1.106118] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: dbae232d36ad7257df58e2fefc4fab11a387ce7c'
[    1.106133] registered taskstats version 1
[    1.108854] Key type trusted registered
[    1.111215] Key type encrypted registered
[    1.113888] rtc_cmos 00:05: setting system clock to 2013-06-19 04:35:36 UTC (1371616536)
[    1.114731] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.114732] EDD information not available.
[    1.115965] Freeing unused kernel memory: 996k freed
[    1.116058] Write protecting the kernel read-only data: 12288k
[    1.118508] Freeing unused kernel memory: 1172k freed
[    1.120798] Freeing unused kernel memory: 1080k freed
[    1.129398] udevd[107]: starting version 175
[    1.143412] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.156100] Disabling lock debugging due to kernel taint
[    1.156689] ahci 0000:00:1f.2: version 3.0
[    1.156764] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.156820] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3 impl SATA mode
[    1.156824] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.156829] ahci 0000:00:1f.2: setting latency timer to 64
[    1.165011] scsi0 : ahci
[    1.165089] scsi1 : ahci
[    1.165142] scsi2 : ahci
[    1.165199] scsi3 : ahci
[    1.165266] scsi4 : ahci
[    1.165330] scsi5 : ahci
[    1.165371] ata1: SATA max UDMA/133 abar m2048@0xf791e000 port 0xf791e100 irq 44
[    1.165375] ata2: SATA max UDMA/133 abar m2048@0xf791e000 port 0xf791e180 irq 44
[    1.165376] ata3: DUMMY
[    1.165378] ata4: DUMMY
[    1.165379] ata5: DUMMY
[    1.165381] ata6: DUMMY
[    1.392285] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.484150] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.484190] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.484499] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.484614] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.484625] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.485202] ata2.00: ATA-9: SanDisk SSD i100 24GB, 11.50.02, max UDMA/133
[    1.485211] ata2.00: 46905264 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    1.485603] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.485718] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.485729] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.485948] ata2.00: configured for UDMA/133
[    1.513837] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.514044] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.514055] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.514997] ata1.00: ATA-8: Hitachi HTS545050A7E380, GG2OA6C0, max UDMA/133
[    1.515006] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.515941] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.516144] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 (SET FEATURES) succeeded
[    1.516155] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.517088] ata1.00: configured for UDMA/133
[    1.517249] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54505 GG2O PQ: 0 ANSI: 5
[    1.517391] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.517395] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.517403] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.517477] sd 0:0:0:0: [sda] Write Protect is off
[    1.517480] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.517513] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.517544] scsi 1:0:0:0: Direct-Access     ATA      SanDisk SSD i100 11.5 PQ: 0 ANSI: 5
[    1.517637] sd 1:0:0:0: [sdb] 46905264 512-byte logical blocks: (24.0 GB/22.3 GiB)
[    1.517663] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.517695] sd 1:0:0:0: [sdb] Write Protect is off
[    1.517697] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.517730] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.520960]  sdb: sdb1 sdb2 sdb3
[    1.521347] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.524412] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.524418] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.524680] hub 1-1:1.0: USB hub found
[    1.524778] hub 1-1:1.0: 6 ports detected
[    1.596124]  sda: sda1
[    1.596641] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.635898] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.768098] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.768108] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.768444] hub 2-1:1.0: USB hub found
[    1.768547] hub 2-1:1.0: 6 ports detected
[    1.831002] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.831004] EXT4-fs (sda1): write access will be enabled during recovery
[    1.839694] usb 1-1.4: new high-speed USB device number 3 using ehci-pci
[    1.895554] tsc: Refined TSC clocksource calibration: 2394.561 MHz
[    1.895564] Switching to clocksource tsc
[    1.932306] usb 1-1.4: New USB device found, idVendor=0bda, idProduct=0139
[    1.932334] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.932337] usb 1-1.4: Product: USB2.0-CRW
[    1.932339] usb 1-1.4: Manufacturer: Generic
[    1.932341] usb 1-1.4: SerialNumber: 20100201396000000
[    2.039399] usb 2-1.5: new high-speed USB device number 3 using ehci-pci
[    2.225489] usb 2-1.5: New USB device found, idVendor=04f2, idProduct=b330
[    2.225498] usb 2-1.5: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    2.225504] usb 2-1.5: Product: USB2.0 HD UVC WebCam
[    2.225508] usb 2-1.5: Manufacturer: Chicony Electronics Co.,Ltd.
[    2.225512] usb 2-1.5: SerialNumber: 200901010001
[    2.299067] usb 2-1.6: new full-speed USB device number 4 using ehci-pci
[    2.395369] usb 2-1.6: New USB device found, idVendor=8087, idProduct=07da
[    2.395381] usb 2-1.6: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.182203] EXT4-fs (sda1): recovery complete
[    3.187753] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.557886] Adding 22389756k swap on /dev/sdb3.  Priority:-1 extents:1 across:22389756k SS
[   15.847845] udevd[409]: starting version 175
[   16.098252] type=1400 audit(1371616551.505:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=660 comm="apparmor_parser"
[   16.098568] type=1400 audit(1371616551.505:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=660 comm="apparmor_parser"
[   16.098721] type=1400 audit(1371616551.505:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=660 comm="apparmor_parser"
[   16.457252] Bluetooth: Core ver 2.16
[   16.457285] NET: Registered protocol family 31
[   16.457287] Bluetooth: HCI device and connection manager initialized
[   16.457293] Bluetooth: HCI socket layer initialized
[   16.457295] Bluetooth: L2CAP socket layer initialized
[   16.457301] Bluetooth: SCO socket layer initialized
[   16.460724] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \GPIS 1 (20121018/utaddress-251)
[   16.460731] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 2 (20121018/utaddress-251)
[   16.460736] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.460740] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   16.460743] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GP01 2 (20121018/utaddress-251)
[   16.460746] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.460747] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   16.460750] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GP01 2 (20121018/utaddress-251)
[   16.460754] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.460755] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   16.465218] lp: driver loaded but no devices found
[   16.469563] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x12
[   16.469829] [drm] Initialized drm 1.1.0 20060810
[   16.473387] cfg80211: Calling CRDA to update world regulatory domain
[   16.475170] usbcore: registered new interface driver btusb
[   16.475401] Linux video capture interface: v2.00
[   16.476913] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   16.482507] mei 0000:00:16.0: setting latency timer to 64
[   16.482570] mei 0000:00:16.0: irq 45 for MSI/MSI-X
[   16.488507] scsi6 : SCSI emulation for RTS5139 USB card reader
[   16.488668] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   16.488793] usbcore: registered new interface driver rts5139
[   16.489340] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   16.489343] Copyright(c) 2003-2012 Intel Corporation
[   16.489480] iwlwifi 0000:03:00.0: irq 46 for MSI/MSI-X
[   16.492314] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   16.493507] wmi: Mapper loaded
[   16.495421] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   16.501638] uvcvideo: Found UVC 1.00 device USB2.0 HD UVC WebCam (04f2:b330)
[   16.513160] input: USB2.0 HD UVC WebCam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input4
[   16.513278] usbcore: registered new interface driver uvcvideo
[   16.513280] USB Video Class driver (1.1.1)
[   16.517410] MXM: GUID detected in BIOS
[   16.517456] ACPI Error: Needed [Buffer/String/Package], found [Integer] ffff88029fc83d80 (20121018/exresop-590)
[   16.517461] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20121018/dswexec-460)
[   16.517466] ACPI Error: Method parse/execution failed [\_SB_.PCI0.GFX0._DSM] (Node ffff8802a009b370), AE_AML_OPERAND_TYPE (20121018/psparse-537)
[   16.517477] failed to evaluate _DSM: 12291
[   16.517558] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.GFX0 handle
[   16.517574] checking generic (d0000000 300000) vs hw (e0000000 10000000)
[   16.517576] checking generic (d0000000 300000) vs hw (f0000000 2000000)
[   16.518447] [drm] Memory usable by graphics device = 2048M
[   16.518452] checking generic (d0000000 300000) vs hw (d0000000 10000000)
[   16.518454] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
[   16.518485] Console: switching to colour dummy device 80x25
[   16.518639] i915 0000:00:02.0: setting latency timer to 64
[   16.558607] asus_wmi: ASUS WMI generic driver loaded
[   16.565734] asus_wmi: Initialization: 0x1asus_wmi: BIOS WMI version: 7.9
[   16.565953] asus_wmi: SFUN value: 0x4a2877<6>[   16.571608] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input5
[   16.586879] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.603336] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[   16.603345] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   16.603346] [drm] Driver supports precise vblank timestamp query.
[   16.603398] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   16.701928] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x12
[   16.703015] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x12
[   16.703300] fbcon: inteldrmfb (fb0) is primary device
[   16.704857] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x12
[   16.706114] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   16.722233] asus_wmi: Backlight controlled by ACPI video driver
[   16.783519] cfg80211: World regulatory domain updated:
[   16.783519] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.783521] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.783522] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.783522] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.783523] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.783523] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.838896] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[   16.841624] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1
[   16.854776] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   16.854777] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   16.854777] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   16.854778] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   16.854779] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   16.854780] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6235 AGN, REV=0xB0
[   16.854827] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   16.874897] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.934601] usb 2-1.6: USB disconnect, device number 4
[   17.015459] psmouse serio4: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[   17.203828] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x361f02)
[   17.216392] psmouse serio4: elantech: Synaptics capabilities query result 0x00, 0x15, 0x0e.
[   17.278554] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input6
[   17.768278] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   18.846422] Console: switching to colour frame buffer device 240x67
[   18.849581] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   18.849583] i915 0000:00:02.0: registered panic notifier
[   18.851139] acpi device:05: registered as cooling_device4
[   18.851167] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[   18.851305] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input7
[   18.862449] init: failsafe main process (972) killed by TERM signal
[   18.863813] acpi device:28: registered as cooling_device5
[   18.866353] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   18.866472] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   18.866887] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   18.867053] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   18.867334] nouveau ![  DEVICE][0000:01:00.0] unknown Fermi chipset
[   18.867360] nouveau E[  DEVICE][0000:01:00.0] unknown chipset, 0x0d7000a2
[   18.867381] nouveau E[     DRM] failed to create 0x80000080, -22
[   18.872514] nouveau: probe of 0000:01:00.0 failed with error -22
[   18.885546] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   18.885615] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   19.130611] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.130613] Bluetooth: BNEP filters: protocol multicast
[   19.130619] Bluetooth: BNEP socket layer initialized
[   19.131218] Bluetooth: RFCOMM TTY layer initialized
[   19.131225] Bluetooth: RFCOMM socket layer initialized
[   19.131227] Bluetooth: RFCOMM ver 1.11
[   19.623750] ppdev: user-space parallel port driver
[   19.661984] init: avahi-cups-reload main process (1038) terminated with status 1
[   19.667482] type=1400 audit(1371616555.077:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1055 comm="apparmor_parser"
[   19.667827] type=1400 audit(1371616555.077:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1055 comm="apparmor_parser"
[   20.679833] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   20.686409] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[   21.085830] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   21.092395] iwlwifi 0000:03:00.0: Radio type=0x2-0x1-0x0
[   21.318651] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.873916] type=1400 audit(1371616557.289:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1136 comm="apparmor_parser"
[   21.873928] type=1400 audit(1371616557.289:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1134 comm="apparmor_parser"
[   21.874188] type=1400 audit(1371616557.289:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=1136 comm="apparmor_parser"
[   21.874201] type=1400 audit(1371616557.289:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1134 comm="apparmor_parser"
[   21.875407] type=1400 audit(1371616557.289:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1137 comm="apparmor_parser"
[   21.875713] type=1400 audit(1371616557.289:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1135 comm="apparmor_parser"
[   21.875941] type=1400 audit(1371616557.289:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1135 comm="apparmor_parser"
[   21.878120] type=1400 audit(1371616557.293:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1137 comm="apparmor_parser"
[   21.878327] type=1400 audit(1371616557.293:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1137 comm="apparmor_parser"
[   21.879513] type=1400 audit(1371616557.293:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1140 comm="apparmor_parser"
[   24.627939] init: plymouth-stop pre-start process (1493) terminated with status 1
[   27.602815] wlan0: authenticate with 74:d0:2b:41:b8:c8
[   27.609567] wlan0: send auth to 74:d0:2b:41:b8:c8 (try 1/3)
[   27.612272] wlan0: authenticated
[   27.613279] wlan0: associate with 74:d0:2b:41:b8:c8 (try 1/3)
[   27.617048] wlan0: RX AssocResp from 74:d0:2b:41:b8:c8 (capab=0x411 status=0 aid=4)
[   27.618918] wlan0: associated
[   27.618944] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   34.029416] CPU2: Package power limit notification (total events = 1)
[   34.029418] CPU3: Package power limit notification (total events = 1)
[   34.029419] CPU1: Package power limit notification (total events = 1)
[   34.029421] CPU0: Package power limit notification (total events = 1)
[   34.040441] CPU0: Package power limit normal
[   34.040446] CPU2: Package power limit normal
[   34.040475] CPU1: Package power limit normal
[   34.040479] CPU3: Package power limit normal
[   70.165933] usb 3-3: new high-speed USB device number 2 using xhci_hcd
[   70.182785] usb 3-3: New USB device found, idVendor=0781, idProduct=5151
[   70.182796] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   70.182810] usb 3-3: Product: Cruzer Micro
[   70.182812] usb 3-3: Manufacturer: SanDisk
[   70.182813] usb 3-3: SerialNumber: 077530168F8364F5
[   70.274508] Initializing USB Mass Storage driver...
[   70.274614] scsi7 : usb-storage 3-3:1.0
[   70.274685] usbcore: registered new interface driver usb-storage
[   70.274687] USB Mass Storage support registered.
[   71.272747] scsi 7:0:0:0: Direct-Access     SanDisk  Cruzer           7.01 PQ: 0 ANSI: 0 CCS
[   71.273551] sd 7:0:0:0: Attached scsi generic sg3 type 0
[   71.273708] sd 7:0:0:0: [sdd] 15794175 512-byte logical blocks: (8.08 GB/7.53 GiB)
[   71.273825] sd 7:0:0:0: [sdd] Write Protect is off
[   71.273827] sd 7:0:0:0: [sdd] Mode Sense: 45 00 00 08
[   71.274007] sd 7:0:0:0: [sdd] No Caching mode page present
[   71.274009] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[   71.275511] sd 7:0:0:0: [sdd] No Caching mode page present
[   71.275514] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[   71.277388]  sdd: sdd1
[   71.278108] sd 7:0:0:0: [sdd] No Caching mode page present
[   71.278110] sd 7:0:0:0: [sdd] Assuming drive cache: write through
[   71.278112] sd 7:0:0:0: [sdd] Attached SCSI removable disk
[   71.700108] systemd-hostnamed[2677]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  399.866040] CPU1: Package power limit notification (total events = 137)
[  399.866042] CPU3: Package power limit notification (total events = 137)
[  399.866044] CPU0: Package power limit notification (total events = 137)
[  399.866047] CPU2: Package power limit notification (total events = 137)
[  399.867810] CPU0: Package power limit normal
[  399.867815] CPU2: Package power limit normal
[  399.867819] CPU1: Package power limit normal
[  399.867823] CPU3: Package power limit normal
[  732.852941] CPU1: Package power limit notification (total events = 154)
[  732.852944] CPU2: Package power limit notification (total events = 154)
[  732.852945] CPU3: Package power limit notification (total events = 154)
[  732.852946] CPU0: Package power limit notification (total events = 154)
[  732.853459] CPU3: Package power limit normal
[  732.853460] CPU2: Package power limit normal
[  732.853461] CPU1: Package power limit normal
[  732.853462] CPU0: Package power limit normal
[ 1106.024302] CPU1: Package power limit notification (total events = 178)
[ 1106.024304] CPU2: Package power limit notification (total events = 178)
[ 1106.024306] CPU3: Package power limit notification (total events = 178)
[ 1106.024308] CPU0: Package power limit notification (total events = 178)
[ 1106.027300] CPU0: Package power limit normal
[ 1106.027301] CPU2: Package power limit normal
[ 1106.027303] CPU1: Package power limit normal
[ 1106.027304] CPU3: Package power limit normal
[ 1419.810222] CPU0: Package power limit notification (total events = 210)
[ 1419.810225] CPU3: Package power limit notification (total events = 210)
[ 1419.810227] CPU1: Package power limit notification (total events = 210)
[ 1419.810228] CPU2: Package power limit notification (total events = 210)
[ 1419.815865] CPU3: Package power limit normal
[ 1419.815869] CPU1: Package power limit normal
[ 1419.815875] CPU2: Package power limit normal
[ 1419.815878] CPU0: Package power limit normal

Step 6:
sudo lshw -C network
[sudo] password for steve: 
  *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6235
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 24
       serial: c4:85:08:36:65:cd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.8.0-25-generic firmware=18.168.6.1 ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:f7800000-f7801fff

Step 7:
iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 74:D0:2B:41:B8:C8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"SMBWMFB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001399a85c15
                    Extra: Last beacon: 44952ms ago
                    IE: Unknown: 0007534D42574D4642
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1ABD191BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DDA90050F204104A0001101044000102103B000103104700105434FDC5A1ABEEA48F498DF497560373102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000852542D41433636551042000C4341494141323030303030311054000800060050F20400011011000852542D4143363655100800022008103C0001031049000600372A000120
                    IE: Unknown: DD090010180203001C0000
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00

Step 8:
lsb_release -d
Description:    Ubuntu 13.04

Step 9:
uname -mr
3.8.0-25-generic x86_64

Step 10:
sudo /etc/init.d/networking restart
```  
Waited a long time with no activity.  Then got a "sorry, we've run into problem" type message. Allowed it to try to file with the forum and had to power down the box. >>

---

### Post by wildmanne39 on 2013-06-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by SMButler on 2013-06-19
I'm new to Ubuntu and didn't follow.  I'm still finding my way around the forum.  Code tags?  Text Box Header?

---

### Post by ahallubuntu on 2013-06-19
~

---

### Post by SMButler on 2013-06-20
Don't know about AP isolation.  Will check when I get home.  Can't get on the internet either.  I can ping (occasionally) my main desktop (a Win7 box).

Latest firmware -- both I and the router checked.  I will post a query there since all hardware involved is Asus.

WPA2-PKS  AES.

My research this morning found a thread (how do I reference another thread) that 802.11n drivers don't always work correctly in 13.04.  Perhaps I'm running into that issue?  If so, how do I disable the 'n' option in Ubuntu?

---

### Post by SMButler on 2013-07-01
Found this command that solved my issue:  echo "iwlwifi 11n_disable=1" > /etc/modprobe.d/iwlagn.conf

Then reboot the box.

---

