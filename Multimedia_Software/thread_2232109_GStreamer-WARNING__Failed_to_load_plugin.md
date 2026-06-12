---
title: "GStreamer-WARNING **: Failed to load plugin"
date: 2014-06-29
forum: Multimedia Software
---

### Post by Lionel_London on 2014-06-29
I am running Ubuntu 13.10. When attempting to use gstreamer dependent applications (specifically totem from the terminal), I receive the following error:

GStreamer-WARNING **: Failed to load plugin '/usr/lib/i386-linux-gnu/gstreamer-1.0/libgstlibav.so': libavutil.so.51: cannot open shared object file: No such file or directory
** Message: Missing plugin: gstreamer|1.0|totem|MPEG-4 Video decoder|decoder-video/mpeg, mpegversion=(int)4, systemstream=(boolean)false, parsed=(boolean)true, profile=(string)advanced-simple, level=(string)5 (MPEG-4 Video decoder)

I have verified that "/usr/lib/i386-linux-gnu/gstreamer-1.0/libgstlibav.so" exists.

While the above warning happens when I try to use totem player (e.g. even totem's thumbnailing functionality doesn't work), the general problem appears to be with my gstreamer installation. 

What is the most efficient and safe way to completely reinstall all gstreamer components?

---

### Post by Toz on 2014-06-29
Hello and welcome to the forums

> **Lionel_London said:**
> libavutil.so.51: cannot open shared object file: No such file or directory

libavutil.so.51 is part of the **libavutil-extra-51** package. Do you have it installed?

---

### Post by Lionel_London on 2014-06-29
Yes.

---

### Post by Toz on 2014-06-29
Lets see if the library dependencies add up. What does the following return:
```
ldd /usr/lib/i386-linux-gnu/gstreamer-1.0/libgstlibav.so
```

And, can you provide more info about your totem install?
```
apt-cache policy totem
```

And finally, which gstreamer libraries do you have installed?
```
dpkg -l | grep gstreamer
```

---

### Post by mc4man on 2014-06-29
May be worth checking what you do have (in terms of package versions

```
apt-cache policy libavutil* gstreamer1.0-libav
```

---

### Post by Lionel_London on 2014-07-02
TOZ: Thanks for chiming in. I've put the output of your suggested commands here: [http://pastebin.com/SwUXN1F6](http://pastebin.com/SwUXN1F6)

---

### Post by Lionel_London on 2014-07-02
Hi mc4man, here's what I get:

libavutil-extra-50:  Installed: (none)
  Candidate: (none)
  Version table:
libavutil-extra-51:
  Installed: 7:2.2.1-2~saucy1
  Candidate: 7:2.2.1-2~saucy1
  Version table:
 *** 7:2.2.1-2~saucy1 0
        500 [http://ppa.launchpad.net/djcj/vlc-stable/ubuntu/](http://ppa.launchpad.net/djcj/vlc-stable/ubuntu/) saucy/main i386 Packages
        100 /var/lib/dpkg/status
     6:0.8.12ubuntu0.13.10.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/universe i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/universe i386 Packages
     6:0.8.7ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe i386 Packages
libavutil-extra-52:
  Installed: (none)
  Candidate: (none)
  Version table:
libavutil-dev:
  Installed: (none)
  Candidate: 7:2.2.1-2~saucy1
  Version table:
     7:2.2.1-2~saucy1 0
        500 [http://ppa.launchpad.net/djcj/vlc-stable/ubuntu/](http://ppa.launchpad.net/djcj/vlc-stable/ubuntu/) saucy/main i386 Packages
     6:0.8.12-0ubuntu0.13.10.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main i386 Packages
     6:0.8.7-1ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/main i386 Packages
libavutil51:
  Installed: (none)
  Candidate: 6:0.8.12-0ubuntu0.13.10.1
  Version table:
     6:0.8.12-0ubuntu0.13.10.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/main i386 Packages
        100 /var/lib/dpkg/status
     6:0.8.7-1ubuntu2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/main i386 Packages
libavutil52:
  Installed: 7:2.2.1-2~saucy1
  Candidate: 7:2.2.1-2~saucy1
  Version table:
 *** 7:2.2.1-2~saucy1 0
        500 [http://ppa.launchpad.net/djcj/vlc-stable/ubuntu/](http://ppa.launchpad.net/djcj/vlc-stable/ubuntu/) saucy/main i386 Packages
        100 /var/lib/dpkg/status
gstreamer1.0-libav:
  Installed: 1.0.10-1ubuntu1
  Candidate: 1.0.10-1ubuntu1
  Version table:
 *** 1.0.10-1ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe i386 Packages
        100 /var/lib/dpkg/status

---

### Post by Lionel_London on 2014-07-02
After a bit of tinkering, I solved it!

While some scattered forum posts for similar errors suggested that completely removing then reinstalling all gstreamer components was the key, I actually had to:

Completely removed the following packages:
libavutil-extra-51


Removed the following packages:
libavcodec-extra-53
libavformat-extra-53


Installed the following packages:
libavcodec53 (6:0.8.12-0ubuntu0.13.10.1)
libavformat53 (6:0.8.12-0ubuntu0.13.10.1)
libavutil51 (6:0.8.12-0ubuntu0.13.10.1)

That fixed it!!

---

### Post by Toz on 2014-07-02
> **Lionel_London said:**
> TOZ: Thanks for chiming in. I've put the output of your suggested commands here: [http://pastebin.com/SwUXN1F6](http://pastebin.com/SwUXN1F6)

From your results:
> libavutil.so.51 => not found
...so its not there.

However, from your apt-cache results:
> libavutil-extra-51:
Installed: 7:2.2.1-2~saucy1
Candidate: 7:2.2.1-2~saucy1
Version table:
*** 7:2.2.1-2~saucy1 0
500 [http://ppa.launchpad.net/djcj/vlc-stable/ubuntu/](http://ppa.launchpad.net/djcj/vlc-stable/ubuntu/) saucy/main i386 Packages
100 /var/lib/dpkg/status
6:0.8.12ubuntu0.13.10.1 0
500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/universe i386 Packages
500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) saucy-security/universe i386 Packages
6:0.8.7ubuntu1 0
500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/universe i386 Packages
...the necessary package is installed, however from a PPA (not the official repositories). And here is where it gets interesting...the package isn't even in the PPA anymore.

Ahhh nevermind now, I see you fixed it. Good news. The packages in question were probably removed from the PPA at some point in time but still existed in your system.

---

### Post by Lionel_London on 2014-07-02
Thanks anyhows TOZ! I still learned a bit from your response.

---

### Post by mc4man on 2014-07-02
There are a number of ppa's that contain newer FFmpeg or Libav shared libs. So if using, one should make themselves well aware of why are you using  & also of what sources/packages that use those shared libs will break or degrade.

Personally don't really see the advantage unless one is willing to rebuild & occasionally patch the effected apps that they use. By & large simply installing newer or different  libs doesn't translate to apps that use them. (with some exceptions
I didn't go to that ppa  page though my view is the ppa should warn about what may break & whenever possible offer rebuilt sources that do work with the new shared libs

(- there is one ppa that offers shared FFmpeg libs but does so thru alternatives. It seems it may be ok though I gather one would need to change the .so's used as needed. I guess that's workable but certainly not ideal.

---

