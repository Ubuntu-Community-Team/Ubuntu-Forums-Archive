---
title: "PulseAudio: cross-platform?"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by sedi911 on 2008-03-03
So here's my situation:

I have 3 computers running Vista or Windows XP in my house. They all have music on them, and I want to leave the music on these computers. However, I have an old computer running Gutsy, and I want to be able to redirect the sound through my network to this computer, which will play through the central stereo.

From what I can tell, PulseAudio should be able to solve this problem. However, I downloaded the Windows binaries, and when I run ```
pulseaudio -nC
``` in the Windows shell, I get the following errors:

```
W: pulsecore/random.c: failed to get proper entropy. Falling back to seedin
h current time.
W: pulsecore/core-util.c: secure directory creation not supported on Win32.
W: pulsecore/core.c: failed to allocate shared memory pool. Falling back to
rmal memory pool.
W: pulsecore/core-util.c: WARNING: Only sockets can be made non-blocking!
W: pulse/mainloop.c: WARNING: cannot monitor non-socket file descriptors.
W: pulsecore/core-util.c: WARNING: Only sockets can be made non-blocking!
W: pulse/mainloop.c: WARNING: cannot monitor non-socket file descriptors.
```

I was under the impression that PulseAudio was cross-platform, but I'm relatively new to all this, so I could be wrong. There seems to be a severe lack of documentation in this area. So I guess my question is this: Is PulseAudio the solution to my situation? If not, is there another cross-platform sound server that I can use?

Eddie

---

