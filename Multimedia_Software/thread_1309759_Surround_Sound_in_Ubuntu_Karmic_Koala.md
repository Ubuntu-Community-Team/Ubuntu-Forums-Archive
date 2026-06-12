---
title: "Surround Sound in Ubuntu Karmic Koala"
date: 2009-11-01
forum: Multimedia Software
---

### Post by zamrg on 2009-11-01
I can't seem to get my surround sound working on Ubuntu Karmic Koala - had the same problem with Hardy and Jaunty but managed to fix it by disabling pulseaudio and using alsa directly ([http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)).  I'm a little reluctant to do this again and I'm hoping there's a simple solution with Karmic Koala.  I've tried a whole bunch of suggested solutions but I now don't have a clue what to do.

At first I had no sound, but google lead me to Sound Preferences -> Hardware -> Profile from which I changed 'Analog Stereo Output' to 'Digital Stereo Duplex (IEC958)', after which I managed to get stereo working.

lspci -v
```

03:00.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
	Subsystem: Creative Labs Device 1021
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at d000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

```

aplay -L
```

front:CARD=Audigy2,DEV=0
    SB Audigy 4 [SB0610], ADC Capture/Standard PCM Playback
    Front speakers
rear:CARD=Audigy2,DEV=0
    SB Audigy 4 [SB0610], ADC Capture/Standard PCM Playback
    Rear speakers
center_lfe:CARD=Audigy2,DEV=0
    SB Audigy 4 [SB0610], ADC Capture/Standard PCM Playback
    Center and Subwoofer speakers
side:CARD=Audigy2,DEV=0
    SB Audigy 4 [SB0610], ADC Capture/Standard PCM Playback
    Side speakers
surround40:CARD=Audigy2,DEV=0
    SB Audigy 4 [SB0610], ADC Capture/Standard PCM Playback
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Audigy2,DEV=0
    SB Audigy 4 [SB0610], ADC Capture/Standard PCM Playback
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Audigy2,DEV=0
    SB Audigy 4 [SB0610], ADC Capture/Standard PCM Playback
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Audigy2,DEV=0
    SB Audigy 4 [SB0610], ADC Capture/Standard PCM Playback
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Audigy2,DEV=0
    SB Audigy 4 [SB0610], ADC Capture/Standard PCM Playback
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Audigy2,DEV=0
    SB Audigy 4 [SB0610], ADC Capture/Standard PCM Playback
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server

```

I have edited my /etc/pulse/daemon.conf and uncommented 'default-sample-channels = 8'

I've also set up a .asoundrc in my home directory which looks like:

```

pcm.!dmix {
   type plug
   slave {
   pcm surround71
   channels 8
}

}
pcm.!default {
   type plug
   slave.pcm "dmix"
   slave.channels 8
   route_policy duplicate
}

```

I'm also getting a whole bunch of errors in my user.log, although I have no idea what they mean.

```

Oct 31 22:32:12 zephyr pulseaudio[1956]: alsa-util.c: Unable to set sw params: No such device
Oct 31 22:32:12 zephyr pulseaudio[1956]: alsa-sink.c: Failed to set software parameters: No such device
Oct 31 22:39:02 zephyr pulseaudio[2707]: alsa-util.c: Unable to set sw params: No such device
Oct 31 22:39:02 zephyr pulseaudio[2707]: alsa-sink.c: Failed to set software parameters: No such device
Oct 31 22:39:08 zephyr pulseaudio[2845]: pid.c: Stale PID file, overwriting.
Oct 31 22:39:08 zephyr pulseaudio[2845]: module-alsa-card.c: Failed to find a working profile.
Oct 31 22:39:08 zephyr pulseaudio[2845]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="0" name="pci-0000_03_00.0" card_name="alsa_card.pci-0000_03_00.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Oct 31 22:40:46 zephyr pulseaudio[2033]: alsa-util.c: Unable to set sw params: No such device
Oct 31 22:40:46 zephyr pulseaudio[2033]: alsa-sink.c: Failed to set software parameters: No such device
Oct 31 22:40:59 zephyr pulseaudio[2211]: module-alsa-card.c: Failed to find a working profile.
Oct 31 22:40:59 zephyr pulseaudio[2211]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="0" name="pci-0000_03_00.0" card_name="alsa_card.pci-0000_03_00.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Oct 31 22:42:21 zephyr pulseaudio[2555]: alsa-util.c: Unable to set sw params: No such device
Oct 31 22:42:21 zephyr pulseaudio[2555]: alsa-sink.c: Failed to set software parameters: No such device
Oct 31 22:42:26 zephyr pulseaudio[2641]: pid.c: Stale PID file, overwriting.
Oct 31 22:42:57 zephyr pulseaudio[2641]: alsa-util.c: Unable to set sw params: No such device
Oct 31 22:42:57 zephyr pulseaudio[2641]: alsa-sink.c: Failed to set software parameters: No such device
Oct 31 22:44:44 zephyr pulseaudio[2102]: alsa-util.c: Unable to set sw params: No such device
Oct 31 22:44:44 zephyr pulseaudio[2102]: alsa-sink.c: Failed to set software parameters: No such device

```

---

### Post by zamrg on 2009-11-01
I went into alsamixer and unmuting 'Audigy Analog/Digital Output Jack' and I now get sound from 5/7 of my speakers.

I've just done a speaker-test -c8 -twav & I get the following result:

front left - no sound
front center - working
front right - no sound
side right - comes out as front right
side left - comes out as front left
rear right - working
rear left - working

If I try play something with vlc/totem, only my front left & front right work.

*EDIT*

I switched from 'Digital Stereo Duplex (IEC95) to 'Analog Surround 5.1 Output' and speaker-test now works on 5 speakers & vlc/totem play through all of them.  I still can't choose 'Analog Surround 7.1 Output' but anyhow, this seems to work.

---

### Post by fermulator on 2010-08-22
I have the same issue.
 * Ubuntu 9.10 (Linux fermmy-media 2.6.31-22-generic-pae #61-Ubuntu SMP Wed Jul 28 03:15:32 UTC 2010 i686 GNU/Linux)
 * pulseaudio (1:0.9.19-0ubuntu4.1)
 * vlc 1.02

> multimedia@fermmy-media:~$ cat /etc/pulse/daemon.conf | grep sample-channel
default-sample-channels = 8



**_In {{{pavucontrol}}}, "Configuration" tab:_**

If I choose the 7.1 SB Audigy profile:
 * speaker test for 7.1 works
 * vlc doesn't play any sound

If I choose the 5.1 SB Audigy profile:
 * speaker test still works for 7.1 surround (this is confusing and odd, but, I guess with the sample-channels=8 this still works...)
 * vlc plays some audio, but is lacking the front left/right channels (i.e. no vocal/speech), but ambient background and music plays.

If I choose the 4.0 SB Audigy profile:
 * speaker test still works for 7.1 surround
 * vlc plays front left/right, rear left/right, as per 4.0 profile.

I want /everything/ to work with the 7.1 surround sound.  How can we accomplish this?

In vlc, there is no way (AFAIK) to manually set the surround sound type.  There doesn't appear to be anything useful in the Audio configuration for this application, and so I presume it defaults to whatever hardware profile is currently set by Ubuntu.  Thus, I was trying to set the hardware profile to something better than 4.0.  (for now, I leave @ 4.0 because at least it is functional, but not optimal)

I've tried a few other players, and similar problems exist.

---

