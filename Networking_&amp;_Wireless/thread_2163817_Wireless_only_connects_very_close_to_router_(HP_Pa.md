---
title: "Wireless only connects very close to router (HP Pavilion g6)"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by Quail2 on 2013-07-19
I recently installed Ubuntu 13.04 on my new laptop, and the wireless connection seems a bit dodgy. If I sit very close to the router, it connects to the network fine, the internet is okay, etc. But if I move away (say about 8 metres down the hall) it becomes very slow and disconnects. If I try to connect again, it asks repeatedly for the password and never connects. I was wondering if this could be a compatibility issue, and if there is anything I could do that might fix it.

---

### Post by praseodym on 2013-07-19
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by TheFu on 2013-07-19
8 meters seems like a long way to me, but I guess the type of materials the signal is going through matters most. Going though concrete is hard for wifi.

Did this work well under Ubuntu 12.04, you know, the LTS release, from the same distance?
The specific router and the specific wifi chips can matter. What are those?
Is the antenna pointed correctly for the place you want coverage?
2.4 Ghz is getting more and more devices. Are there other devices interfering? Microwaves, bluetooth, other routers, cordless phones, remote controls, ... lots-o-things.

Perhaps if you tested using scientific methods - measured distances, number of walls, and captured the S/N for each point, a pattern would be displayed?  There are tools that help build a wifi reception map. This can be very useful when trying to determine issues of this type.

I do wifi deployments (1200+ locations) and almost all of the nearby issues are due to concrete walls or interference from other devices.  Expecting a $20 home wifi router to provide great connections more than 5 meters away is asking a lot. If there are walls or metal bars involved, it becomes harder and harder for non-commercial equipment.  There is good news. For $90, you can get a great wifi AP from Ubiquity that can cover much larger areas fairly well.

Anyway, facts are what we need to help.  Hardware used, wall materials, count and distances, drivers, any other interference items, plus how these impact the specific locations you'd like coverage.

---

### Post by Quail2 on 2013-07-20
Hi, sorry for the late reply. I was travelling today so only just have access to the internet again.
> **praseodym said:**
> Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

> 01:00.0 Network controller [0280]: Ralink corp. Device [1814:539b]
    Subsystem: Hewlett-Packard Company Device [103c:18ed]
    Kernel driver in use: rt2800pci
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:183f]
    Kernel driver in use: r8169
quail@quail-laptop:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 1bcf:2c1e Sunplus Innovation Technology Inc. 
quail@quail-laptop:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
udf                    89374  1 
crc_itu_t              12707  1 udf
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
joydev                 17377  0 
nls_iso8859_1          12713  1 
hp_accel               26012  0 
lis3lv02d              20111  1 hp_accel
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
input_polldev          13896  1 lis3lv02d
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_idt      70256  1 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
coretemp               13355  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
kvm                   443165  0 
arc4                   12615  2 
snd_rawmidi            30180  1 snd_seq_midi
rt2800pci              18582  0 
rt2800lib              66507  1 rt2800pci
rt2x00pci              14519  1 rt2800pci
rt2x00lib              54869  3 rt2x00pci,rt2800lib,rt2800pci
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
mac80211              606457  3 rt2x00lib,rt2x00pci,rt2800lib
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
hp_wmi                 18048  0 
mac_hid                13205  0 
rtsx_pci_ms            13011  0 
sparse_keymap          13890  1 hp_wmi
memstick               16554  1 rtsx_pci_ms
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
cfg80211              510937  2 mac80211,rt2x00lib
lpc_ich                17061  0 
soundcore              12680  1 snd
mei                    41158  0 
psmouse                95870  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
eeprom_93cx6           13344  1 rt2800pci
microcode              22881  0 
serio_raw              13215  0 
ext2                   72837  1 
crc_ccitt              12707  1 rt2800lib
xts                    12885  1 
gf128mul               14951  1 xts
dm_crypt               22820  2 
usb_storage            57204  0 
rtsx_pci_sdmmc         17475  0 
wmi                    19070  1 hp_wmi
i915                  600396  3 
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
video                  19390  1 i915
ahci                   25731  4 
i2c_algo_bit           13413  1 i915
libahci                31364  1 ahci
drm_kms_helper         49394  1 i915
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  67446  0 
drm                   286028  4 i915,drm_kms_helper
quail@quail-laptop:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BTHomeHub2-7JFM"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:26:44:EC:7D:7B   
          Bit Rate=26 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:225  Invalid misc:533   Missed beacon:0

quail@quail-laptop:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



---

### Post by Quail2 on 2013-07-20
> **TheFu said:**
> 8 meters seems like a long way to me, but I guess the type of materials the signal is going through matters most. Going though concrete is hard for wifi.

Did this work well under Ubuntu 12.04, you know, the LTS release, from the same distance?
The specific router and the specific wifi chips can matter. What are those?
Is the antenna pointed correctly for the place you want coverage?
2.4 Ghz is getting more and more devices. Are there other devices interfering? Microwaves, bluetooth, other routers, cordless phones, remote controls, ... lots-o-things.

Perhaps if you tested using scientific methods - measured distances, number of walls, and captured the S/N for each point, a pattern would be displayed?  There are tools that help build a wifi reception map. This can be very useful when trying to determine issues of this type.

I do wifi deployments (1200+ locations) and almost all of the nearby issues are due to concrete walls or interference from other devices.  Expecting a $20 home wifi router to provide great connections more than 5 meters away is asking a lot. If there are walls or metal bars involved, it becomes harder and harder for non-commercial equipment.  There is good news. For $90, you can get a great wifi AP from Ubiquity that can cover much larger areas fairly well.

Anyway, facts are what we need to help.  Hardware used, wall materials, count and distances, drivers, any other interference items, plus how these impact the specific locations you'd like coverage.
The routers I've been having trouble connecting to are BT and Sky routers. The Sky one is at my home, where I can only connect to the network if I'm downstairs next to it (although my partner's desktop will connect two floors up). Last night I was at my parents' house, which is a bungalow and I couldn't connect at the opposite end of the bungalow. I'm currently in a holiday apartment with a BT router and can only connect when I'm in the same room as it. I wasn't having this problem at home before we changed our internet from O2, so it could well be a problem with the router we were sent. I had a similar problem with my previous HP laptop running Ubuntu 12.04, but not quite to the same extent. My old laptop, the manufacturer of which I can't quite remember, which is running Ubuntu 11.10 doesn't have the same problem though. That's what made me wonder if it was something to do with the hardware in the laptop. (Sorry if this sounds a little vague. I'm not the most knowledgeable person about computers and networking.)

---

### Post by praseodym on 2013-07-31
Deactivate the power management:
```

sudo iwconfig wlan0 power off
```

---

