---
title: "PulseAudio remote playback problems (sound Ok, video hangs)"
date: 2012-09-17
forum: Multimedia Software
---

### Post by aps2012 on 2012-09-17
Hi all,

I have two Ubuntu boxes, both 10.10 on a local 1GB LAN.  I have pulseaudio installed and running on both, one configured as a server (where the speakers are plugged in) and one as the client. Both are configured correctly, sound is transmitted from one to the other normally (e.g. system sounds, audio applications). However, any time I play video (using Totem), or any time images are being synchronised to sound, the video locks up after a very short while while the sound continues to play.

Here are the things I've noticed about my setup:

[LIST=1]
[*] The sound will only continue to play by itself for a while (not more than 10 or 20 seconds at best. After that, the sound stops as well.
[*]It definitely seems to be a video synchronisation problem, as in acknowledgements from transmitted audio frames from client to server not getting back in time to synchronise the next frame of video. HD videos will lock up almost instantly whilst old low-resolution encoded 4:3 videos may play for a while.
[*] No matter how I tweak [FONT=Courier New]/etc/init.d/pulse/daemon.conf[/FONT] and restart, on both client *and* server, the amount of physical network bandwidth being used for sound transmission never changes. A network monitor on both the client and the server show between 190KB/sec and 230KB/sec bandwidth being used for sound, even if I set the [FONT=Courier New]default-sample-rate[/FONT] parameter to (e.g.) 4KHz and the [FONT=Courier New]resample-method[/FONT] parameter to *ffmpeg*.
[*]I've tried increasing the priority to realtime to give it more CPU time. I used the "pulse-rt group" method and added myself to the group on both client and server. However, if it's a network saturation problem (as I suspect) then this won't help anyway.
[*]I get a lot of messages in [FONT=Courier New]/var/log/syslog[/FONT] that look like the following on both the client and server:```
pulseaudio[1879]: ratelimit.c: 1035 events suppressed
```
[*]I also get a lot of messages in [FONT=Courier New]/var/log/syslog[/FONT] that look list this on both the client and server:```
pulseaudio[1879]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 1 is less than avail 18.
pulseaudio[1879]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
pulseaudio[1879]: alsa-util.c: snd_pcm_dump(): <lots of dump information follows>.

```
[/LIST]
    In particular, does anybody know why (3) is happening, and how I can reduce the amount of bandwidth pulseaudio is using for sound transmission?

Of course, if anybody knows of a solution to this problem then that would be Ok has well :-)

Thanks in advance.

---

### Post by baltoche on 2012-10-15
Hello,

I have the exact same problem.
Did you manage to fix it after all?

Thanks.

---

### Post by baltoche on 2012-10-15
I managed to fix it after reading this thread
[https://bbs.archlinux.org/viewtopic.php?id=146287](https://bbs.archlinux.org/viewtopic.php?id=146287)

---

