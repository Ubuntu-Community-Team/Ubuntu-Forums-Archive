---
title: "segfault with window media file (wma/wmv)"
date: 2015-04-16
forum: Multimedia Software
---

### Post by vincent27 on 2015-04-16
Hello,
since an update, I can't read windows media files anymore (I was able to read them before). Every times I try to read a wma or wmv file,
 the software (banshee, vlc, ...) crash.
Banshee gives me this log with banshee --debug

```

...
(Banshee:2799): GStreamer-CRITICAL **: gst_structure_new_empty: assertion 'gst_structure_validate_name (name)' failed
[1 Debug 19:47:55.537] (libbanshee:player) [gapless] Triggering track-change signal

Native stacktrace:

    banshee() [0x8105b4a]
    banshee() [0x806a278]
    [0xb771440c]
    /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstlibav.so(+0x18f3a) [0xa53bdf3a]

Debug info from gdb:

Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Opération non permise.
No threads.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```

and vlc stacktrace after the segfault is :
```

[Switching to Thread 0xac3ffb40 (LWP 3963)]
0xac0564ef in ?? () from /usr/lib/vlc/plugins/codec/libavcodec_plugin.so

```

Is there a way to fix this problem. I use Ubuntu 14.04 and my system is up to date.

Thank you for your awnsers.

---

