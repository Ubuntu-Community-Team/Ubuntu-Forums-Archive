---
title: "Amarok starts fast forwarding randomly"
date: 2009-04-24
forum: Multimedia Software
---

### Post by letired on 2009-04-24
Firstly, this may not be amarok-related. I've experienced it in amarok 2.0.2, and again after downgrade to 1.4.10. I haven't been able to reproduce the problem, however.
What happens is that sometime after about 1 minute of playback, the track being played starts to fast-forward. It's not like regular fast forward though - sound quality drops and the track is played faster for a while, and at this point I usually just kill the process. It seems to be happening to the first song played after boot only.
Killing pulseaudio or amarok naturally shuts off the sound, and when amarok is restarted, all is well.
The problem seems to have come with the upgrade from 8.10 to 9.04.

Any ideas?

---

### Post by markbuntu on 2009-04-24
In a terminal stop pulseaudio and start it again in verbose mode

killall pulseaudio

pulseaudio -vvv

Start amarok and play something

copy the output from the terminal and file a bug report at launchpad against pulseaudio. There may already be a bug report on this but you can add your two cents.

---

### Post by letired on 2009-04-25
> **markbuntu said:**
> In a terminal stop pulseaudio and start it again in verbose mode

killall pulseaudio

pulseaudio -vvv

Start amarok and play something

copy the output from the terminal and file a bug report at launchpad against pulseaudio. There may already be a bug report on this but you can add your two cents.

I've been looking at the output of said command for a while now, but even when I managed to catch the random speed-up, there was nothing to tell me what had happened, the pulseaudio output looks fairly consistent. Maybe it isn't pulseaudio?
Another, possibly related, problem is that youtube videos are suddenly screwed up as well, the audio remains fine but the video keeps speeding up and slowing down. That's prolly flash-related though.

..Christ. Next time I'll think twice about typing dist-upgrade.

---

### Post by letired on 2009-04-26
> **letired said:**
> I've been looking at the output of said command for a while now, but even when I managed to catch the random speed-up, there was nothing to tell me what had happened, the pulseaudio output looks fairly consistent. Maybe it isn't pulseaudio?
Another, possibly related, problem is that youtube videos are suddenly screwed up as well, the audio remains fine but the video keeps speeding up and slowing down. That's prolly flash-related though.

..Christ. Next time I'll think twice about typing dist-upgrade.

Bump. I'm currently experiencing problems with all kinds of multimedia applications.
Youtube/Flash - Speeds up video, slows down video
AmaroK - speeds up audio
MPlayer - Loses audio randomly, it's off for a second, then on, then off etc.
VLC - Same as MPlayer + crashing very often.
Killing pulseaudio, then the app, seems to stabilize the system but not fully so it might just be placebo. However, the more sound sources I have running at the same time, the more destabilized it becomes. MPlayer lags slightly on every action (browsing web pages, opening tabs etc) in Firefox.

I cannot find anything worth copying into a bug report from the pulseaudio output, unless ~80ms latency is of any concern. I'm messing around with the volume controls and switching between alsa & OSS mixers and the sound problem keeps coming back. Again, the pulseaudio output looks insignificant.

---

### Post by ubuser_7 on 2009-04-28
I am facing the exact same problems. Amarok (both 2, 1.4) speed up the playback. Even regular playback pauses randomly. Flash sound works fine, while the video speeds up/slows down (Although Flash is more stable for me now).

This started after the upgrade from Intrepid to Jaunty.

---

### Post by markbuntu on 2009-04-28
Look in the messages log. Are you getting meessages like this?

```

Apr 24 20:35:19 mark-jaunty-desktop pulseaudio[3835]: alsa-sink.c: Increasing wakeup watermark to 45.99 ms
Apr 24 20:35:19 mark-jaunty-desktop pulseaudio[3835]: alsa-source.c: Increasing minimal latency to 46.00 ms
Apr 24 20:35:19 mark-jaunty-desktop pulseaudio[3835]: alsa-source.c: Increasing minimal latency to 26.00 ms
Apr 24 20:35:19 mark-jaunty-desktop pulseaudio[3835]: alsa-sink.c: Increasing wakeup watermark to 15.99 ms
Apr 24 20:35:19 mark-jaunty-desktop pulseaudio[3835]: alsa-sink.c: Increasing wakeup watermark to 35.99 ms
Apr 24 20:35:19 mark-jaunty-desktop pulseaudio[3835]: alsa-source.c: Increasing minimal latency to 56.00 ms
Apr 24 20:35:21 mark-jaunty-desktop pulseaudio[3835]: ratelimit.c: 23 events suppressed
Apr 24 20:35:28 mark-jaunty-desktop pulseaudio[3835]: ratelimit.c: 16 events suppressed
Apr 24 20:35:41 mark-jaunty-desktop pulseaudio[3835]: alsa-source.c: Increasing wakeup watermark to 36.00 ms
Apr 24 20:35:41 mark-jaunty-desktop pulseaudio[3835]: alsa-sink.c: Increasing minimal latency to 56.00 ms
Apr 24 20:35:44 mark-jaunty-desktop pulseaudio[3835]: ratelimit.c: 19 events suppressed
Apr 24 20:35:49 mark-jaunty-desktop pulseaudio[3835]: ratelimit.c: 17 events suppressed
Apr 24 20:37:15 mark-jaunty-desktop pulseaudio[3835]: alsa-sink.c: Increasing minimal latency to 66.00 ms
Apr 24 20:37:15 mark-jaunty-desktop pulseaudio[3835]: alsa-source.c: Increasing wakeup watermark to 45.99 ms
Apr 24 20:37:15 mark-jaunty-desktop pulseaudio[3835]: alsa-source.c: Increasing minimal latency to 56.00 ms

```

---

### Post by letired on 2009-04-29
> **markbuntu said:**
> Look in the messages log. Are you getting meessages like this?
Can't find anything like that in /var/log/messages - the only related stuff is this:
```
Apr 28 12:20:54 mkn-laptop pulseaudio[6363]: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
Apr 28 12:20:54 mkn-laptop pulseaudio[6363]: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
Apr 28 12:20:54 mkn-laptop pulseaudio[6363]: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
```
The above is printed on boot or when starting pulseaudio - but not every time, strangely(?).
Here's what pulseaudio is doing when I'm getting heavy lags in audio playback using MPlayer in Firefox for a .wma stream:
```
I: resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
I: resampler.c: Using resampler 'copy'
I: resampler.c: Using float32le as working format.
I: sink-input.c: Created input 9 "ALSA Playback" on combined with sample spec float32le 2ch 44100Hz and channel map front-left,front-right
I: protocol-native.c: Requested tlength=5944.31 ms, minreq=23.22 ms
I: protocol-native.c: Final latency 5967.53 ms = 5897.87 ms + 2*23.22 ms + 23.22 ms
I: module-combine.c: [combined] avg total latency is 79.78 msec.
I: module-combine.c: [combined] target latency is 79.78 msec.
I: module-combine.c: [Simultaneous output on HDA Intel - ALC268 Analog] new rate is 44100 Hz; ratio is 1.000; latency is 79780 usec.
I: sink-input.c: Freeing input 9 "ALSA Playback"
I: module-stream-restore.c: Restoring device for stream sink-input-by-application-name:ALSA plug-in [firefox (deleted)].
I: module-stream-restore.c: Restoring volume for sink input sink-input-by-application-name:ALSA plug-in [firefox (deleted)].
```
This happens over and over, almost once per "lag" it seems.

edit: I'd like to help out by posting bug reports, but I'm not sure how to detect the bug, or what output would be helpful.

---

### Post by ubuser_7 on 2009-04-29
I couldnt find anything useful in my logs either. Did you start pulseaudio with a debug/verbose mode?

---

### Post by markbuntu on 2009-04-29
Try this. Make yourself and root members of the following groups

pulse
pulse-rt
pulse-access

That should fix the first set of messages.

float32le?

did you set that?

Simultaneous output is also giving me problems and I filed a bug report here

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/368941](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/368941)

Daniel Chen has asked me to try a patched kernel to see it it resolves this problem. I am not using that Jaunty install right now but will be sometime soon and will give it a try then. 

In the meantime you could give it a try and let Daniel know if it fixed your problem by adding a comment at the bug report above.

[http://kernel.ubuntu.com/~dtchen/](http://kernel.ubuntu.com/~dtchen/) ?

---

### Post by IB1Dance on 2009-06-16
Any news on this Bug.Since I upgraded to Jaunty Amarok has been acting weird.Speeding up mp3's,skipping,volume going off then back on? .

---

### Post by letired on 2009-06-18
> **IB1Dance said:**
> Any news on this Bug.Since I upgraded to Jaunty Amarok has been acting weird.Speeding up mp3's,skipping,volume going off then back on? .

My amarok issues have since receded and want away completely, which is strange because I'm pretty sure it "just happened". The .flv issues persist, however, in web browsers as well as when playing downloaded .flv's in any movie player. killall firefox &#8594; killall pulseaudio &#8594; firefox and reload the vid usually (95% of the time) helps.

---

### Post by ferrouswheel on 2009-09-03
I get the same thing with amarok 1.4 in Jaunty. I thought it was some weirdness with playing music on a samba share, but I get the same thing with internet streams too. Are you guys use network sources when you get the problem?

(It only happens occassionally for me, and stop and starting a few times seems to fix it temporarily).

---

