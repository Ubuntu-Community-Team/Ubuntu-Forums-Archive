---
title: "ffmpeg on ubuntu 8.10 w/ enable-shared"
date: 2009-02-20
forum: Multimedia Software
---

### Post by darkzerox on 2009-02-20
So, I've recompiled ffmpeg about a dozen times now, but I just can't seem to get it to work with --enable-shared. I get this error message:

> ffmpeg: error while loading shared libraries: libavcodec.so.52: cannot open shared object file: No such file or directory

Any idea why? Or where can I get libavcodec52? I can't seem to find it.

Oh..I'm using a fresh svn checkout of ffmpeg...whatever version that is.

---

### Post by FakeOutdoorsman on 2009-02-20
Why do you want to --enable-shared?  What are your FFmpeg ./configuration options?  Did you run "sudo ldconfig" after installing FFmpeg to update the links to the new shared libraries?  I get an error:
```
error while loading shared libraries: libavfilter.so.0: cannot open shared object file: No such file or directory
```
if I don't run "sudo ldconfig" after installing FFmpeg with --enable-shared.  After running ldconfig FFmpeg runs normally.

Using the following (this is just a test configuration and doesn't reflect what I would normally use):
```
./configure --disable-debug --enable-postproc --enable-avfilter --enable-pthreads --enable-libtheora --enable-x11grab --enable-libmp3lame --enable-libx264 --enable-libfaac --enable-libfaad --enable-gpl --enable-shared
```

I get:
```
/usr/local/lib/libavcodec.so
/usr/local/lib/libavcodec.so.52
/usr/local/lib/libavcodec.so.52.18.0
```

---

### Post by darkzerox on 2009-02-21
I need --enable-shared so that I can compile OpenCV with ffmpeg support. I'm not too concerned about all the other filters and options right now, I just need something that works.

I recompiled ffmpeg with the configuration you suggested. Indeed, I got the same error as you (about libavfilter) after compiling. But even after running "sudo ldconfig" it gave me the same error again (this is before running "make install"). After running "make install" and "sudo ldconfig" again, it gives me

> ffmpeg: symbol lookup error: /usr/local/lib/libavcodec.so.52: undefined symbol: av_gcd

On the bright side, libavcodec.so.52 exists now. Do you know how I can fix this error though?
---
Scratch that. This fixed it:

```
LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH
```

Is this a permanent fix though? Or will LD_LIBRARY_PATH get reset when I restart my system? Why isn't it looking in /usr/local/lib by default?

---

### Post by FakeOutdoorsman on 2009-02-21
I apologize for giving you such a bad configuration line.  I wasn't really suggesting that you use it, but I used it because I was trying to debug another user's setup at the same time.

I recommend uninstalling FFmpeg and following this guide:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

You will of course need to add *--enable-shared* and then run "sudo ldconfig" as the last step.

Also, paste the output of:
```
dpkg --get-selections | grep -E ^libav\|libsw
```

---

### Post by FakeOutdoorsman on 2009-02-21
I was able to duplicate your error:
```
ffmpeg: symbol lookup error: /usr/local/lib/libavcodec.so.52: undefined symbol: av_gcd
```
If **libavcodec51** and **libavutil49** are installed when using FFmpeg with "--enable-shared".  Once those packages were removed FFmpeg worked fine.

---

### Post by darkzerox on 2009-02-21
Ah, I think you missed my edit :)

I need libavcodec51. It may have been libavutil49 that was the problem. Regardless, pointing ffmpeg to the new libraries (as I mentioned in my last post), fixes the issue.

Thank you very much for your help!

Edit: libavutil49 was the problem. That EXPORT trick seems to be temporary (yes, I have no idea what I'm doing). But ffmpeg (or opencv?) complains if you uninstall libavcodec51, so I recommend you keep it.

---

### Post by jed64 on 2009-09-17
It's generally not a good idea to set LD_LIBRARY_PATH and is **not** a permanent fix: [http://linuxmafia.com/faq/Admin/ld-lib-path.html](http://linuxmafia.com/faq/Admin/ld-lib-path.html)

Instead you should probably add /usr/local/lib to /etc/ld.so.conf (I added it on a new line) and run ldconfig again. This page explains that a little more in the 4th paragraph: [URL="http://www.dwheeler.com/secure-programs/Secure-Programs-HOWTO/dlls.html"]http://www.dwheeler.com/secure-programs/Secure-Programs-HOWTO/dlls.html
[/URL]
That cleared the error *ffmpeg: error while loading shared libraries: libavfilter.so.0: cannot open shared object file: No such file or directory* for me.

---

