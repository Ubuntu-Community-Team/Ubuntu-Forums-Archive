---
title: "Anybody able to install Handbrake on 12.10 64-bit?"
date: 2012-11-11
forum: Multimedia Software
---

### Post by The Bright Side on 2012-11-11
Hey guys!

A couple weeks after release, I remain unable to install Handbrake on Ubuntu 12.10 64-bit. A while ago, I couldn't add the PPA (ppa:stebbins/handbrake-releases) at all, with Ubuntu telling me it couldn't find it. Now, I can add the PPA but all I find in it is an i386 version:

handbrake-gtk:i386

When I try to install that, I'm told a crapload of packages need to be removed, among them stuff like VLC, k9copy and mplayer, which I really want to keep. It also says it needs to install a huge load of i386 libraries.

Anybody able to run Handbrake on 12.10 64? How did you pull it off?

Thanks!

---

### Post by JohnAStebbins on 2012-11-12
> **The Bright Side said:**
> Hey guys!

A couple weeks after release, I remain unable to install Handbrake on Ubuntu 12.10 64-bit. A while ago, I couldn't add the PPA (ppa:stebbins/handbrake-releases) at all, with Ubuntu telling me it couldn't find it. Now, I can add the PPA but all I find in it is an i386 version:

handbrake-gtk:i386

When I try to install that, I'm told a crapload of packages need to be removed, among them stuff like VLC, k9copy and mplayer, which I really want to keep. It also says it needs to install a huge load of i386 libraries.

Anybody able to run Handbrake on 12.10 64? How did you pull it off?

Thanks!
One other person reported having this kind of problem. Then it just resolved itself.  If you continue to have problems, you might want to try downloading the deb file manually from the ppa and use dpkg -i to install it.  The 64 bit package is definitely there on the ppa.

---

### Post by JohnAStebbins on 2012-11-12
Is it possible you have the same problem as this poster?
[http://ubuntuforums.org/showthread.php?p=12351000&highlight=handbrake#post12351000](http://ubuntuforums.org/showthread.php?p=12351000&highlight=handbrake#post12351000)

---

### Post by The Bright Side on 2012-11-12
Thanks so much! That worked!

---

