---
title: "package xmms-mp4"
date: 2009-07-30
forum: Multimedia Software
---

### Post by hydrotemplar on 2009-07-30
the package is an old plugin to add support for AAC formats to XMMS(1).  One of its dependencies is libglib1.2 or better.  I have libglib2.0 and libglib1.2ldbl.  I found the libglib1.2 package, but it won't install because it would break libglib1.2ldbl.  How can I resolve this issue to get xmms-mp4 to install?

Thanks,
David

---

### Post by AmyRose on 2009-07-30
Where did you get these packages from?

---

### Post by hydrotemplar on 2009-07-30
xmms: [http://www.xmms.org/](http://www.xmms.org/)
xmms-mp4: [http://packages.ubuntu.com/dapper/sound/xmms-mp4](http://packages.ubuntu.com/dapper/sound/xmms-mp4)
libglib1.2: [http://packages.debian.org/etch/i386/libglib1.2/download](http://packages.debian.org/etch/i386/libglib1.2/download)
   also tried the one from the dapper repositories (didn't think it would be any different, and it wasn't)

libglib2.0 and libglib1.2ldbl are in the package manager

---

### Post by AmyRose on 2009-07-30
It is not recommended to manually download packages from Debian and try to install them. What version of Ubuntu are you on?

Have you tried Audacious? it's basically a port of XMMS to GTK 2 and other more modern libraries, and it's been in the Universe repos for a while. The equalizer also works for everything, not just MP3s. It's my favorite music player.

---

### Post by hydrotemplar on 2009-07-31
I'm on Jaunty, and I know I can't expect everything work right from older packages, though if it's doable I would very much like to have it working...

as for audacious, I've used it for several months, and have never been particularly pleased with it, but it served my purpose.  several days ago it failed at a very critical point, which combined with its sub-par usual performance, is unforgivable...
I found it slower, and the settings I changed the most were buried, which gets quite frustrating.  also alot of little things didn't work like they should... overall I found it to be mediocre at best.
xmms is faster, and everything works right.  with this one exception, i've been extremely pleased with my experience with it.

if this can't be resolved, i'll probably convert my m4a's to mp3, however I shudder at the loss of quality...

thanks though : )

---

### Post by mc4man on 2009-07-31
I use hardy but take a look here and see what you can possibly work out for jaunty.
[http://colonos.wordpress.com/2009/04/27/xmms-in-jaunty-jackalope-904-how-to-install-with-codecs/](http://colonos.wordpress.com/2009/04/27/xmms-in-jaunty-jackalope-904-how-to-install-with-codecs/)

It also appears you may be able to use the hardy redo of the dapper mp4 plugin in jaunty (mentioned in above link 
[https://launchpad.net/ubuntu/hardy/i386/xmms-mp4/2.6-1](https://launchpad.net/ubuntu/hardy/i386/xmms-mp4/2.6-1)

---

### Post by hydrotemplar on 2009-07-31
mc4man, thank you so much, the binary in the second link installed and works right!

---

