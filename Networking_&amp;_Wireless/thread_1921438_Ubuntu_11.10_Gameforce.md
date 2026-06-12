---
title: "Ubuntu 11.10 Gameforce"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by soldcarvalho on 2012-02-06
Hello Everyone,

Im making a test on Ubuntu and Linux by himself, im a technician who a little work with linux and now Im making a work with ubuntu 11.10 (one of my favourites distribution) but I dont know many things about this.

Well, lets begin with my problem, I Have a insys gameforce which the Internet is too slow with ubuntu, well, like this:

[http://www.speedtest.net/result/1756603613.png](http://www.speedtest.net/result/1756603613.png)

[[IMG]http://www.speedtest.net/result/1756603613.png[/IMG]](http://www.speedtest.net)

Bad isnt it? 

Before I posted this here I tried a lot of commands from other post here, like this one [http://ubuntuforums.org/showthread.php?t=1877120](http://ubuntuforums.org/showthread.php?t=1877120) but nothing could resolve my problem, because that I need some of your help please.

Well, my lsmod is this 


> gameforce@gameforce-M7X0SU:~$ lspci -nnk | grep -iA2 net
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
	Subsystem: CLEVO/KAPOK Computer Device [1558:0802]
	Kernel driver in use: sis190
gameforce@gameforce-M7X0SU:~$ lsmod
Module                  Size  Used by
usbhid                 41905  0 
hid                    77367  1 usbhid
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
vesafb                 13489  1 
arc4                   12473  2 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
rtl8187                56323  0 
mac80211              393459  1 rtl8187
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              172427  2 rtl8187,mac80211
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
eeprom_93cx6           12653  1 rtl8187
uvcvideo               67271  0 
psmouse                73673  0 
nvidia               7098131  36 
serio_raw              12990  0 
snd_timer              28932  2 snd_pcm,snd_seq
videodev               85626  1 uvcvideo
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
dm_multipath           22771  0 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  0 
wmi                    18744  0 
sis_agp                13165  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sis190                 22575  0 
sata_sis               12703  3 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash


Any help is welcome :)


Thank You,
Soldcarvalho

---

### Post by soldcarvalho on 2012-02-07
Today when i got home speedtest got a result of 10mb. But now is bad again like yesterday.

Can anyone tell me something please?

Im making a good resume right?

---

### Post by soldcarvalho on 2012-02-09
Please some help? :(

---

