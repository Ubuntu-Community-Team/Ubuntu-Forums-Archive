---
title: "Logitech QC Pro 9000 in Ubuntu 9.10"
date: 2010-01-03
forum: Multimedia Software
---

### Post by thomasivan7 on 2010-01-03
Hi all,

I recently purchased Logitech Quickcam pro 9000. I have installed Ubuntu 9.10. The camera worked instantly with no hassles.

However the auto focus feature does not work.

Can anybody tell what i need to do to get this feature?
Also what software has to be installed in order to access my camera via a c++ program ?

What is the purpose of the drivers in here:
[http://www.quickcamteam.net/software/libwebcam/]("http://www.quickcamteam.net/software/libwebcam/")

Btw what is UVC? V4L? damn confusing!!

Plz help!

---

### Post by santhony on 2010-01-03
> **thomasivan7 said:**
> Hi all,

I recently purchased Logitech Quickcam pro 9000. I have installed Ubuntu 9.10. The camera worked instantly with no hassles.

However the auto focus feature does not work.

Can anybody tell what i need to do to get this feature?
Also what software has to be installed in order to access my camera via a c++ program ?

What is the purpose of the drivers in here:
[http://www.quickcamteam.net/software/libwebcam/]("http://www.quickcamteam.net/software/libwebcam/")

Btw what is UVC? V4L? damn confusing!!

Plz help!

I'm in the same boat.. but do have little more understanding..

V4L is Video for Linux.

The cam does work out of the box, such as it works immediately with Skype.

I think the extra software might enable the camera options such as the auto focus and other features...  

The website only offers it as source code.. which needs to be comipiled and such..  But.. I'm sure someone has already done this for Ubuntu.. So we should be able to find the files as Debian, where we can just double click them and they will install automaticially for us...

I'll post a link if I find them..

---

### Post by andersja on 2010-09-24
> **santhony said:**
> I'm sure someone has already done this for Ubuntu.. So we should be able to find the files as Debian, where we can just double click them and they will install automaticially for us...

FYI I think libwebcam is now packaged in the Ubuntu repositories for Maverick.

This should work in the terminal:

```
sudo aptitude install uvcdynctrl
```

More info + examples of usage here:
[http://forum.skype.com/index.php?showtopic=152201](http://forum.skype.com/index.php?showtopic=152201)

See also:
[https://bugs.launchpad.net/ubuntu/+bug/394635](https://bugs.launchpad.net/ubuntu/+bug/394635)

---

