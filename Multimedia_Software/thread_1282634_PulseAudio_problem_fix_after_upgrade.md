---
title: "PulseAudio problem fix after upgrade?"
date: 2009-10-04
forum: Multimedia Software
---

### Post by NickD-NLUG on 2009-10-04
Hi,

A friend recently upgraded their Jaunty installation, and sound failed to work... again ;)  They couldn't get any sound out of their machine, put from the command line using "play" as root worked.

My fix process was:

add the user back into the "audio" group using the "vigr" and "vigr -s" commands

sudo apt-get --reinstall install pulseaudio

Then for their user:

rm -f ~/.pulse/*
rm -rf /tmp/pulse-*

get the user to logout and log back in.

Yes, I didn't quite know what the problem was... and I'm not completely sure that all of the above steps are required. But I looked at permissions, hoped for some obvious clue from comparing "strace play soundfile.wav" as their user and the root user... but in the end it came down to just randomly punching pulseaudio until it decided to work again. This is posted to the forum in case anyone else has the same issue.

---

