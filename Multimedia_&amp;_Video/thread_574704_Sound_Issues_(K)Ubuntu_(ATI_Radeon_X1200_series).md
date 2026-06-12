---
title: "Sound Issues (K)Ubuntu (ATI Radeon X1200 series)"
date: 2007-10-13
forum: Multimedia &amp; Video
---

### Post by PeterSomnium on 2007-10-13
Hi, I recently bought a new laptop (Asus Z83Useries M/B A7U), and I decided to install kubuntu 7.10 on it, since I wanted to get rid of the Vista pre-install asap.

At the moment, everything works, except for 2 things, wifi and sound. Wifi is not my main concern, since the laptop is a desktop replacement and there is a cable available. The point is, sound would be nice ^_^".

Anyway, my issue is quite strange, if I say so myself. The laptop seems to recognize the card perfectly, and doesn't give errors, but for some reason, there is no sound. And yes, I checked all the volume and mute settings through Kmix, alsamixer and physical buttons (there are none).

this is my lspci output 
```

root@peter-laptop:~# lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
05:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
07:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
08:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
08:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

```

Also, this is my aplay-l output, and the card(s) seem to be recognized as well there.
```
root@peter-laptop:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 0: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

I hope someone can help me, I've been searching for a solution for 2 days now, and I'm nearing insanity.

---

### Post by wieman01 on 2007-10-13
Might this relate to your problem? I had similar problems and it turned out that it actually was an issue with the admin rights:
[http://ubuntuforums.org/showthread.php?t=571426]("http://ubuntuforums.org/showthread.php?t=571426")
[http://ubuntuforums.org/showthread.php?t=561644]("http://ubuntuforums.org/showthread.php?t=561644")

---

### Post by PeterSomnium on 2007-10-13
And how would that work? My main user (peter UID=1000) is part of the audio-group, I've checked that.

Any other options?

I've checked the other threads, but there is no solution for me there.

---

### Post by PeterSomnium on 2007-10-14
I checked my dmesg, and the following is in it:

```

[   73.692000] hda-intel: Invalid position buffer, using LPIB read method instead.

```

This could be related to this issue, right? It seems that the ATI Radeon X1200 is using hda_intel.

lsmod | grep snd yields the following:

```

peter@peter-laptop:~$ lsmod | grep snd
snd_seq_dummy           4996  0
snd_seq_oss            35328  0
snd_seq_midi            9728  0
snd_rawmidi            26112  1 snd_seq_midi
snd_hda_intel         262552  7
snd_pcm_oss            44800  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                81028  5 snd_hda_intel,snd_pcm_oss
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54256  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56452  21 snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm

```

Also, I read earlier in another topic (lost the number, sorry) that more devices with the same name (in this case the soundcard card0) can give conflicting issues.
As seen in my first post, there are 2 entries with card0 when doing aplay -l. One is my analogue sound card (don't care much about HD) and the other is the built-in modem.
Is there a way to unload those device drivers to see if that helps or not?

---

### Post by hth on 2007-10-21
Hi,

since I'm experiencing the very same problem (gigabyte ga-ma69vm-s2): did you find a solution/workaround?

regards

Holger

---

### Post by PeterSomnium on 2007-10-22
Nope, sorry, I'm still looking for a proper solution.
At the moment, I'm running Kubuntu in a VMware machine under windows XP (lame I know, but I refuse to use windows, and try to avoid it anytime possible.

I ám still looking for a solution, but since I hear lots of people about this issue, I don't think it's going to be anywhere soon.

Cheers,
Pete

---

### Post by hth on 2007-10-22
Hmmm, I guess I kind of fixed it... I reinstalled ALSA manually (can't remember, where I found the instructions though...):
```

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
```

Now I had sound when I started xine, but couldn't control it using the kmix-plugin. It turned out, that the kmix master channel was set to PC Speaker, not to Front.

---

### Post by PeterSomnium on 2007-10-22
Tried that before, but that didn't work for me.
I did a fresh install of Kubuntu, tried compiling alsa myself and also used the module-assistant.

I tried OpenSUSE 10.4 as well, so the issue is not only limited to (K)ubuntu, it's a driver issue. There seems to be an issue with the snd_hda_intel driver, it doesn't work properly.

Or at least, that's my opinion, feel free to concur.

---

### Post by hth on 2007-10-22
I just rechecked everything... and recognized, that my machine gives diffent output for aplay -i:
```

**** Liste von PLAYBACK Geräten ****
Karte 0: SB [HDA ATI SB], Gerät 0: ALC883 Analog [ALC883 Analog]
  Untergeordnete Geräte: 0/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: SB [HDA ATI SB], Gerät 1: ALC883 Digital [ALC883 Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
```
lspci | grep -i audio results in pretty much the same output as your machine:
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
```
Too bad, that your problem can't be cured as easy as mine...

---

### Post by PeterSomnium on 2007-10-23
What I see in my aplay -l is that there is another device, a modem or such.
There is a slight possibility that it's working against the other ones.

The point is, I know some things about linux, but not how to remove that one ^_~

---

### Post by henklaak on 2007-10-24
Hi there,

I have the luxury of two Asus laptops, a Asus F5R and a A7U:

Both have the same audio hardware, both are running 7.10, same kernel 2.6.22-14
The F5R makes sound and the A7U is silent.
From the logs, both are pretty equal. The A7U has the HDMI though.

Any ideas what I could do to help solving the issue?

Regards, Henk

--- output follows ---

========================================================================================
F5R > sudo lcpci -v -s 14.2
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: ASUSTeK Computer Inc. Unknown device 1339
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at febf4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2

A7U > sudo lcpci -v -s 14.2
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
        Subsystem: ASUSTeK Computer Inc. Unknown device 1339
        Flags: bus master, slow devsel, latency 64, IRQ 16
        Memory at febf4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2

========================================================================================
F5R > aplay -l
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

A7U > aplay -l
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 0: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

========================================================================================
F5R > dmesg
[   44.888000] hda-intel: Invalid position buffer, using LPIB read method instead.

A7U > dmesg
[   35.088000] hda-intel: Invalid position buffer, using LPIB read method instead.

========================================================================================
F5R > lsmod | grep snd
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

A7U > lsmod | grep snd
snd_hda_intel         262552  1 
snd_pcm_oss            44800  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35328  0 
snd_seq_midi            9728  0 
snd_rawmidi            26112  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54256  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56452  12 snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm

---

### Post by henklaak on 2007-10-25
Partly good news. I found that the A7U's microphone is working. When I use skype, the receiving party can hear me.

Regards, Henk

---

### Post by henklaak on 2007-10-28
Solved it! Yesssssssssss!!

This excellent howto: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
made it possible.

I built the latest ALSA drivers 1.0.15 and needed to add this line to my /etc/modprobe.d/alsa-conf file:

options snd-hda-intel model=auto

I don't know if the 1.0.15 was necessary, but I'm not going back to try it out. A working system doesn't need fixing, right?

Gr. Henk.

---

### Post by Daviey on 2007-11-01
Did you get sound over HDMI working?

---

### Post by henklaak on 2007-11-01
To be honest, I don't even know how to try that. 

I still think of HDMI as "the DRM encumbered VGA connector" and I won't use it.

Video goes through VGA, speakers go in my audio mini-jacks. 

So, the answer is: maybe, I didn't try it.

Gr. Henk.

---

