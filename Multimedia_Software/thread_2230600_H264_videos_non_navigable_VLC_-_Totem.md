---
title: "H264 videos non navigable VLC - Totem"
date: 2014-06-20
forum: Multimedia Software
---

### Post by d-lhoest-y on 2014-06-20
Hello ladies and gentlemen.

I have a new issue but I do not know its origin. I have upgraded from 13.10 to 14.04 but do not remember if I tried playing a 720p video since. 

Anyway, what is happening is that those movies play fine but if I am trying to navigate, jump to specific time, go forward, etc, VLC spikes to 30 - 40% of CPU, the image goes black, no sound and I can have to wait up to 10 minutes to have the movie most of the time without sound. With Totem, it is the same problem.

I did go around the internet looking for a solution. I tried reverting from avconv to ffmpeg (but honestly, who knows why) reinstalled my drivers, reinstalled VLC, reset VLC options, reinstalled unbuntu-restricted-extra, xorg-server, ...

Nothing worked.

Any help is appreciated indeed!

Specs : Dell Inspiron 14Z, intel i5, 8Gb ram, intel graphic card, Ubuntu 14.04 64bits
Some interesting outputs : 
```
/usr/lib/nux/unity_support_test -pOpenGL vendor string:   Intel Open Source Technology Center[COLOR=#000000]OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string:  3.0 Mesa 10.1.3

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes
 [/COLOR][COLOR=#000000]Unity 3D supported:       yes[/COLOR]
```

When navigating through the movie with VLC : 

```
[h264 @ 0x7fec8624b040] mmco: unref short failure
```

---

### Post by gordan-vrbanec-vepar on 2014-06-20
I had the same problem not long before, in Ubuntu 13.10.
I don't know the details, but it probably had something to do with the file itself rather than the OS or VLC...
I "fixed" it by converting that particular file to another format. Then it played nicely...

Now, if you're having this problem with all the files, and indeed another player, it's a different issue.
It might be your graphic card. I haven't known Intel cards to play well with Linux. Or windows for that matter...

If i experience this sort of a system wide bug, the first thing i do is try to revert to a previous driver/codec/whatever, and that usually works...
You wrote that you upgraded to 14.10. The upgrade might have had something to do with it. Did you just upgrade the OS, or did you reinstall it from scratch?
Because something might not be compatible with the new OS version that you previously had installed.

Try some older VLC version or driver versions and see if that does the trick.

---

### Post by d-lhoest-y on 2014-06-21
****. You are right, I do not know what I wouldn't even try another file. Just tested with several other movies and it works absolutely wonders!

Thank you for your help :)

---

### Post by gordan-vrbanec-vepar on 2014-06-21
Glad to be of help! :)

---

