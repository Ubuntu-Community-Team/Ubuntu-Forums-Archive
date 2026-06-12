---
title: "Can't use custom xorg.conf"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by pseudonym on 2007-01-14
I'm running the 9746 nvidia driver from nvidia.com on a custom 2.6.19 kernel from kernel.org, Xubuntu Edgy AMD64. Since a recent update to the xserver-xorg-core and xserver-xorg-dev packages I've been unable to start X using my custom xorg.conf file. The message I get is - ```
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x71) [0x480b81]
1: /lib/libc.so.6 [0x2b5385861510]
2: /usr/bin/X(NumMotionEvents+0x12) [0x43e962]
3: /usr/bin/X(CreateConnectionBlock+0x53) [0x4306f3]
4: /usr/bin/X(main+0x658) [0x431238]
5: /lib/libc.so.6(__libc_start_main+0xf4) [0x2b538584e0c4]
6: /usr/bin/X(FontFileCompleteXLFD+0xa1) [0x430339]

Fatal server error:
Caught signal 11.  Server aborting
``` which is a standard cryptic X crash message.

I have a feeling the problem might be related to me not uninstalling the nvidia driver first before this update (I used to do that only when the package xserver-xorg was updated but I guess things are different in Xorg post-7.0).

Uninstalling and reinstalling the driver didn't help by itself. I can start X, but only with a xorg.conf file generated as a result of running ```
sudo dpkg-reconfigure -phigh xserver-xorg

or, right after -

sudo dpkg-reconfigure xserver-xorg
```
to give me a few more config options. But I need my hand-edited xorg.conf for my USB mouse and TV-out. Any kind of manual edit, even changing 'nvidia' to 'nv', results in the crash above.

Running 'sudo depmod -ae' didn't help either. I think it's a problem with the xserver-xorg package itself, rather than any module IMHO.

Xorg has always been a temperamental beast, but I've never had it do this to me. Does anyone know what I can do to get things back to the way they were? (google and the nvidia forums didn't yield any useful results).

Thanks.

---

### Post by pseudonym on 2007-01-14
Anyone?

---

