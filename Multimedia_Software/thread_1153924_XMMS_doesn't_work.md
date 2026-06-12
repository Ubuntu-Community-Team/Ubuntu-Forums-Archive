---
title: "XMMS doesn't work"
date: 2009-05-09
forum: Multimedia Software
---

### Post by zurih on 2009-05-09
Hey,
This is the first time I tried to open XMMS, and it doesn't seem to work.
This is error I'm getting when I try to run xmms2d from terminal:

```
 INFO: ../src/xmms/log.c:36: Initialized logging system :)
ERROR: ../src/xmms/ipc.c:938: Couldn't setup IPC listening on 'unix:///tmp/xmms-ipc-zurih'.
FATAL: ../src/xmms/main.c:484: IPC failed to init!
```

In ~/.cache/xmms2/xmms2d.log I see this:

```

--- Starting new xmms2d ---
 INFO: ../src/xmms/log.c:36: Initialized logging system :)
 INFO: ../src/xmms/ipc.c:950: IPC listening on 'unix:///tmp/xmms-ipc-zurih'.
 INFO: ../src/xmms/main.c:507: Using output plugin: alsa
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (0) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (4) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (4) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (4) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (4) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (4) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (4) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (4) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (4) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (4) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (4) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (4) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (4) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (4) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (4) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (12) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (12) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (12) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (12) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (12) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (12) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (12) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (12) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (12) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (12) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (12) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (12) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (12) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (12) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (16) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (16) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (16) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (16) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (16) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (16) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (16) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (16) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (16) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (16) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (16) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (16) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (16) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:266: Sample format (16) not available for playback.
ERROR: ../src/plugins/alsa/alsa.c:549: Failed to find mixer element
```

Any idea?

Thanks

---

### Post by zurih on 2009-05-13
bump

---

### Post by zurih on 2009-05-15
another bump

---

### Post by Defrector on 2009-10-09
I was able to fix the mixer problem by setting the output plugin to whatever my audio system is. It uses ALSA by default.

For example, for using pulseaudio I ran the following once:
```
xmms2 config output.plugin pulse
```

This put the output plugin key into the xmms config file. Depending on the system you use for sound you may have to put something else in. I still got the IPC error, as that is apparently unrelated. The audio errors cleared up. Note that if you use pulse you need to install the xmms2-plugin-pulse package. If you use something else, do a search in Synaptic for xmms2-plugin and a bunch should show up.

Apparently the recommended way to start xmms2d is using:
```
xmms2-launcher
```

The output of the launcher has been less helpful.

To get rid of the IPC socket error, you need to remove a socket file in /tmp.  It generally starts with ```
xmms-ipc-
``` and then your username. After removing that and fixing your audio, try launching again.

Here is where I found the clue:
[http://forum.soft32.com/linux/Bug-510638-XMMS2-fails-startup-default-IPC-Unix-socket-exist-ftopict473805.html](http://forum.soft32.com/linux/Bug-510638-XMMS2-fails-startup-default-IPC-Unix-socket-exist-ftopict473805.html)

---

