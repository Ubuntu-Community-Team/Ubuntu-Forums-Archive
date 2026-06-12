---
title: "Possible to get sound from games / anything while backend is running?"
date: 2010-03-05
forum: Mythbuntu
---

### Post by eljeffe on 2010-03-05
I have a combined frontend-backend system. I would love to be able to play games on this machine while the backend is running. I have my audio going to line in;  therefor I guess that I need to use /dev/dsp for shows to be recorded. At least that was the only way I could get recording to work properly.

Does this mean that the backend "traps" all sounds? Can I use a backend system for games, browsing and hearing youtube type videos?

Thanks in advance.

---

### Post by ian dobson on 2010-03-06
Hi,

Mythtv doesn't like pulseaudio and tries to disable it when it's running. I think there's a command line option to stop the mythbackend process from stopping pulseaudio, but I can't check it out at the moment. Maybe google mythtv/pulseaudio.

Regards
Ian Dobson

---

### Post by eljeffe on 2010-03-09
Thanks for the quick suggestion. I'll give it a try.

---

### Post by gwagchunks on 2010-03-11
Recently the kids were using youtube to find our how to complete a supermario level, I started up the box and while watching tv, I got supermario music all over the program I was watching! Could still hear both the tv audio and youtube! Not using sp/dif or anything like that, just the default audio settings.

---

