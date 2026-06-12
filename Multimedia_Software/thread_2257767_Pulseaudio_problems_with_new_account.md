---
title: "Pulseaudio problems with new account"
date: 2014-12-22
forum: Multimedia Software
---

### Post by the_one(2) on 2014-12-22
Hello everybody!

I was trying to get mpd working on my computer but it just wouldn't work. After lots of googling I tried finding the simplest root to the problem. I sudo'd to mpd and tried
$ pulseaudio 
which failed without reporting any errors. It reported a couple of warnings which I believe are irrelevant but you can see below. No amount of -vvvv shed any light on the situation.
I've tried adding mpd to the groups pulse and pulse-access. It was already a member of audio

The output:
W: [pulseaudio] core-util.c: Failed to open configuration file '/home/user/.config/pulse//daemon.conf': Permission denied
W: [pulseaudio] daemon-conf.c: Failed to open configuration file: Permission denied

I'm a bit confused as to why it tries to open user's configuration files but that shouldn't matter right?

---

