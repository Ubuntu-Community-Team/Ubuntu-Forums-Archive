---
title: "HP Laptop Crashing Verizon Realtek Router..Looks like ARP Poisoning?"
date: 2013-05-08
forum: Networking &amp; Wireless
---

### Post by ncandiano on 2013-05-08
Recently upgraded my HP laptop to 12.10 and 13.04 64bit.  Ever since the first upgrade, I'll get a solid wifi connection for a few minutes, then the router will crash, resulting in DNS errors for every device on the network.  Realizing that my native tether on my android works with no issues, I ran wireshark, and it looks like my computer is ARP poisoning my router.  After a few connections, the router starts sending DNS queries to my laptop.  The following is my system information.

lsmod
Module                  Size  Used by
nvram                  14362  0 
vesafb                 13828  1 
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228619  10 bnep,rfcomm
parport_pc             28152  0 
ppdev                  17073  0 
joydev                 17377  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
arc4                   12615  2 
rt2800pci              18582  0 
snd_hda_codec_idt      70256  1 
rt2800lib              66507  1 rt2800pci
snd_hda_codec_hdmi     36913  1 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
kvm_amd                59717  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
kvm                   443165  1 kvm_amd
rt2x00pci              14519  1 rt2800pci
video                  19390  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
wmi                    19070  1 hp_wmi
snd_timer              29425  2 snd_pcm,snd_seq
fglrx                5201161  168 
rt2x00lib              54869  3 rt2x00pci,rt2800lib,rt2800pci
mac_hid                13205  0 
mac80211              606457  3 rt2x00lib,rt2x00pci,rt2800lib
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
rtsx_pci_ms            13011  0 
cfg80211              510937  2 mac80211,rt2x00lib
memstick               16554  1 rtsx_pci_ms
eeprom_93cx6           13344  1 rt2800pci
amd_iommu_v2           19068  1 fglrx
k10temp                13126  0 
microcode              22881  0 
psmouse                95870  0 
i2c_piix4              13266  0 
serio_raw              13215  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
soundcore              12680  1 snd
crc_ccitt              12707  1 rt2800lib
rtsx_pci_sdmmc         17475  0 
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  67446  0 
ahci                   25731  2 
libahci                31364  1 ahci

Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]

ifconfig
eth0      Link encap:Ethernet  HWaddr 78:e3:b5:63:8f:ad  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:124506 (124.5 KB)  TX bytes:124506 (124.5 KB)

wlan0     Link encap:Ethernet  HWaddr e4:d5:3d:8b:f0:c1  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e6d5:3dff:fe8b:f0c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28643 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33935061 (33.9 MB)  TX bytes:3808409 (3.8 MB)
 iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"DangerZone"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:B8:A0:E8:16   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:63   Missed beacon:0

Also, testing connectivity from my router is showing some really bad ping times,  test results for a couple runs are here:

[TABLE]
[TR="bgcolor: #E0E5F1"]
[TD="class: GRID_NO_RIGHT, width: 25%"]**Status**:[/TD]
[TD="class: GRID_NO_LEFT, width: 75%"][COLOR=#008000]Test Succeeded[/COLOR][/TD]
[/TR]
[TR="bgcolor: #F1F3F9"]
[TD="class: GRID_NO_RIGHT, width: 25%"]**Packets**:[/TD]
[TD="class: GRID_NO_LEFT, width: 75%"]4/4 transmitted, 4/4 received, 0% loss[/TD]
[/TR]
[TR="bgcolor: #E0E5F1"]
[TD="class: GRID_NO_RIGHT, width: 25%"]**Round Trip Time**:[/TD]
[TD="class: GRID_NO_LEFT, width: 75%"]Minimum = 1 ms
Maximum = 833 ms
Average = 615 ms

[TABLE]
[TR="bgcolor: #E0E5F1"]
[TD="class: GRID_NO_RIGHT, width: 25%"]**Status**:[/TD]
[TD="class: GRID_NO_LEFT, width: 75%"][COLOR=#008000]Test Succeeded[/COLOR][/TD]
[/TR]
[TR="bgcolor: #F1F3F9"]
[TD="class: GRID_NO_RIGHT, width: 25%"]**Packets**:[/TD]
[TD="class: GRID_NO_LEFT, width: 75%"]4/4 transmitted, 4/4 received, 0% loss[/TD]
[/TR]
[TR="bgcolor: #E0E5F1"]
[TD="class: GRID_NO_RIGHT, width: 25%"]**Round Trip Time**:[/TD]
[TD="class: GRID_NO_LEFT, width: 75%"]Minimum = 29 ms
Maximum = 665 ms
Average = 441 ms[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

---

