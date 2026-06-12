---
title: "Sound problem with apps using OSS"
date: 2008-11-30
forum: Multimedia Software
---

### Post by Zeikcied on 2008-11-30
OSS worked for me up until some point when I was using Kubuntu Gutsy or Feisty, I forget which.  I'm currently using Intrepid (I did the software upgrade to Hardy and Intrepid).

The problem is that there are some apps I use that make use of OSS.  But they haven't output any sound since OSS stopped working.  I know there are some workarounds, like installing the ALSA OSS compatibility libraries, and then using aoss to start the program.  But is there any way to either fix OSS (assuming it's still available in Intrepid) or set it so that all apps looking for OSS use ALSA or ALSA's compatibility layer without me having to constantly use the aoss command?

---

### Post by markbuntu on 2008-11-30
Go here, it is a quick guide to getting sound working in Intrepid, including oss apps:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Most oss apps will just use the libasound2 plugins transparently but for those that do not you can use aoss (alsa wrapper) or padsp (pulseaudio wrapper) in the launcher after you have installed the packages reccomended in the post.

---

### Post by Zeikcied on 2008-11-30
> **markbuntu said:**
> Go here, it is a quick guide to getting sound working in Intrepid, including oss apps:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Most oss apps will just use the libasound2 plugins transparently but for those that do not you can use aoss (alsa wrapper) or padsp (pulseaudio wrapper) in the launcher after you have installed the packages reccomended in the post.
I have all the packages mentioned in that thread (except the GNOME and GTK-based apps, as I'm using Kubuntu Intrepid thus KDE4).

Sound works just fine.  But there are a handful of applications that only use OSS (one of which is an SDL app) and for whatever reason aren't using the alsa-oss compatibility libraries.  I was more or less hoping for an easier solution than to constantly have to use aoss.  But I guess I'm stuck with that, huh?

---

### Post by markbuntu on 2008-11-30
There is a sdl package that has the alsa and pulse plugins, you might try that for the SDL apps .

libsdl1.2debian-all

or for just pulseaudio:

libsdl1.2debian-pulseaudio

You can also just make a launcher for your panel or menu or desktop and use aoss application as the launch command.

---

### Post by Zeikcied on 2008-11-30
> **markbuntu said:**
> There is a sdl package that has the alsa and pulse plugins, you might try that for the SDL apps .

libsdl1.2debian-all

or for just pulseaudio:

libsdl1.2debian-pulseaudio

You can also just make a launcher for your panel or menu or desktop and use aoss application as the launch command.
I was able to make SDL use ALSA by using an export command that I found online.  But I don't now how to configure SDL to always use ALSA.  If that's even possible when using a pre-compiled binary.

---

