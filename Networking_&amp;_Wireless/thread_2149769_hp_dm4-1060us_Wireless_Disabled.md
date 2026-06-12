---
title: "hp dm4-1060us Wireless Disabled"
date: 2013-05-29
forum: Networking &amp; Wireless
---

### Post by checkthamethod on 2013-05-29
I  just installed Linux 13.04 via installation cd because my windows bootloader was acting up. Now that it's installed my wifi is not connecting. It shows that I have a Intel Centrino Wireless N + WiMax 6150 on the notification bar in the top beside the sound control but everytime i go to system settings > network to turn it on it just jumps back to off. Any help would do!

---

### Post by Hadaka on 2013-05-30
Hi, try this...
[http://ubuntuforums.org/showthread.php?t=2010968](http://ubuntuforums.org/showthread.php?t=2010968)

---

### Post by checkthamethod on 2013-05-31
I have tried all that stuff on that forum and it did not work.

---

### Post by Hadaka on 2013-05-31
Not quite sure what you mean about "turning it on"
and it jumps back off... Let's take a look at some things
and see what we find.. please do.
```
lspci -nnk | grep -iA3 net
rfkill list all
lsmod
ifconfig
```
post the output
thanks.

---

### Post by checkthamethod on 2013-06-01
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0886] (rev 67)
	Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1315]
	Kernel driver in use: iwlwifi
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:1793]
	Kernel driver in use: r8169
05:00.0 USB controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
bryan@bryan-HP-Pavilion-dm4-Notebook-PC:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: i2400m-usb:1-1.4:1.0: WiMAX
	Soft blocked: yes
	Hard blocked: no
bryan@bryan-HP-Pavilion-dm4-Notebook-PC:~$ lsmod
Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_idt      70256  1 
ipheth                 13448  0 
uvcvideo               80847  0 
i2400m_usb             36375  0 
videobuf2_vmalloc      13056  1 uvcvideo
i2400m                107578  1 i2400m_usb
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
wimax                  34760  1 i2400m
videodev              129260  2 uvcvideo,videobuf2_core
joydev                 17377  0 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
coretemp               13355  0 
arc4                   12615  2 
kvm                   443165  0 
snd_hda_intel          39619  5 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
ghash_clmulni_intel    13259  0 
snd_hwdep              13602  1 snd_hda_codec
aesni_intel            55399  0 
iwldvm                241834  0 
snd_pcm                97451  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
mac80211              606457  1 iwldvm
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  600351  5 
snd_rawmidi            30180  1 snd_seq_midi
wmi                    19070  1 hp_wmi
drm_kms_helper         49394  1 i915
video                  19390  1 i915
iwlwifi               173477  1 iwldvm
drm                   286313  6 i915,drm_kms_helper
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
mei                    41158  0 
hp_accel               26012  0 
cfg80211              510937  3 iwlwifi,mac80211,iwldvm
lis3lv02d              20111  1 hp_accel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
input_polldev          13896  1 lis3lv02d
mac_hid                13205  0 
i2c_algo_bit           13413  1 i915
snd                    68876  19 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
rtsx_pci_ms            13011  0 
memstick               16554  1 rtsx_pci_ms
psmouse                95870  0 
soundcore              12680  1 snd
lpc_ich                17061  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
microcode              22881  0 
serio_raw              13215  0 
rtsx_pci_sdmmc         17475  0 
ahci                   25731  2 
libahci                31364  1 ahci
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  67446  0 
bryan@bryan-HP-Pavilion-dm4-Notebook-PC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 10:1f:74:6a:fc:5b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth1      Link encap:Ethernet  HWaddr 9a:fe:94:12:1f:37  
          inet addr:172.20.10.2  Bcast:172.20.10.15  Mask:255.255.255.240
          inet6 addr: fe80::98fe:94ff:fe12:1f37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:549175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:769196185 (769.1 MB)  TX bytes:26736557 (26.7 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:101875 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7207906 (7.2 MB)  TX bytes:7207906 (7.2 MB)


wmx0      Link encap:Ethernet  HWaddr 64:d4:da:6d:c5:a1  
          UP NOARP  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:20 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

