---
title: "Voodoo 4 4500"
date: 2006-01-20
forum: Multimedia &amp; Video
---

### Post by Kirin on 2006-01-20
In an old-ish machine I'd like to use with Ubuntu I have a Voodoo 4 4500, which I believe uses the same chipset as the Voodoo 5. In both Warty and Hoary, I could just install libglide3 via apt-get, restart X and have flawless hardware acceleration going. In Breezy I've installed the library, but no results. I've tried ldconfig, which gives the following:

```
libglide3.so.3 -> libglide3x.so
```

Still no X hardware acceleration. Has anyone had any success using glide3 with Breezy? What changed between Hoary and Breezy that broke this?

---

### Post by mo_x on 2006-01-21
I used to have a Voodo3 card and just used the tdfx driver in my xorg.conf.

---

### Post by Kirin on 2006-01-25
I'm already using the tdfx driver. So far as I know, the tdfx driver should automatically use the glide3 library if it's present. I'm not sure why 5.10 won't do that, unlike the earlier versions.

---

### Post by mo_x on 2006-01-26
What tells you that hardware acceleration is not working? What is the output of glxinfo?

---

### Post by Kirin on 2006-01-27
This is (I think) the pertinent part of the output of glxinfo:

```
direct rendering: No
```

I've attached the full output of glxinfo below. Thanks for your help so far!

---

### Post by mo_x on 2006-01-27
Yep, that is no hardware acceleration :(
Can you post your /etc/X11/xorg.conf and /var/log/Xorg.0.log.

---

### Post by Kirin on 2006-01-27
Okay, here they are. I had to generate my xorg.conf using `dpkg-reconfigure xserver-xorg` to get it working, as the autodetect (incorrectly) chose the inbuilt Intel AGP graphics chip.

(I had to GZip the Xorg.0.log file, since as plain text it exceeded the forum's max size for text files.)

---

### Post by mo_x on 2006-01-28
I am afraid I have no answer to your problem. Here is a link to a page with some more info on the tdfx driver.
[http://p197.ezboard.com/fx3dfxfrm2.showMessage?topicID=3168.topic](http://p197.ezboard.com/fx3dfxfrm2.showMessage?topicID=3168.topic)

---

### Post by Kirin on 2006-01-28
Okay, thanks for trying to help anyway. I'd heard that the Ubuntu community was supportive, but this is my first experience; it speaks well for these forums, and the distro in general.

---

### Post by Orbatos on 2006-05-13
jburnette at this thread:[http://www.ubuntuforums.org/showthread.php?p=1011347]("http://www.ubuntuforums.org/showthread.php?p=1011347")
is currently trying to resolve the same issue with a 5500.

You should talk.

---

