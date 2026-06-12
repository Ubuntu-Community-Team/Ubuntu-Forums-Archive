---
title: "Pulseaudio, mpd and ordinary sound sources in 9.04"
date: 2009-05-04
forum: Multimedia Software
---

### Post by PureW on 2009-05-04
Hello there

I have some trouble with playing sound through mpd at the same time as listening to other sound sources. This is Ubuntu 9.04, fresh install of 9.04RC and then updated.

Previously I could listen to mpd (which, should connect to Pulseaudio as the computer starts up) but not hear anything from other sources, for example, youtube.

Then I followed a few tips, guides and then I could listen to youtube, but not mpd. So the situation was reversed. :(

Now I tested to kill the user-spawned Pulseaudio and start it with "sudo /etc/init.d/mpd start"
```

$ pulseaudio --kill
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
$ sudo /etc/init.d/pulseaudio start
 * PulseAudio configured for per-user sessions
$ sudo /etc/init.d/mpd start
 * Starting Music Player Daemon mpd                                      [ OK ] 
$

```

This made mpd work again but now I can't hear youtube again. And Pulseaudio did not start as system-wide service according to:
```

$ ps -u anders |grep pulse
 5536 ?        00:00:02 pulseaudio

```

Any ideas on how to make mpd play along with pulseaudio and all the other sound sources.

I have tried both alsa and pulse as audio outputs by mpd. But somehow I wonder if it is mpd that is causing the problems since more often than not, it is working and not the flash player.

**UPDATE: I think I know what is wrong. It seems as only one source can connect to pulseaudio. If I kill mpd, and restart pulse, the flashplayer works fine. Why is that? **

---

### Post by PureW on 2009-05-04
It seems as only one source can connect to pulseaudio. If I kill mpd, and restart pulse, the flashplayer works fine. Why is that?

---

### Post by pnutzh4x0r on 2009-05-04
Have you looked at: 

[http://mpd.wikia.com/wiki/PulseAudio]("http://mpd.wikia.com/wiki/PulseAudio")

in particular:

[http://ubuntuforums.org/showthread.php?p=4725592#post4601963]("http://ubuntuforums.org/showthread.php?p=4725592#post4601963")

I've used the paprefs method and that has worked for me.

---

### Post by PureW on 2009-05-04
> **pnutzh4x0r said:**
> Have you looked at: 

[http://mpd.wikia.com/wiki/PulseAudio]("http://mpd.wikia.com/wiki/PulseAudio")

in particular:

[http://ubuntuforums.org/showthread.php?p=4725592#post4601963]("http://ubuntuforums.org/showthread.php?p=4725592#post4601963")

I've used the paprefs method and that has worked for me.

I've read the mpd-wiki several times but never thought that the paprefs-solution would do any difference in 9.04 since it's been around for over a year.

But now I tried it, and after a pulseaudio restart, it seems to have worked. Thank you!

EDIT: I can't find the thank you-button, but thanks again!

---

