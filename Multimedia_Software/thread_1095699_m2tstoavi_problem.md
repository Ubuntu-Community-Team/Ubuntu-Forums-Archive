---
title: "m2tstoavi problem"
date: 2009-03-14
forum: Multimedia Software
---

### Post by chilimac02 on 2009-03-14
I got m2tstoavi to install properly (I think) in Intrepid. I'm trying to execute the command, and get this:

justin@justin-laptop:~/Videos/Movies$ m2tstoavi *
using:
/usr/local/bin/xporthdmv
ldecod: Command not found.
justin@justin-laptop:~/Videos/Movies$ 


What is 'ldecod' and what do I need to do to fix this problem?

---

### Post by cotcot on 2009-03-14
I think that the script installs ldecod and that it did not found it.

I use another instruction working fine with the .mts files from a Canon HF100:

```
mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=1920:1080,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=8000:keyint=15:aspect=16/9:threads=4 00126.MTS -ofps 25 -fps 50 -o 00126.mpg
```

I found it [[COLOR="Red"]here[/COLOR]]("http://blog.mymediasystem.net/avchd/howto-convert-and-write-avchd-mts-to-dvd-on-linux/")

---

### Post by chilimac02 on 2009-03-16
I'll give that a shot later. I use a Sony HDR-SR11 myself... thanks for the info

---

### Post by chilimac02 on 2009-03-17
I ran that script and received some errors:

Skipping frame!
[h264 @ 0x88433b0]PAFF interlacing is not implemented  A-V:0.068 [8054:448]
[h264 @ 0x88433b0]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x88433b0]PAFF interlacing is not implemented  A-V:0.030 [8065:448]
[h264 @ 0x88433b0]illegal short term buffer state detected
[h264 @ 0x88433b0]concealing 7848 DC, 7848 AC, 7848 MV errors
[h264 @ 0x88433b0]PAFF interlacing is not implemented  A-V:0.032 [8063:448]
[h264 @ 0x88433b0]MBAFF + spatial direct mode is not implemented
[h264 @ 0x88433b0]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x88433b0]PAFF interlacing is not implemented  A-V:0.034 [8066:448]
[h264 @ 0x88433b0]MBAFF + spatial direct mode is not implemented
[h264 @ 0x88433b0]concealing 8159 DC, 8159 AC, 8159 MV errors

-Justin

---

### Post by cotcot on 2009-03-17
Then I think you need to get a later version of mplayer through SVN.

[[COLOR="Red"]Her[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1024592")e is a howto. Sorry it is some terminal work.

---

### Post by citybird on 2009-03-27
tried this and got that...

```
:~/Desktop$ locate ldecod
/usr/bin/opldecode
/usr/bin/qpdldecode
/usr/share/man/man1/opldecode.1.gz
/usr/share/man/man1/qpdldecode.1.gz

```

is there a sym link missing somewhere?

---

