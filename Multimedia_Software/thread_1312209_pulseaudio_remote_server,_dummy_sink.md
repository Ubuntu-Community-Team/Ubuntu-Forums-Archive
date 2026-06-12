---
title: "pulseaudio remote server, dummy sink"
date: 2009-11-02
forum: Multimedia Software
---

### Post by felixnine on 2009-11-02
i'm trying to stream audio from my laptop to my media server. both running karmic, pulseaudio 1:0.9.19-0ubuntu4.

if i log in to the server via gdm, the server, sink, and source show up in padevchooser on my laptop. if i log in to the server via ssh and issue 

```
pulseaudio --start
```

all i can see on the server is dummy outputs. i can't for the life of me figure out what's different.

---

