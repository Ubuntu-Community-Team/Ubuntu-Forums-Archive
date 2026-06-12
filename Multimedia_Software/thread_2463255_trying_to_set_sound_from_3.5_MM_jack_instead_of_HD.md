---
title: "trying to set sound from 3.5 MM jack instead of HDMI"
date: 2021-06-07
forum: Multimedia Software
---

### Post by jfaberna on 2021-06-07
I have 2 monitors connected via HDMI/DP to a new ASRock i7 NUC 1165G7. I can get sound by selecting either of the HDMI Monitors as the sound output device, but I want to use a set of amplified PC speakers that I used with my old PC connected to the 3.5MM jack on the front of the NUC.

With the speakers connected to the front of the NUC I only hear occasional pops and the analog out doesn't show up on my list of devices in settings/sound.

I know this NUC is a new gen 11 CPU and chipset but I've gotten everything else to work by using the OEM kernel: 5.10.0-1029-oem x86_64

Any help would be appreciated.

---

### Post by TheFu on 2021-06-07
Could the front jacks be wired backwards?  Mic --> speakers and speakers --> Mic?

Anyway, go into **pavucontrol**, start in the far right tabs and disable (select "Off") for any hardware you don't want used - only leave the analog output enabled, no HDMI and no digital output.  If the device only has HDMI outputs, then set that entire device "off".

Then work left through the tabs - Output, Playback. Ensure the output settings are at 100%, not muted and enabled. Should say "Headphones (plugged in)" Don't use the "monitor" device.  Only use the "Playback" tab to control the volume.

On my Intel desktop, the device is listed as "Built-in Audio Analog Surround 5.1".

A minimal inxi run would let us see the audio setup. For example:
```
$ inxi -Ax
Audio:     Card-1 Intel 8 Series/C220 Series High Def. Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k5.4.0-74-generic
```
On my system, both are using Intel audio drivers - one is for HDMI and the other is handling all the non-HDMI output.

---

### Post by jfaberna on 2021-06-11
with pavucontrol it shows a number of HDMI and analog choices. but all of the analog ones are unavailable/unplugged.

inxi -Ax
Audio:
  Device-1: Intel vendor: ASRock driver: snd_hda_intel v: kernel 
  bus ID: 00:1f.3 
  Sound Server: ALSA v: k5.10.0-1029-oem

---

### Post by TheFu on 2021-06-11
Have you tried unplugging and replugging in the 3.5mm jack?  Sometimes that is enough.

I see you are on the bleeding edge kernel. Could be a kernel issue. Can you use an older kernel or does the newness of the computer demand only the latest?  New isn't always better. 

Or it could be that the driver doesn't recognize when a 3.5mm jack is plugged in.  Open a bug if that is the situation.

---

### Post by jfaberna on 2021-06-12
I'm guessing the hardware is too new. I installed the OEM kernel to get the GFX working mainly. My solution has been to use the analog out of the HDMI monitors for the speakers 3.5mm plug. It works but sometimes it forgets which monitor the sound is coming from and I have to use settings to select the other HDMI sound channel.

---

