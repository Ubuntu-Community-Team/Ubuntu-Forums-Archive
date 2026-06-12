---
title: "sound drops from hardware tab of sound prefs"
date: 2010-03-14
forum: Multimedia Software
---

### Post by mylo9000 on 2010-03-14
I just did a complete reinstall of my dualboot system hoping it was user error that caused my audio problems, but the issue has followed me to this install. This tells me that is probably application based.

my Via VT1708/A device tends to disappear from my system.
it started shortly after setting up TVTime.
When i restart the system my usb headset and vt1708 show up ok, but after a while the vt1708 will disappear and i can't get sound to pipe from the cd line to the usb headset. this makes watching tv a no joy situation.

i checked my syslog and found this:

```
Mar 14 17:43:07 mylo9000-desktop pulseaudio[2523]: module-alsa-card.c: Failed to find a working profile.
Mar 14 17:43:07 mylo9000-desktop pulseaudio[2523]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c: snd_pcm_delay() returned a value that is exceptionally large: -685632 bytes (-3886 ms).
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c: snd_pcm_dump():
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c: Soft volume PCM
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c: Control: PCM Playback Volume
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c: min_dB: -51
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c: max_dB: 0
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c: resolution: 256
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c: Its setup is:
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   stream       : CAPTURE
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   access       : MMAP_INTERLEAVED
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   format       : S16_LE
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   subformat    : STD
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   channels     : 2
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   rate         : 44100
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   exact rate   : 44100 (44100/1)
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   msbits       : 16
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   buffer_size  : 16384
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   period_size  : 8192
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   period_time  : 185759
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   tstamp_mode  : ENABLE
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   period_step  : 1
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   avail_min    : 8192
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   period_event : 0
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   start_threshold  : -1
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   stop_threshold   : 1073741824
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   silence_threshold: 0
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   silence_size : 0
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   boundary     : 1073741824
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c: Slave: Hardware PCM card 0 'HDA VIA VT82xx' device 0 subdevice 0
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c: Its setup is:
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   stream       : CAPTURE
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   access       : MMAP_INTERLEAVED
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   format       : S16_LE
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   subformat    : STD
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   channels     : 2
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   rate         : 44100
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   exact rate   : 44100 (44100/1)
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   msbits       : 16
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   buffer_size  : 16384
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   period_size  : 8192
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   period_time  : 185759
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   tstamp_mode  : ENABLE
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   period_step  : 1
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   avail_min    : 8192
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   period_event : 0
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   start_threshold  : -1
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   stop_threshold   : 1073741824
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   silence_threshold: 0
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   silence_size : 0
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   boundary     : 1073741824
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   appl_ptr     : 180192
Mar 14 17:43:24 mylo9000-desktop pulseaudio[2523]: alsa-util.c:   hw_ptr       : 8784
Mar 14 17:43:28 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 3507 events suppressed
Mar 14 17:43:33 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 4096 events suppressed
Mar 14 17:43:38 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 4099 events suppressed
Mar 14 17:43:43 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 4013 events suppressed
Mar 14 17:43:48 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 4091 events suppressed
Mar 14 17:43:53 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 4022 events suppressed
Mar 14 17:43:58 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 4174 events suppressed
Mar 14 17:44:03 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 3964 events suppressed
Mar 14 17:44:08 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 4090 events suppressed
Mar 14 17:44:13 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 3977 events suppressed
Mar 14 17:44:18 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 4095 events suppressed
Mar 14 17:44:23 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 4042 events suppressed
Mar 14 17:44:28 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 4096 events suppressed
Mar 14 17:44:33 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 4085 events suppressed
Mar 14 17:44:38 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 3985 events suppressed
Mar 14 17:44:43 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 3946 events suppressed
Mar 14 17:44:48 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 4054 events suppressed
Mar 14 17:44:53 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 4090 events suppressed
Mar 14 17:44:58 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 3986 events suppressed
Mar 14 17:45:02 mylo9000-desktop pulseaudio[2523]: alsa-source.c: snd_pcm_avail: Device or resource busy
Mar 14 17:45:03 mylo9000-desktop pulseaudio[2523]: ratelimit.c: 2523 events suppressed
Mar 14 17:45:54 mylo9000-desktop pulseaudio[2523]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Mar 14 17:45:54 mylo9000-desktop pulseaudio[2523]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_usb_audio'. Please report this issue to the ALSA developers.
Mar 14 17:45:54 mylo9000-desktop pulseaudio[2523]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
```

i can reboot pulse audio with:
```
killall pulseaudio
```
followed by:
```
pulseaudio
```
and it will work again but only to fail again minutes later.
i would like to fix this so it doesn't keep happening because it isn't acceptable to keep killing and restarting pulseaudio to keep using my head set.
Rythembox won't play music either as long as the via card isn't responding, and will stop playing as with an error as soon as the via card disappears.

any help on this will be greatly appreciated.

---

### Post by mylo9000 on 2010-03-14
Ok i think i've got a source on where the issue is that causing alsa to die on me...
well i think alsa is dying based on the syslog

i had the module-loop back added based on this forum post

> **rusty0101 said:**
> WARNING: I am including command line commands to make modifications to my system. Do not blindly do this yourself. If you do not understand what the commands are doing, please review the manual entries for each command, and review the parameters carefully. A poorly constructed command or one maliciously constructed can leave your system in an unreliable or even unusable state.

For future reference, the link I followed to get the following information was [https://answers.launchpad.net/ubuntu/+source/pulseaudio/+question/83742](https://answers.launchpad.net/ubuntu/+source/pulseaudio/+question/83742)

To add the loopback module to the running instance of Pulse Audio I used the command:
$ pactl load-module module-loopback

To make the module automatically load in the future, I used the command:
$ sudo sh -c ' echo "load-module module-loopback" >> /etc/pulse/default.pa '

Once module-loopback was loaded, the pulse audio Volume Control panel adds an option to the Recording tab that allows you to select the input you wish to use on the loopback device.

I'm of the opinion that this should be a cleaner setup. If you have a TV Capture card, or as I do, radios that you want to be able to listen to, and at other times want to be able to record podcasts,etc through the same interface, it's a bit difficult to do without the module loaded. It could be muted by default, perhaps with a hovering help lable indicating what the features or functions of the device are. For many there will be no interest in the device. That's OK too.

so from that i tried to pipe the CD line in from my via card to my usb headset. but for some reason after a little while my via on board sound would die. hell, it dies 2 minutes after a boot up. so i removed the module for my tv card thinking that was it. but still after a few minutes the via card drops out and the same stuff showed up in syslog.

so i commented out the stuff added to the default.pa rebooted and the alsa and the vt1708/a is stable... i suppose the loopback causes a build up in the alsa system that eventully causes it to fail. 

well i guess I'm going to have to find a different way to get the sound from my tv card to my usb headset.

or just wait until they finally get pulseaudio to properly work allocating all aspects of the sound system. but i won't hold my breath. I see now why there is so much un-love for the pa system. it works-ish but not as well as it could.

---

### Post by Yellow Pasque on 2010-03-14
Have you tried updating ALSA? There's been some fixes for USB audio since the version of ALSA found in Karmic: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

