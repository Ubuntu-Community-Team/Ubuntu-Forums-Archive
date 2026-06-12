---
title: "ipod mount difficulties"
date: 2008-06-04
forum: Multimedia Software
---

### Post by rflight79 on 2008-06-04
So, back when I had Gutsy, I plugged in my iPod (2nd Gen Nano), and there it was, all ready to go for gtkPod or Amarok, no problems at all. I just upgraded to Hardy, and went back to Gnome (because gtkpod has fewer problems), and I went to plug in my iPod.

This is what I got:

> Error org.freedesktop.DBus.Error.AccessDenied

And I can't see my iPod. Not a happy camper. I did some searching around, and all I can find is that it seems I don't have the ability to mount the iPod as a user. Thankfully, I found this:

[http://blogs.techrepublic.com.com/opensource/?p=217](http://blogs.techrepublic.com.com/opensource/?p=217)

The whole problem just comes down to creating a directory to mount to, finding where you iPod is in /dev, and making the appropriate entry in fstab, but it is the equivalent of a USB key as far as the OS is concerned, why should I have to do that? Didn't have to do it before (afaik), so why now? 

Hope not too many other people have this problem.

---

