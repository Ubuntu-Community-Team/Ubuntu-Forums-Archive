---
title: "mdb flash conflict"
date: 2010-01-30
forum: Multimedia Software
---

### Post by yekibud on 2010-01-30
Whether or not I configure mdb.conf to use alsa or pulse, whenever I run flash audio (e.g. a hulu video), my MDB clients (GMPC, sonata) produce the following error: "problems opening audio device."  I've googled and checked the forums, found some similar posts, but nothing described exactly this way, and none of the solutions worked.

Any help?

Running Karmic...

---

### Post by qball on 2010-02-01
What is MDB? 

Your soundcard only supports playing one audio stream at the same time. To work around this you need a software audio mixer, like dmix or pulseaudio.
But ALL programs need to use this same mixer, your music program and flash.

---

### Post by yekibud on 2010-02-01
Yeah, um, can you help me configure my Access database to work with Flash audio?

What a jerk (me).  I meant MPD - Music Player Daemon.

So event if I've got both Flash and MPD using Pusleaudio, I still have to kill Firefox if, for example, I've got my MPD client (GMPC) running and start/pause a Hulu video.  Interestingly, using a non-MPD audio player, like Rhythmbox, does not conflict.

Any thoughts?  Thanks.

---

### Post by qball on 2010-02-01
This is not trivial.  as pulseaudio daemon normally runs per user session.
And mpd runs as it own user on startup.

One solution is to run mpd inside your user session.

If you have both flash and mpd using pulseaudio, everything should work fine..  if it doesn't then they are not both using pulse.

---

### Post by yekibud on 2010-02-07
Thanks, qball.  I tried troubleshooting with the assumption that everything should be fine if both Flash and MPD were using pulse.  And, sure enough, MPD wasn't configured to use pulse correctly.  The following solution from [the pulse audio wiki]("http://mpd.wikia.com/wiki/PulseAudio") got everything working correctly:

```
An alternate solution for fixing access rights

This is required in Ubuntu Jaunty.
Another solution, found on [Ubuntu Forums] is to adjust the network access permissions using the paprefs tool. On Ubuntu:

  $ sudo aptitude install paprefs
  $ paprefs

Select the following settings:

    * Enable network access to local sound devices
    * Don't require authentication 

Set mpd.conf as follows and restart mpd

audio_output {
	type    "pulse"
	name    "My MPD PulseAudio Output"
}

```

---

