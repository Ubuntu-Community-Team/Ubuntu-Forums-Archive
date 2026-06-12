---
title: "Pop/crackle on initial record (and completion)"
date: 2023-04-11
forum: Multimedia Software
---

### Post by dave-bullet on 2023-04-11
Hello,

I'm trying to eliminate a "startup" pop/crackle and final "thud" when playback ceases.

My sound chain is as follows:

Dell laptop (Windows Foobar) -> 3.5mm audio out -> Dell Optiplex 3050 with 3.5mm (dell-headset-multi) audio in -> ALSA (PCH) -> arecord

I am using alsa native - no pulseaudio / jack / pipewire.  My asound.conf is empty and using direct hardware devices, eg:

```
arecord -D hw:0 -f cd /tmp/test.wav
```

On playback via

```
aplay -D hw:0 /tmp/test.wav
```

I get a crackle/pop just before the song starts playing.  When I stop playback in Foobar, after about 3 seconds there is a "pop/thud" as it seems the soundcard / input "turns off" on the Dell Optiplex 3050.

If I restart song playback within the 3 seconds, there is no pop/click.

I am using the default snd-hda-intel kernel module with realtek codec supporting the recognised ALC3234 device/chipset.

I have disabled power_save and power_save_controller parameters on the snd-hda-intel driver (and confirmed these settings in /sys/module)

I have tried a cheap AliExpress USB5.1 soundcard (as a capture device) instead of the built in Dell card and no such crackle on recording commencement.  As this uses the snd-usb-audio driver, I suspect there is a problem with snd-hda-intel (or a parameter I've missed)

I have also tried using an alsa dsnoop device, to allow multi record sessions., thinking the first one would "keep the card awake" whilst then playing the song and recording into another file.  The pop/crackle is still present.

I am unsure what "wake up" or "initialisation" is being done then "Reset" after silence.  

Out of interest, this also happens on an Archlinux 6.2.9 kernel build

Ubuntu version:
```
root@ubuntu-pc:/etc# uname -arLinux ubuntu-pc 5.15.0-60-generic #66-Ubuntu SMP Fri Jan 20 14:29:49 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```

I did an Ubuntu server install with no other custom packages.  I have tried removing pulseaudio and dependent packages but the pop/click on song startup remains.

I'd appreciate any advice, and happy to provide any config dumps needed.

---

### Post by SeijiSensei on 2023-04-12
Try **ffmpeg** to cut off the offending sections and put the results in a new file. For instance, you can tell it to create a file that starts after three seconds and ends just before the final pop. Here are some examples: [https://superuser.com/questions/744823/how-i-could-cut-the-last-7-second-of-my-video-with-ffmpeg/](https://superuser.com/questions/744823/how-i-could-cut-the-last-7-second-of-my-video-with-ffmpeg/).

---

### Post by dave-bullet on 2023-04-12
I appreciate the advice on ffmpeg, but I am dealing with live streaming. that is the source (laptop or TV) will startup anytime and I need this discard first say 0.3seconds to occur when the device "wakens".  I am assuming there is some keep alive or other codec / module setting I should be using... or it is a bug?

I will be capturing the device into DSP software and this runs continually without any knowledge of upstream device activation (i.e. routing via stdin or alsa devices is possible, but it would know when the stream "starts" as it is continually running).

---

### Post by dave-bullet on 2023-04-13
Ok - dumb me.  It is my stupid Windows 10 source laptop with very aggressive power management settings.

I had just blamed my fresh Linux install and poor configuration skills.  not a problem at all :D

Although not sticky between reboots, and for the benefit of others, the Realtek chipset required these binary keys to be set to 4 zeroes:

Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Class\{4d36e96c-e325-11ce-bfc1-08002be10318}\0001\PowerSettings

ConservationIdleTime
IdlePowerState
PerformanceIdleTime

This changes power management from S3 to D0 (disable).

Now to find out how to make it sticky.

---

### Post by SeijiSensei on 2023-04-13
I thought registry changes made using regedit were always permanent but I haven't used it in years. Maybe there's a File > Save option.

---

