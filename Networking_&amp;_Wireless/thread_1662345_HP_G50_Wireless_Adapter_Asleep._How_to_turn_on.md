---
title: "HP G50 Wireless Adapter Asleep. How to turn on?"
date: 2011-01-07
forum: Networking &amp; Wireless
---

### Post by programmer99 on 2011-01-07
Hello. My problem is that I cannot get my wireless internet working. After looking on the Ubuntu website and following a few steps, some shown below, I found that my wireless network adapter is asleep. The problem is, the Ubuntu documentation said that enabling a wireless adapter is different for every computer. I was wondering if anyone with an Hewlett Packard G50 knows how to enable the wireless adapter. Below are some details on my problem.

After using the lshw command:

*-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: 00:23:4e:64:d7:e7
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:d2600000-d260ffff

I think the results of the lshw command are telling me that the computer recognizes the wireless network adapter so that is not the problem.

My driver is an ath5k and it shows up in the lsmod command so I know it is recognized.

After running another command, I forget the name, it showed that my adapter was asleep. I do not know how to turn it on. Thanks.

---

### Post by PatchesTheCaveman on 2011-01-08
Try this:  [http://ubuntuforums.org/showpost.php?p=10326568&postcount=2](http://ubuntuforums.org/showpost.php?p=10326568&postcount=2)

---

### Post by programmer99 on 2011-01-08
I used the terminal commands from that post and the results gave me:
 
0: phy0: Wireless LAN
soft block: no
hard block: yes
 
Since it is hardblocked I decided to hit the wireless button on my computer but it didn't fix it. Any suggestions?

---

### Post by PatchesTheCaveman on 2011-01-09
Apparently this laptop needs the kernel to do some magic to turn on your wireless card.  I need to collect some information to figure out how to make it do that.  Please run:
```
lsmod
```
and copy/paste the output.

---

### Post by programmer99 on 2011-01-11
Module Size Used by
nls_iso8859_1 3249 0 
nls_cp437 4919 0 
vfat 8933 0 
fat 47767 1 vfat
binfmt_misc 6587 1 
ppdev 5259 0 
joydev 8708 0 
snd_hda_codec_intelhdmi 11622 1 
snd_hda_codec_conexant 22641 1 
fbcon 35102 71 
tileblit 2031 1 fbcon
font 7557 1 fbcon
bitblit 4707 1 fbcon
softcursor 1189 1 bitblit
vga16fb 11385 0 
vgastate 8961 1 vga16fb
arc4 1153 2 
snd_hda_intel 22005 2 
snd_hda_codec 74201 3 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep 5412 1 snd_hda_codec
snd_pcm_oss 35308 0 
snd_mixer_oss 13746 1 snd_pcm_oss
snd_pcm 70694 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy 1338 0 
snd_seq_oss 26722 0 
snd_seq_midi 4557 0 
snd_rawmidi 19056 1 snd_seq_midi
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 19098 2 snd_pcm,snd_seq
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915 287426 3 
drm_kms_helper 29329 1 i915
ath5k 121632 0 
snd 54180 17 snd_hda_codec_intelhdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo 57054 0 
videodev 34361 1 uvcvideo
drm 162409 4 i915,drm_kms_helper
v4l1_compat 13251 2 uvcvideo,videodev
mac80211 205402 1 ath5k
ath 7611 1 ath5k
psmouse 63245 0 
serio_raw 3978 0 
cfg80211 126528 3 ath5k,mac80211,ath
led_class 2864 1 ath5k
intel_agp 24375 2 i915
soundcore 6620 1 snd
agpgart 31724 2 drm,intel_agp
snd_page_alloc 7076 2 snd_hda_intel,snd_pcm
i2c_algo_bit 5028 1 i915
video 17375 1 i915
output 1871 1 video
lp 7028 0 
parport 32635 2 ppdev,lp
usb_storage 39553 0 
ahci 32200 2 
r8169 34108 0 
mii 4381 1 r8169

---

### Post by nm_geo on 2011-01-11
While Patches is doing the heavy lifting, I am sure you have pushed the wireless button right?

[http://h10032.www1.hp.com/ctg/Manual/c01572022.pdf](http://h10032.www1.hp.com/ctg/Manual/c01572022.pdf)

---

### Post by PatchesTheCaveman on 2011-01-12
Run:
```
sudo modprobe rfkill
sudo rfkill unblock all
```
That will fix it for now.

To make that fix permanent, run this:
```
sudo bash -c "echo rfkill >> /etc/modules"
```

---

### Post by crazyimbroglios on 2013-01-30
anyone having this problem there is a simple fix while booting after you select your OS from grub wait a few seconds and press the wifi button one time before linux loads you may have to try a few times to get it but it does work

---

