---
title: "HP DV4 Wifi Button"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by PaperorPlastic on 2010-02-18
Good evening all. I have a HP dv4 1435dx that I just installed 9.10 x64 on. The wifi button is amber and will not allow me to turn on the wifi network card. With that being said here is the following output of various commands that show me atleast the NIC is seen and has drivers loaded for it. Any idea on how to "enable" this button so I can use the Wifi?

 lspci | grep -i net
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


lsmod:
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_intelhdmi    14880  1 
snd_hda_codec_idt      72976  1 
snd_hda_intel          31880  2 
snd_hda_codec          87584  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
iptable_filter          3872  0 
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
b43                   136552  0 
ip_tables              21200  1 iptable_filter
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
uvcvideo               65260  0 
x_tables               25832  1 ip_tables
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              210104  1 b43
snd                    77096  17 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 13088  0 
cfg80211              109144  2 b43,mac80211
sdhci_pci               8928  0 
psmouse                57124  0 
serio_raw               6596  0 
jmb38x_ms              11300  0 
memstick               12528  1 jmb38x_ms
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
sdhci                  20484  1 sdhci_pci
lirc_ene0100            9444  0 
lirc_dev               13928  1 lirc_ene0100
hp_accel               12480  0 
lis3lv02d               9312  1 hp_accel
input_polldev           4720  1 lis3lv02d
led_class               5256  3 b43,sdhci,hp_accel
lp                     11908  0 
parport                40528  2 ppdev,lp
fbcon                  41344  72 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
r8169                  38884  0 
mii                     6368  1 r8169
ssb                    40944  1 b43
i915                  246984  3 
drm                   193856  3 i915
i2c_algo_bit            7076  1 i915
intel_agp              32816  2 i915
video                  23612  1 i915
output                  3680  1 video

Any help would be warmly received.

Thank you in advance!

---

### Post by northd_tech on 2010-02-18
> **PaperorPlastic said:**
> 
 **lspci | grep -i net**
02:00.0 Network controller: **Broadcom Corporation BCM4312** 802.11b/g (rev 01)
03:00.0 Ethernet controller: [COLOR=Red]Realtek[/COLOR] Semiconductor Co., Ltd. [COLOR=Red]RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)[/COLOR]

**lsmod:**
Module                  Size  Used by

**b43**                   136552  0 
mac80211              210104  1 **b43**
cfg80211              109144  2 **b43**,mac80211
[COLOR=Red]
r8169                  38884  0 
mii                     6368  1 r8169[/COLOR]
ssb                    40944  1 **b43**


You have a Broadcom 4312 wireless interface, and it looks like you have got the Broadcom "b43" modules (and related "80211" modules) loaded.  

The "ssb" module is related too (but I've got a Broadcom 4321AG and use the Broadcom "STA" driver instead of the "b43" stuff, so I'm not 100% certain what a working one of those looks like).

If you're interested, the stuff I colored [COLOR=Red]red[/COLOR] above is for your Realtek cabled ethernet connection and its network modules.

There are several threads linked that I recently bumped about that Broadcom 4312 Wifi:

[http://ubuntuforums.org/showthread.php?t=1410259](http://ubuntuforums.org/showthread.php?t=1410259)

[http://ubuntuforums.org/showthread.php?t=1406947](http://ubuntuforums.org/showthread.php?t=1406947)

It would also help if you post the results of the following terminal commands before you change any settings:

```
ifconfig

iwconfig

uname -a
```

---

### Post by PaperorPlastic on 2010-02-19
ifconfig:
paper@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:5a:a6:bf:85  
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:5aff:fea6:bf85/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:427811 (427.8 KB)  TX bytes:67007 (67.0 KB)
          Interrupt:30 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.




Linux ubuntu 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

---

### Post by PaperorPlastic on 2010-02-19
Woo I got it fixed. Thanks so much for your help!

Post number #7 is how I fixed it.
[http://ubuntuforums.org/showthread.php?t=1317801](http://ubuntuforums.org/showthread.php?t=1317801)

Thank you so much for your help.

---

