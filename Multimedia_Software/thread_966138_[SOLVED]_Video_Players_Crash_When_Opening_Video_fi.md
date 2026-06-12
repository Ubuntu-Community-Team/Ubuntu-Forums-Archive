---
title: "[SOLVED] Video Players Crash When Opening Video files"
date: 2008-11-01
forum: Multimedia Software
---

### Post by rudihawk on 2008-11-01
Hi All
I upgraded to Intrepid Ibex and have installed the ubuntu-restricted-extra's package.
However when I try and play video files e.g .wmv's, .flv's .avi's etc totem and vlc bother crash.
Output from terminal for totem crash:
```
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 190 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Here is the output from terminal when vlc crashes:
```

QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84

```

Does anyone have any idea on how I can solve this problem. I have installed all the updates(except the kernel updates) that were avaliable to me this morning.

Much appreciated.
All the audio works, can play audio files(music) through both vlc and totem.

---

### Post by Maqz447 on 2008-11-01
Do you have desktop effects enabled? Try selecting no desktop effects in System -> Preferences -> Appearance -> Visual effects and see if it works then. If so, you have the same problem I had after installing Intrepid (I'm sure you do, I had the exact same error messages).

I fixed it by following these suggestions:

[http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html](http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html)  

It works perfectly for me, but beware that there might be a performance hit on older/slower machines, because you're turning off 2D acceleration by your GPU, leaving it to the CPU. I have a 1.86 GHz C2D and I don't notice any performance problems though.

The only thing that doesn't work for me is the gecko mplayer plugin, where I get sound but no video. About to start a thread on that...

---

### Post by rudihawk on 2008-11-01
I don't think it will be a problem with performance i have E6600 (2.4Ghz Core2 Duo).

Thanks :)

---

