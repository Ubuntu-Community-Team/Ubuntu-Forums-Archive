---
title: "Sound, Creative Audigy SE [ ca0106 ]. No microphone with ALSA 1.0.10-4ubuntu4."
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by 7zeal on 2006-07-26
Since the ca0106 microphone/line-in volume tab (Input, or Capture) is added in ALSA 1.0.11, I tried to compile both ALSA 1.0.11 and 1.0.12rc1 (alsa-drivers) - same behaviour.
(Sound IS working flawlessly in the latest alsa, 1.0.10-4ubuntu4 that's found in the repositories.
I removed alsa-base, alsa-modules-$(uname -r) and alsa-utils ..

Then I installed the new alsa-drivers, alsa-lib (which replaced some of libasound2's files, but that's not a problem, apt-get install --reinstall is always there : since libasound2 can't be uninstalled without uninstalling amarok, vlc and a whole lot of other apps) and alsa-utils, in this order.
My kernel is 2.6.15-26-386, Dapper Drake 6.06.
Alsa-drivers was compiled using ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=ca0106 --with-oss=yes  (tried --with-debug=full, but there is still no feedback anywhere about alsa - in /var/log/dmesg, /var/log/messages, nowhere).
Then I ran make, make install, and then installed alsa-lib and alsa-utils.

Restarted the system, alsasound service is started properly and without error, could do a restart on it and no error would pop up.
lsmod says snd_ca0106 is there... 
modprobe snd_ca0106, works, doesn't return anything.

My modules with alsa 1.0.10-4ubuntu4 were loaded as follows:

snd_seq_dummy           3972  0
snd_seq_oss            32128  0
snd_seq_midi            9760  0
snd_seq_midi_event      6912  2 snd_seq_oss,snd_seq_midi
snd_seq                51856  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_ca0106             31652  3
snd_rawmidi            24480  2 snd_seq_midi,snd_ca0106
snd_seq_device          8588  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_ac97_codec         84128  1 snd_ca0106
snd_pcm_oss            54048  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                88712  4 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              23940  3 snd_seq,snd_pcm
snd                    57836  17 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event,snd_seq,snd_ca0106,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

With the new drivers, kmix loaded and did show the Capture tab too, with volumes for line-in and microphone and others, and though all volumes were at max in Playback, I couldn't hear sound. Everything played, but no sound outputted to speakers. No error reported.. nothing
Did an alsaconfig too, but it didn't help.
Ran the ./snddevices too which created some stuff in /dev/snd, still no sound,even after restart, same behaviour.

What should I do to make the latest alsa work as installed from source?

Thanks in advance,
Dan

---

### Post by jbaloul on 2006-07-26
Same problem here:
```

0000:00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

```

My guess is the new 2.6.15-26 doesn't play nice with Alsa

any info would be apreciated...

--
Jacob
[http://howtoforums.net](http://howtoforums.net)

---

