---
title: "kino/avidemux wont accept my .ogg files"
date: 2007-12-29
forum: Multimedia Production
---

### Post by akimatsu123 on 2007-12-29
i recorded my screen with recordMyDesktop that is available from the synaptic repositories. 

i have tried to import these into kino and avidemux, but neither will import the file. 

kino says:

```
"/home/akihiro/Videos/demo/cool.ogg" is not a DV file. Do you want to import it?
```

and when i click yes, it says:

```
Failed to load media file "/home/akihiro/Videos/demo/video.ogg.dv"
```

avidemux says:

```
Attempt to open /home/user/Videos/demo/video.ogg failed!
```

and then

```
Could not open file
```

how do i get this working? maybe im missing a gstreamer plugin or sth? i can watch the .ogg files fine. i juts cant import them :S

what do i do? thanks for your help

---

### Post by akimatsu123 on 2007-12-30
never mind got it working. 

[http://packages.ubuntu.com/feisty/graphics/kino](http://packages.ubuntu.com/feisty/graphics/kino) 

installed some packages (i suspect it's the last one vorbis-tools) and i was able to import :D

---

