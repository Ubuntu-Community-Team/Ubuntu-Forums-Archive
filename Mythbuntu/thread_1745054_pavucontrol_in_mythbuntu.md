---
title: "pavucontrol in mythbuntu"
date: 2011-04-30
forum: Mythbuntu
---

### Post by linuxhippy on 2011-04-30
I just installed Mythbuntu 11.04 and can only get audio in mythtv but not from any other app like mplayer.  I think my pc has decided that my 2 TV cards are my sound card and my sound card isn't being seen first (I had to specify that mythtv was to use card=2 for sound).  I downloaded the pulse audio control (pavucontrol) because I was hoping I could fix the sound but it won't start in mythbuntu even with the mythtv process stopped (I get an error window that just says it cannot start).

How can I get pavucontrol to start in mythbuntu?

---

### Post by kja999 on 2011-05-01
Mythbuntu doesnt use pulseaudio ... you would need to install that first ...

---

### Post by linuxhippy on 2011-05-01
interesting...so what tool could I put into mythbuntu that would control the current audio cards used by the entire computer without installing pulse audio?

---

### Post by kja999 on 2011-05-02
Myth gives you the choice of which audio channel to change when you set the volume. If you choose master then this is the main master channel for the machine. If you use myth internal controls it should change the volume just within myth.

---

### Post by linuxhippy on 2011-05-02
this is new to me, I think.  Is this some kind of GUI program or is it CLI and where/how?

I specified in the mythfronted to use card=2 but it was done with the keys.  Where is this done globally?

---

### Post by nickrout on 2011-05-03
what is the output of ls -l /proc/asound   ?

---

### Post by linuxhippy on 2011-05-03
total 0
lrwxrwxrwx  1 root root 5 2011-05-03 06:13 Audigy2 -> card2
dr-xr-xr-x  3 root root 0 2011-05-03 06:13 card0
dr-xr-xr-x  3 root root 0 2011-05-03 06:13 card1
dr-xr-xr-x 11 root root 0 2011-05-03 06:13 card2
-r--r--r--  1 root root 0 2011-05-03 06:13 cards
lrwxrwxrwx  1 root root 5 2011-05-03 06:13 CX8801 -> card1
lrwxrwxrwx  1 root root 5 2011-05-03 06:13 CX8801_1 -> card0
-r--r--r--  1 root root 0 2011-05-03 06:13 devices
-r--r--r--  1 root root 0 2011-05-03 06:13 hwdep
-r--r--r--  1 root root 0 2011-05-03 06:13 modules
-r--r--r--  1 root root 0 2011-05-03 06:13 pcm
dr-xr-xr-x  2 root root 0 2011-05-03 06:13 seq
-r--r--r--  1 root root 0 2011-05-03 06:13 timers
-r--r--r--  1 root root 0 2011-05-03 06:13 version

Now we're getting somewhere!!  card 0 and 1 are my tuner cards while card 2 is my sound card.

---

### Post by nickrout on 2011-05-04
sorry i should have asked these first time, what audio device is myth using?

what is the output of aplay -l and aplay -L

---

### Post by linuxhippy on 2011-05-04
no problem-these are new commands to me (I'm learning):

tux@FreeVo:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: Audigy2 [SB Audigy 2 [SB0350b]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 2: Audigy2 [SB Audigy 2 [SB0350b]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Audigy2 [SB Audigy 2 [SB0350b]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy2 [SB Audigy 2 [SB0350b]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

tux@FreeVo:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Audigy2
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    Default Audio Device
front:CARD=Audigy2,DEV=0
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Audigy2,DEV=0
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Audigy2,DEV=0
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
side:CARD=Audigy2,DEV=0
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    Side speakers
surround40:CARD=Audigy2,DEV=0
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audigy2,DEV=0
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audigy2,DEV=0
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audigy2,DEV=0
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audigy2,DEV=0
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Audigy2,DEV=0
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Audigy2,DEV=0
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    Direct sample mixing device
dmix:CARD=Audigy2,DEV=2
    SB Audigy 2 [SB0350b], Multichannel Capture/PT Playback
    Direct sample mixing device
dmix:CARD=Audigy2,DEV=3
    SB Audigy 2 [SB0350b], Multichannel Playback
    Direct sample mixing device
dmix:CARD=Audigy2,DEV=4
    SB Audigy 2 [SB0350b], p16v
    Direct sample mixing device
dsnoop:CARD=Audigy2,DEV=0
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    Direct sample snooping device
dsnoop:CARD=Audigy2,DEV=2
    SB Audigy 2 [SB0350b], Multichannel Capture/PT Playback
    Direct sample snooping device
dsnoop:CARD=Audigy2,DEV=3
    SB Audigy 2 [SB0350b], Multichannel Playback
    Direct sample snooping device
dsnoop:CARD=Audigy2,DEV=4
    SB Audigy 2 [SB0350b], p16v
    Direct sample snooping device
hw:CARD=Audigy2,DEV=0
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    Direct hardware device without any conversions
hw:CARD=Audigy2,DEV=2
    SB Audigy 2 [SB0350b], Multichannel Capture/PT Playback
    Direct hardware device without any conversions
hw:CARD=Audigy2,DEV=3
    SB Audigy 2 [SB0350b], Multichannel Playback
    Direct hardware device without any conversions
hw:CARD=Audigy2,DEV=4
    SB Audigy 2 [SB0350b], p16v
    Direct hardware device without any conversions
plughw:CARD=Audigy2,DEV=0
    SB Audigy 2 [SB0350b], ADC Capture/Standard PCM Playback
    Hardware device with all software conversions
plughw:CARD=Audigy2,DEV=2
    SB Audigy 2 [SB0350b], Multichannel Capture/PT Playback
    Hardware device with all software conversions
plughw:CARD=Audigy2,DEV=3
    SB Audigy 2 [SB0350b], Multichannel Playback
    Hardware device with all software conversions
plughw:CARD=Audigy2,DEV=4
    SB Audigy 2 [SB0350b], p16v
    Hardware device with all software conversions

---

### Post by nickrout on 2011-05-04
what device is myth using (I did ask that, maybe you missed part of my question )

---

### Post by linuxhippy on 2011-05-04
oh, audio device is a pci card:

Creative Labs SB Audigy (rev 04)

---

### Post by nickrout on 2011-05-04
OK I'll be more specific: go into settings, general and on about the third page there is a setting for the sound device - what is the setting?

---

### Post by linuxhippy on 2011-05-04
ok, this is in mythfrontend on the Audio System page:

Audio output device: ALSA:default:CARD=2

Another thread here was saying to add the CARD=2 to that since I had no sound before that.  I still don't have sound when I play dvds since that uses mplayer or vlc, so I need to know how to make my soundcard the default sound device globally so that I can take out the CARD=2 in mythtv.

---

