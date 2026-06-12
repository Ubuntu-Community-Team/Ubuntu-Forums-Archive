---
title: "Howto install RealPlay-10 for Ubuntu?"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by kline on 2006-11-14
About ten days ago I installed helix in /root/RealPlayer.  I tried to get it to work with SMIL and RM, RAM, but with limited success.  What's the best way to grab RealPlayer-10 and to install it?

I can use xmms to play mmp3 files, but trying to listen to R?M files, I get the stderr: "Cannot open audio device".  Not even a theraputic reboot cleaned out whatever lock file or other file is causing error message.  I am doing a system-wide grep to see if I can find the src of this string.  So far, no-joy.  Any help willl be very much appreciated!

---

### Post by ciscosurfer on 2006-11-14
You can try using [Automatix]("http://getautomatix.com") to grab RealPlayer or [you can go here]("https://player.helixcommunity.org/2004/downloads/"), download the source and build it yourself, or download the RPM and use **Alien** to convert it to a .deb and install it that way.

---

### Post by shawn fernandes on 2006-11-15
How to use alien?

---

### Post by ciscosurfer on 2006-11-15
[Look here and go to the section called RPM package (.rpm)]("http://monkeyblog.org/ubuntu/installing/")

Once you get Alien installed, you can look at the man pages for additional command line switches```
man alien
```

---

### Post by gjtoth on 2006-11-17
> **ciscosurfer said:**
> [Look here and go to the section called RPM package (.rpm)]("http://monkeyblog.org/ubuntu/installing/")

Once you get Alien installed, you can look at the man pages for additional command line switches```
man alien
```

First of all, thanks!  I thought I was losing my mind (and I still might be ](*,) ).  I did not know Alien was not installed by default.  

Now, where do I get it?

---

### Post by gjtoth on 2006-11-17
> **gjtoth said:**
> First of all, thanks!  I thought I was losing my mind (and I still might be ](*,) ).  I did not know Alien was not installed by default.  

Now, where do I get it?


Never mind... I got it from Freshmeat.org  :)

---

### Post by ciscosurfer on 2006-11-17
Glad you grabbed it from Freshmeat.org

You can also download it from the Ubuntu repos as well.

---

### Post by gjtoth on 2006-11-17
heh... as it turns out, I didn't require it for Limewire as I anticipated. I'm sure it will come in handy for other stuff, though.

---

### Post by ciscosurfer on 2006-11-17
What I love about Alien is how versatile it is (but remember, it's good advice to use it sparingly as you can wind up with dependency issues, that is, an .rpm that you convert may require additional packages that you don't have installed and that may be incompatible with your system--which is why it's usually a good idea to grab packages that are specific to your distro, in our case, Ubuntu and .deb packages).  That said, I truly marvel at how it works and what it can do (from the man pages):

**DESCRIPTION**
       alien is a program that converts between Red Hat rpm, Debian deb, Stampede slp, Slackware tgz, and Solaris pkg file formats. If you want to use a package from another linux distribution than the one you have installed on your system, you can use alien to convert it to your preferred package format and install it. It also supports LSB packages.

---

