---
title: "Intel 915G... stuck at low resolution..."
date: 2005-12-14
forum: Multimedia &amp; Video
---

### Post by Donshyoku on 2005-12-14
I know there has been a lot of discussion on here about the chipstet, but I couldn't find anything relevant to me.

I upgraded my computer today to the latest packages, and I am running 5.10.  It detected my video, it works, and it's fast... but I am stuck in 1024x768 as a maximum resolution!  Granted it is not that low, but on a 17" LCD, it's not too flattering.  

Do I need to install a driver for this (I saw from other posts that it is included in the latest kernel)?  How can I go above this barrier?  Or worse... can I!?

Thanks in advance for the help!:)

---

### Post by kairu0 on 2005-12-14
In order to get my Intel 915GM to function at the 1280x800 resolution, I had to add that resolution to my xorg.conf file.

```
sudo gedit /etc/X11/xorg.conf
```

Toward the bottom of the file there is a section that lists each color depth with the resolutions available for it in order of priority. Add "1280x800" before the other resolutions.

If "1280x800" is already there or you can't get 1280x800 after adding it and restarting X, then you might need the 915 chipset utility (some older versions of the chipset require it as their BIOS took a lot for granted.)

---

### Post by nalmeth on 2005-12-14
if you haven't yet, try:
sudo dpkg-reconfigure xserver-xorg

most all defaults will be acceptable, but when it asks for what resolutions you want enabled, put in what you need.

---

### Post by aysiu on 2005-12-14
Just about every screen resolution fix you can find is in this post:
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by Donshyoku on 2005-12-15
I've been bouncing back and forth in my head about Kubuntu vs. Ubuntu... as for now, I am going to install Kubuntu and give it a shot, not for the video, just to taste it.  I have been really intrigued by it as of late...

On that note, however, is it possible that higher resolutions would be unlocked with KDE as opposed to Gnome... or is this based on X?

Just curious!  Thanks for the replies, if KDE doesn't fix it, I am going to leaf through those threads!

---

### Post by kairu0 on 2005-12-15
This is an X problem.

Gnome and KDE discover what resolutions are available by asking X. I don't think Kubuntu will do any better at auto-configuring a 1280x800 resolution. On the other hand, it might be a good idea to try Kubuntu just to see if you like it.

---

### Post by Donshyoku on 2005-12-15
During the install it asked me to choose the available resolutions... I was able to enable 1280x1024 and it works fine now!  

However, I am going to move back to Gnome... I'll have to start all over again and figure it out from there!  That's cool... I'll reference the threads and methods linked.

Thanks again!

---

