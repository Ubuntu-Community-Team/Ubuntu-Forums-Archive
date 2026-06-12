---
title: "No Sound in Skype"
date: 2010-07-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jlward4th on 2010-07-08
I'm on the latest Maverick and sound is no longer working in Skype.  If I uninstall pulseaudio it works again.  Any ideas on how to make it work with pulse?

---

### Post by jlward4th on 2010-07-09
I'm not sure if this helps but here is some of the debug log from pulseaudio when I try to play a sound in Skype:
```
Jul  9 07:57:08 w500 pulseaudio[3661]: module-stream-restore.c: Restoring volume for sink input sink-input-by-media-role:event.
Jul  9 07:57:08 w500 pulseaudio[3661]: module-stream-restore.c: Restoring mute state for sink input sink-input-by-media-role:event.
Jul  9 07:57:08 w500 pulseaudio[3661]: sink.c: Suspend cause of sink alsa_output.pci-0000_00_1b.0.analog-stereo is 0x0000, resuming
Jul  9 07:57:08 w500 pulseaudio[3661]: reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Trying resume...
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-util.c: Maximum hw buffer size is 23777 ms
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-util.c: Set buffer size first (to 88192 samples), period size second (to 44096 samples).
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: hwbuf_unused=0
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: setting avail_min=87862
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Resumed successfully...
Jul  9 07:57:08 w500 pulseaudio[3661]: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo becomes idle, timeout in 5 seconds.
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Starting playback.
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Cutting sleep time for the initial iterations by half.
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Cutting sleep time for the initial iterations by half.
Jul  9 07:57:08 w500 pulseaudio[3661]: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo becomes busy.
Jul  9 07:57:08 w500 pulseaudio[3661]: resampler.c: Channel matrix:
Jul  9 07:57:08 w500 pulseaudio[3661]: resampler.c:        I00 
Jul  9 07:57:08 w500 pulseaudio[3661]: resampler.c:     +------
Jul  9 07:57:08 w500 pulseaudio[3661]: resampler.c: O00 | 1.000
Jul  9 07:57:08 w500 pulseaudio[3661]: resampler.c: O01 | 1.000
Jul  9 07:57:08 w500 pulseaudio[3661]: remap_sse.c: Using SSE mono to stereo remapping
Jul  9 07:57:08 w500 pulseaudio[3661]: resampler.c: Using resampler 'speex-float-1'
Jul  9 07:57:08 w500 pulseaudio[3661]: resampler.c: Using float32le as working format.
Jul  9 07:57:08 w500 pulseaudio[3661]: resampler.c: Choosing speex quality setting 1.
Jul  9 07:57:08 w500 pulseaudio[3661]: memblockq.c: memblockq requested: maxlength=33554432, tlength=0, base=4, prebuf=0, minreq=1 maxrewind=0
Jul  9 07:57:08 w500 pulseaudio[3661]: memblockq.c: memblockq sanitized: maxlength=33554432, tlength=33554432, base=4, prebuf=0, minreq=4 maxrewind=0
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c: Created input 3 "Event Sound" on alsa_output.pci-0000_00_1b.0.analog-stereo with sample spec s16le 1ch 48000Hz and channel map mono
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     window.icon_name = "skype"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     application.icon_name = "skype"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     media.role = "event"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     media.name = "Event Sound"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     application.name = "Skype"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     native-protocol.peer = "UNIX socket client"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     native-protocol.version = "16"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     application.process.id = "3681"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     application.process.user = "jamesw"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     application.process.host = "w500"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     application.process.binary = "skype"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     application.language = "en_US.UTF-8"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     window.x11.display = ":0.0"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     application.process.machine_id = "bd107505ab84037cda96e4e04b0b0142"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     application.process.session_id = "bd107505ab84037cda96e4e04b0b0142-1278682690.932099-1575009069"
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c:     module-stream-restore.id = "sink-input-by-media-role:event"
Jul  9 07:57:08 w500 pulseaudio[3661]: protocol-native.c: Requested tlength=50.00 ms, minreq=10.00 ms
Jul  9 07:57:08 w500 pulseaudio[3661]: protocol-native.c: Adjust latency mode enabled, configuring sink latency to half of overall latency.
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Cutting sleep time for the initial iterations by half.
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Cutting sleep time for the initial iterations by half.
Jul  9 07:57:08 w500 pulseaudio[3661]: memblockq.c: memblockq requested: maxlength=960000, tlength=3360, base=2, prebuf=0, minreq=960 maxrewind=0
Jul  9 07:57:08 w500 pulseaudio[3661]: memblockq.c: memblockq sanitized: maxlength=960000, tlength=3360, base=2, prebuf=0, minreq=960 maxrewind=0
Jul  9 07:57:08 w500 pulseaudio[3661]: protocol-native.c: Final latency 50.00 ms = 15.00 ms + 2*10.00 ms + 15.00 ms
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Cutting sleep time for the initial iterations by half.
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Latency set to 15.00ms
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: hwbuf_unused=350124
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: setting avail_min=87862
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Requesting rewind due to latency change.
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Requested to rewind 352768 bytes.
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Limited to 350740 bytes.
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: before: 87685
Jul  9 07:57:08 w500 pulseaudio[3661]: reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio0 changed: not busy
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: after: 87685
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Rewound 350740 bytes.
Jul  9 07:57:08 w500 pulseaudio[3661]: sink.c: Processing rewind...
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c: Have to rewind 350740 bytes on render memblockq.
Jul  9 07:57:08 w500 pulseaudio[3661]: source.c: Processing rewind...
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c: Requesting rewind due to uncorking
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Requested to rewind 352768 bytes.
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Limited to 1128 bytes.
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: before: 282
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: after: 282
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Rewound 1128 bytes.
Jul  9 07:57:08 w500 pulseaudio[3661]: sink.c: Processing rewind...
Jul  9 07:57:08 w500 pulseaudio[3661]: source.c: Processing rewind...
Jul  9 07:57:08 w500 pulseaudio[3661]: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo becomes busy.
Jul  9 07:57:08 w500 pulseaudio[3661]: protocol-native.c: Requesting rewind due to rewrite.
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Requested to rewind 2664 bytes.
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Limited to 1256 bytes.
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: before: 314
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: after: 314
Jul  9 07:57:08 w500 pulseaudio[3661]: alsa-sink.c: Rewound 1256 bytes.
Jul  9 07:57:08 w500 pulseaudio[3661]: sink.c: Processing rewind...
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c: Have to rewind 1256 bytes on render memblockq.
Jul  9 07:57:08 w500 pulseaudio[3661]: sink-input.c: Have to rewind 684 bytes on implementor.
Jul  9 07:57:08 w500 pulseaudio[3661]: source.c: Processing rewind...
Jul  9 07:57:11 w500 pulseaudio[3661]: sink-input.c: Requesting rewind due to corking
Jul  9 07:57:11 w500 pulseaudio[3661]: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo becomes idle, timeout in 5 seconds.
Jul  9 07:57:11 w500 pulseaudio[3661]: alsa-sink.c: hwbuf_unused=0
Jul  9 07:57:11 w500 pulseaudio[3661]: alsa-sink.c: setting avail_min=87862
Jul  9 07:57:11 w500 pulseaudio[3661]: alsa-sink.c: Requested to rewind 352768 bytes.
Jul  9 07:57:11 w500 pulseaudio[3661]: alsa-sink.c: Limited to 712 bytes.
Jul  9 07:57:11 w500 pulseaudio[3661]: alsa-sink.c: before: 178
Jul  9 07:57:11 w500 pulseaudio[3661]: alsa-sink.c: after: 178
Jul  9 07:57:11 w500 pulseaudio[3661]: alsa-sink.c: Rewound 712 bytes.
Jul  9 07:57:11 w500 pulseaudio[3661]: sink.c: Processing rewind...
Jul  9 07:57:11 w500 pulseaudio[3661]: source.c: Processing rewind...
Jul  9 07:57:11 w500 pulseaudio[3661]: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo becomes idle, timeout in 5 seconds.
Jul  9 07:57:11 w500 pulseaudio[3661]: core.c: Hmm, no streams around, trying to vacuum.
Jul  9 07:57:11 w500 pulseaudio[3661]: sink-input.c: Freeing input 3 "Event Sound"
Jul  9 07:57:16 w500 pulseaudio[3661]: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_1b.0.analog-stereo idle for too long, suspending ...
Jul  9 07:57:16 w500 pulseaudio[3661]: sink.c: Suspend cause of sink alsa_output.pci-0000_00_1b.0.analog-stereo is 0x0004, suspending
Jul  9 07:57:16 w500 pulseaudio[3661]: alsa-sink.c: Device suspended...
Jul  9 07:57:16 w500 pulseaudio[3661]: reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio0 changed: not busy
Jul  9 07:57:16 w500 pulseaudio[3661]: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
```

Also, sound works fine in other apps.

---

### Post by Blue Beard on 2010-07-09
I had very garbled sound and sometimes no sound in Skype.

I discovered the automatic volume control option in Skype was reseting my microphone level to max which was causing the failures.

I unchecked the Skype option and now all is well.

---

### Post by jlward4th on 2010-07-09
Thanks.  I tried that with no luck.  For no I've just uninstalled pulseaudio.

---

### Post by cariboo on 2010-07-09
Removing pulse defeats the purpose of running a testing version.

---

### Post by Yellow Pasque on 2010-07-10
Maybe this will help: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by mdurham on 2010-07-12
> **cariboo907 said:**
> Removing pulse defeats the purpose of running a testing version.
Pulse was 'tested' in 10.04 and it's still a mess. So, I don't see testing it in 10.10 will make any difference.
Cheers, Mike

---

### Post by psyke83 on 2010-07-12
> **Temüjin said:**
> Maybe this will help: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

Ubuntu's ALSA libraries are patched to automatically detect a running PulseAudio server, and automatically use the configuration from /usr/share/alsa/pulse-alsa.conf (which also defines "pulse" as the default ctl and pcm device). Check it yourself if you don't believe me.

Instructing people to create their own /etc/asound.conf is unnecessary, and will cause conflicts when PulseAudio is uninstalled or unavailable.

---

### Post by Yellow Pasque on 2010-07-12
> **psyke83 said:**
> Ubuntu's ALSA libraries are patched to automatically detect a running PulseAudio server, and automatically use the configuration from /usr/share/alsa/pulse-alsa.conf (which also defines "pulse" as the default ctl and pcm device). Check it yourself if you don't believe me.

Instructing people to create their own /etc/asound.conf is unnecessary, and will cause conflicts when PulseAudio is uninstalled or unavailable.
Hmm, I guess that would explain why my Lucid VM worked like that out of the box. From now on, I'll only use that link for people using upstream (non-Ubuntu) ALSA. That was good to know. Thanks.

---

### Post by psyke83 on 2010-07-12
> **Temüjin said:**
> Hmm, I guess that would explain why my Lucid VM worked like that out of the box. From now on, I'll only use that link for people using upstream (non-Ubuntu) ALSA. That was good to know. Thanks.

For non-Ubuntu users, this is even better: [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

However, most distributions that ship with PulseAudio already have this integration by default. Not to mention that a lot of the instructions are outdated.

Trying to "fix" PulseAudio by using outdated instructions will most likely cause more problems than it solves. When PulseAudio isn't working (on a distribution with good PulseAudio integration, which in the case of Ubuntu means any release post-Intrepid Ibex), it's usually an ALSA issue or not related to PulseAudio at all.

---

