---
title: "No Sound and Ubuntu doesn't recognize Soundcard automaticly"
date: 2009-02-23
forum: Multimedia Software
---

### Post by Tim Leonhardt on 2009-02-23
Hello folks,

since some weeks i have got Problems with my sound. From the beginnig it never realy worked, the best Performance was that Rythmbox and Totemplayer worked but VLC and Flash not. I tried to fix that in several ways.

Finally I removed all the alsa system (together with Ubuntu Desktop - Why is that automaticly removed with alsa?! - sry but that really ****** me off)

Now I try just to get to the point where I was before.

I followed the [https://help.ubuntu.com/community/SoundTroubleshooting-Tutorial](https://help.ubuntu.com/community/SoundTroubleshooting-Tutorial).

I want to apologize for my bad english (I am from Germany) und the bad mood of this text, normally I write funnier texts but I am in the middle of the examperiod and my girlfriend goes on my nerves because we haven't Skyped for weeks (because the sound doesn't work and so does Skype)


Here is what I got until now (I would be really thankfull if somebody could help):

------------------------------------------------------------------
lspci -v | less
#Gave me:
00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Subsystem: ABIT Computer Corp. Device 1415
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-amd64
        Kernel modules: amd64-agp

00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0
------------------------------------------------------------------ 
aplay -l
#gave me:
aplay: device_list:215: keine Soundkarten gefunden...
------------------------------------------------------------------ 

#but it worked bevore reinstalling alsa (had problems with flash - tried, completly deinstall alsa, install oss...didnt work out ...)

------------------------------------------------------------------
 sudo modprobe snd_emu10k1
 cat /proc/asound/cards 
 0 [Audigy2        ]: Audigy2 - Audigy 2 ZS [SB0350]
                      Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0xe500, irq 18
#Finally helped, I can see the Window where I can change the volume. But wenn I try Audio Preferences and klick the test-Button none of the Options (e.g. Audigy 2ZS [...] serial.... (OSS) oder (Alsa)) works.
#after that:
tim@tim-desktop:~$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: Audigy2 [Audigy 2 ZS [SB0350]], Gerät 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Untergeordnete Geräte: 32/32
  Untergeordnetes Gerät '0: subdevice #0
  Untergeordnetes Gerät '1: subdevice #1
  Untergeordnetes Gerät '2: subdevice #2
  Untergeordnetes Gerät '3: subdevice #3
  Untergeordnetes Gerät '4: subdevice #4
  Untergeordnetes Gerät '5: subdevice #5
  Untergeordnetes Gerät '6: subdevice #6
  Untergeordnetes Gerät '7: subdevice #7
  Untergeordnetes Gerät '8: subdevice #8
  Untergeordnetes Gerät '9: subdevice #9
  Untergeordnetes Gerät '10: subdevice #10
  Untergeordnetes Gerät '11: subdevice #11
  Untergeordnetes Gerät '12: subdevice #12
  Untergeordnetes Gerät '13: subdevice #13
  Untergeordnetes Gerät '14: subdevice #14
  Untergeordnetes Gerät '15: subdevice #15
  Untergeordnetes Gerät '16: subdevice #16
  Untergeordnetes Gerät '17: subdevice #17
  Untergeordnetes Gerät '18: subdevice #18
  Untergeordnetes Gerät '19: subdevice #19
  Untergeordnetes Gerät '20: subdevice #20
  Untergeordnetes Gerät '21: subdevice #21
  Untergeordnetes Gerät '22: subdevice #22
  Untergeordnetes Gerät '23: subdevice #23
  Untergeordnetes Gerät '24: subdevice #24
  Untergeordnetes Gerät '25: subdevice #25
  Untergeordnetes Gerät '26: subdevice #26
  Untergeordnetes Gerät '27: subdevice #27
  Untergeordnetes Gerät '28: subdevice #28
  Untergeordnetes Gerät '29: subdevice #29
  Untergeordnetes Gerät '30: subdevice #30
  Untergeordnetes Gerät '31: subdevice #31
Karte 0: Audigy2 [Audigy 2 ZS [SB0350]], Gerät 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Untergeordnete Geräte: 8/8
  Untergeordnetes Gerät '0: subdevice #0
  Untergeordnetes Gerät '1: subdevice #1
  Untergeordnetes Gerät '2: subdevice #2
  Untergeordnetes Gerät '3: subdevice #3
  Untergeordnetes Gerät '4: subdevice #4
  Untergeordnetes Gerät '5: subdevice #5
  Untergeordnetes Gerät '6: subdevice #6
  Untergeordnetes Gerät '7: subdevice #7
Karte 0: Audigy2 [Audigy 2 ZS [SB0350]], Gerät 3: emu10k1 [Multichannel Playback]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Audigy2 [Audigy 2 ZS [SB0350]], Gerät 4: p16v [p16v]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0

#but still:
00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Subsystem: ABIT Computer Corp. Device 1415
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-amd64
        Kernel modules: amd64-agp

00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

:



-----------------------------------------------------------------
After restart I have to  sudo modprobe snd_emu10k1 again.

Why doesn't Ubuntu do this automaticaly anymore, how can i change this?

And how do I get the Sound back again?
(I had this Problem bevor and I think I solved it with the alsamixer-preferences, so the Audiopref-window showed me some mor Options to choose and one of them worked out - (not for flash and vlc - which is the last of the 3 big problems I have got with the sound)

Thank you very much in advance

Greets
Tim

---

### Post by Tim Leonhardt on 2009-03-08
1 week an 61 views but no reply... seems like I have a serious problem.

Maybe I try somthing else...like reinstalling Ubuntu completly. 

Is it possible to save al the settings an so on to recover it afterwards?

---

### Post by markbuntu on 2009-03-09
Troubleshooting help is here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

