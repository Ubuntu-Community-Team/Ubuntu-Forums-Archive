---
title: "BDCM 4320 no firmware"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by Madonk on 2012-06-19
Hello,

I have an old laptop that I am trying to run the newest version of Ubuntu on a Compaq Presario R3000. The Wireless card is 4320. I cannot find nor get any firmware to work! Please help! :(

---

### Post by wildmanne39 on 2012-06-19
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by Madonk on 2012-06-19
```
weekly@weekly-Presario-R3000-DZ353U-ABA:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux weekly-Presario-R3000-DZ353U-ABA 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686 athlon i386 GNU/Linux
weekly@weekly-Presario-R3000-DZ353U-ABA:~$ lspci -nnk | grep -iA2 net
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:006b]
    Kernel driver in use: 8139too
--
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
    Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:12f4]
    Kernel modules: ssb
weekly@weekly-Presario-R3000-DZ353U-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

weekly@weekly-Presario-R3000-DZ353U-ABA:~$ rfkill list all
weekly@weekly-Presario-R3000-DZ353U-ABA:~$ rfkill list all
weekly@weekly-Presario-R3000-DZ353U-ABA:~$ lsmod
Module                  Size  Used by
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83507  0 
hfs                    49479  0 
minix                  31418  0 
ntfs                  100171  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55605  2 vfat,msdos
jfs                   175085  0 
xfs                   747494  0 
reiserfs              230896  0 
ext2                   67987  0 
joydev                 17393  0 
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
nouveau               712294  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
arc4                   12473  0 
ttm                    65344  1 nouveau
pcmcia                 39791  0 
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         45466  1 nouveau
drm                   197692  4 nouveau,ttm,drm_kms_helper
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                72919  0 
yenta_socket           27465  0 
i2c_algo_bit           13199  1 nouveau
serio_raw              13027  0 
mxm_wmi                12859  1 nouveau
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12905  0 
shpchp                 32325  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
i2c_nforce2            12906  0 
video                  19068  1 nouveau
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  1 
ppdev                  12849  0 
wmi                    18744  1 mxm_wmi
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
8139too                23283  0 
8139cp                 26759  0 
pata_amd               13750  2 


```

---

### Post by wildmanne39 on 2012-06-19
Hi, please try:
```
sudo apt-get install linux-firmware-nonfree
```
Then reboot.
Thanks

---

### Post by Madonk on 2012-06-19
wilco. standby.

---

### Post by Madonk on 2012-06-19
> **wildmanne39 said:**
> Hi, please try:
```
sudo apt-get install linux-firmware-nonfree
```
Then reboot.
Thanks
Thank you, it worked! I greatly appreciate you!

---

### Post by wildmanne39 on 2012-06-19
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by zaphod_es on 2012-06-29
Same problem, 64bit Intel system running Ubuntu 12.04 on a fresh default install of a new computer. The wifi card was taken from an old box running Ubuntu 10.04 where it worked just fine.  Network Manager shows the wireless options all greyed out.

I ran this line
```
sudo apt-get install linux-firmware-nonfree
```

And, after that and a reboot the output from the commands you asked Madonk is listed below.

Please help.

ZB


```
$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux USER 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
user@USER:~$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
	Subsystem: Intel Corporation Device [8086:200c]
	Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Askey Computer Corp. Device [144f:7077]
	Kernel modules: ssb
user@USER:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

user@USER:~$ rfkill list all
user@USER:~$ lsmod
Module                  Size  Used by
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
snd_hda_codec_realtek   223867  1 
brcmsmac              570859  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
shpchp                 37277  0 
i915                  468651  3 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         46978  1 i915
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   242038  4 i915,drm_kms_helper
mei                    41616  0 
i2c_algo_bit           13423  1 i915
soundcore              15091  1 snd
video                  19596  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac80211              506816  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205544  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12535  1 brcmsmac
ppdev                  17113  0 
parport_pc             32866  1 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
e1000e                156693  0 
```

---

### Post by chili555 on 2012-06-29
The Wild Man is on his coffee break, so I'll be glad to help. I think the driver that's loaded, brcmsmac is incorrect. Let's try an experiment:```
sudo modprobe -r brcmsmac
sudo modprobe b43
```Does your wireless work now? If so, let's make it persistent:```
sudo su
echo "blacklist brcmsmac" >> /etc/modprobe.d/blacklist.conf
echo b43 >> /etc/modules
exit
```If it's not working, post back and we'll dig deeper.

---

### Post by zaphod_es on 2012-06-30
Fantastic, it now works perfectly, so easy when you know how.  You can throw Wild Man another lump of meat and tell him to sleep on :)

ZB

---

### Post by chili555 on 2012-06-30
We're glad it's working as expected.

NOTE TO SEARCHERS: This magic fix is for pci.id 14e4:4320 *only*. If this is not your device or you are unsure, please post a new thread.

---

