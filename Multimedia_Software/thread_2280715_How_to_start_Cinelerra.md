---
title: "How to start Cinelerra"
date: 2015-06-01
forum: Multimedia Software
---

### Post by satimis on 2015-06-01
Hi all,

Ubuntu 14.04

Please advise how to start "Cinelerra"

whereis cinelerra```

cinelerra: /usr/bin/cinelerra /usr/lib/cinelerra /usr/bin/X11/cinelerra

```

warning```

Cinelerra-CV is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra-CV.
*** Error in `/usr/bin/X11/cinelerra': free(): invalid pointer: 0x00007ffdab6aa2a8 ***
Aborted (core dumped)

```

Thanks

Regards
satimis

---

### Post by Portaro on 2015-06-01
Try 

$ cinelerra

or 

$ LIBGL_ALWAYS_SOFTWARE=1 cinelerra

---

### Post by satimis on 2015-06-02
> **Portaro said:**
> Try 

$ cinelerra

or 

$ LIBGL_ALWAYS_SOFTWARE=1 cinelerra
Hi,

Both failed

&#10219; LIBGL_ALWAYS_SOFTWARE=1 cinelerra ```

Cinelerra-CV 2.2-20150526-PPA 
(C) 2006 Heroine Virtual Ltd.
(C) 2006-2015 The CinelerraCV Community
Internal ffmpeg
Compiled on Tue May 26 19:11:54 UTC 2015

Cinelerra-CV is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra-CV.
*** Error in `cinelerra': free(): invalid pointer: 0x00007ffdb1029d18 ***
Aborted (core dumped)

```

Regards
satimis

---

### Post by satimis on 2015-06-02
Hi all,

Following document works for me;

How To Install Cinelerra 4.6 On Ubuntu 14.10, Ubuntu 14.04 And Derivative Systems (download on website)
Posted on September 13, 2014 by Geekster
[http://linuxg.net/how-to-install-cinelerra-4-6-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems/](http://linuxg.net/how-to-install-cinelerra-4-6-on-ubuntu-14-10-ubuntu-14-04-and-derivative-systems/)

Previously I installed cinelerra on repo according to following document:-

How-to Install Cinelerra Video Editor Ubuntu 14.04 Trusty
[http://tutorialforlinux.com/2015/04/15/how-to-install-the-best-video-editor-for-ubuntu-14-04-trusty-lts-3264bit-gnulinux-easy-guide/](http://tutorialforlinux.com/2015/04/15/how-to-install-the-best-video-editor-for-ubuntu-14-04-trusty-lts-3264bit-gnulinux-easy-guide/)  (April 15th, 2015 by thelinuxevangelist)

But I was unable to start cinelerra because it crashed immediately after start.

Now I can start it on terminal running;
./cinelerra

Regards
satimis

---

### Post by satimis on 2015-06-02
Hi all,

Ubuntu 14.04 64 bit

Cinelerra is installed on /home/user/cinelerra and can be started with following steps on terminal;

$ cd /home/user/cinelerra
$ ./cinelerra

But I couldn't lock its icon to laucher.  Advice would be appreciated.  Thanks

Regards
satimis

---

### Post by Yellow Pasque on 2015-06-02
In your other thread, you say you solved it, and then you made this thread. Please don't make multiple threads with the same question.. It's very confusing...

---

### Post by slickymaster on 2015-06-02
Threads merged.

Please do not create duplicate threads, it dilutes the community&#8217;s efforts to provide support and causes confusion.

---

