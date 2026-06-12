---
title: "gstreamer0.10-plugins-ugly-multiverse install problem"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by sasquatch on 2006-09-22
Trying to get mpeg/wmv/etc viewing working, using RestrictedFormats instructions. I'm a Linux tyro. Useing Dapper on Intel processor:

> uname -a
Linux rivendell 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux

The RestrictedFormats instructions require installing a number of packages, including gstreamer0.10-plugins-ugly-multiverse. When I attempt to use Synaptic to install, I get this error:

gstreamer0.10-plugins-ugly-multiverse:
 Depends: liblame0 (>=3.96.1-1) but it is not installable

Any ideas what this means?

-dave

---

### Post by ropers on 2006-09-22
Apparently your gstreamer plugins require liblame0 to work (hence "dependency").
If you directly search for the liblame0 package name in Synaptic Pkg.Mngr., do you find it? Does it show as installed? If not, can you install it. On my box liblame0 shows as installed.

---

### Post by sasquatch on 2006-09-23
Nope, searched for liblame0 using Synaptic Pkg Mgr, nothing shows up. Same for searching for "lame" and "liblame".

> **ropers said:**
> Apparently your gstreamer plugins require liblame0 to work (hence "dependency").
If you directly search for the liblame0 package name in Synaptic Pkg.Mngr., do you find it? Does it show as installed? If not, can you install it. On my box liblame0 shows as installed.

---

### Post by immer on 2006-09-23
maybe you need to edit your repository list. 
there is an article on it [http://www.ubuntuforums.org/showthread.php?t=185758]("http://www.ubuntuforums.org/showthread.php?t=185758")

it worked for me

---

### Post by ropers on 2006-09-23
> **immer said:**
> maybe you need to edit your repository list. 
there is an article on it [http://www.ubuntuforums.org/showthread.php?t=185758]("http://www.ubuntuforums.org/showthread.php?t=185758")

it worked for me

If you're just starting out it's probably cozier for you to just go to System -- Administration -- Synaptic -- Settings -- Repositories. Select the repositories you're missing there (not all repositories, just the ones you need). If you don't know which repositories you want to include despite reading all the info on the Restricted Formats page, etc. etc. then post which ones you currently HAVE selected. Even should I personcally forget to revisit this post, I'm sure you'll find someone here who you can compare your repository list with.

---

### Post by kfb on 2006-09-23
Hey,

I just had the same problem with a fresh install and I can tell you how to fix it.  In that menu where you enable new repositories you may not find a 'multiverse' one.  That's the one you need to get lame.  If that's the case, click on 'Add' and check the multiverse box.  That'll add the multiverse repository to one of the channels there.  Find the multiverse one and make sure it's enabled.  Hit refresh and you'll be good.

As a note to someone involved with Ubuntu, that channel should've been there when I installed, but it wasn't.  It's been there on installs in the past, so I'm thinking this is a new bug and it looks like I'm not the only person to have encountered it.

---

