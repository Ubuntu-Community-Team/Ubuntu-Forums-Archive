---
title: "No Ouput from Headphone Jack"
date: 2006-10-05
forum: Multimedia &amp; Video
---

### Post by neoeno on 2006-10-05
Hey, using kubuntu edgy on a Fujitsu Seimens amilo pro laptop.

My problem is with the sound, the speakers work as well as laptop speakers can be expected to, but there's nothing coming out of the headphone jack. I've been searching and seen similar problems, but they always seem to be with intel sound cards. Which I don't have.

The output of lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0c.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)

```

The output of lsmod | grep -E snd\|sound
```
snd_seq_dummy           4996  0
snd_seq_oss            36736  0
snd_seq_midi           10112  0
snd_seq_midi_event      9088  2 snd_seq_oss,snd_seq_midi
snd_seq                59760  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx_modem      16776  1
snd_via82xx            30488  1
gameport               17288  1 snd_via82xx
snd_ac97_codec         98464  2 snd_via82xx_modem,snd_via82xx
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47744  0
snd_mixer_oss          19712  1 snd_pcm_oss
snd_mpu401_uart        10368  1 snd_via82xx
snd_rawmidi            27392  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_pcm                85252  4 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25476  2 snd_seq,snd_pcm
snd                    58756  16 snd_seq_oss,snd_seq,snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
snd_page_alloc         11528  3 snd_via82xx_modem,snd_via82xx,snd_pcm
soundcore              11232  1 snd

```

Anyone got any ideas?

---

### Post by neoeno on 2006-10-05
Oh, and I've looked into the alsamixer stuff, there isn't a headphone scrollbar as you would expect.

---

### Post by VividHazE on 2006-12-09
Hey neoeno,

I see no one have come to your rescue yet.  I'm having, I think, the exact same problem on the exact same laptop with the same output from the lspci stuff you displayed.

I was just wondering if you had found out a way to solve this problem on your own or through a different method, and if so please let me know as well.  If not, I'll let you know if I find a solution too. :D

VividHazE

---

### Post by marcthepunk on 2007-01-29
i have an amilo L7320GW.  I was able to find the tweaks for most configurations such as dvd playback, video resolution and even s/pdif output headphone.

by default the headphones are muted.  run alsamixer, browse with the directional keys and unmute surround, pcm, and duplicate front by pressing M.

---

### Post by VividHazE on 2007-02-01
OMG man that worked! I didn't realise you had to press M! *does a backflip* You've no idea how happy I am now :)

---

