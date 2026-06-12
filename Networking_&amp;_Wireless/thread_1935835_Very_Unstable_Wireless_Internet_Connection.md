---
title: "Very Unstable Wireless Internet Connection"
date: 2012-03-05
forum: Networking &amp; Wireless
---

### Post by dbmeade on 2012-03-05
Hello everyone, I just updated my computer to Ubuntu 11.10  (64-bit), and my wireless internet connection has slowed considerably, from 1.5-2 MB/s to .17mb/s.
[[IMG]http://www.speedtest.net/result/1814220838.png[/IMG]]("http://www.speedtest.net")
I've browsed around and have discovered that this problem doesn't seem to be isolated to just me, but none of the other fixes I've tried thus far have worked. Any help would be greatly appreciated!

Logs

Here are various logs I've seen requested on similar problems.

```
dbmeade@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"UKYResnet5"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:15:D0:06:B4:25   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:14  Invalid misc:52   Missed beacon:0


``````
dbmeade@ubuntu:~$ lsmod
Module                  Size  Used by
rt2800pci              18715  0 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
binfmt_misc            17540  1 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
rt2800lib              54538  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50365  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              462046  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              199630  2 rt2x00lib,mac80211
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13791  0 
fglrx                3101156  174 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_core              53746  0 
eeprom_93cx6           12725  1 rt2800pci
i2c_piix4              13301  0 
k10temp                13166  0 
edac_mce_amd           23709  0 
wmi                    19256  0 
serio_raw              13166  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
usbhid                 47198  0 
hid                    95463  1 usbhid
crc_itu_t              12707  1 firewire_core
floppy                 70365  0 
ahci                   26002  2 
libahci                26861  1 ahci
pata_jmicron           12747  0 
r8169                  52788  0 
pata_atiixp            13164  0 

``````
dbmeade@ubuntu:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8169
--
04:07.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
    Subsystem: Ralink corp. Device [1814:2860]
    Kernel driver in use: rt2800pci

```

---

### Post by Damascushead on 2012-03-05
If the problem is not isolated to just you, than changing your personal networking settings will not help anything. It is probably a problem with your ISP, you should contact them. Hope that helps a bit.
 
:D

---

### Post by dbmeade on 2012-03-06
Hmmm, I meant that this problem seems to be common among users who have upgraded their system to to Ubuntu 11.10, not that other people around me are having the same problem. After testing the network work speed on a different computer running Win 7, the download speed was back to normal. I'm quite convinced that it has something to do with the RT2800pci driver, as I've noticed that there have been a lot of complaints and complications with this particular one. However, due to my lack of knowledge in the subject I've been unable to find a suitable solution. Thanks for the feed back though!

---

### Post by Her Tigger on 2012-03-09
Me 2 same problem and no fix so far just some a bunch of circles! :-( [http://ubuntuforums.org/showthread.php?t=1938348&highlight=Ralink+Technology](http://ubuntuforums.org/showthread.php?t=1938348&highlight=Ralink+Technology)

---

