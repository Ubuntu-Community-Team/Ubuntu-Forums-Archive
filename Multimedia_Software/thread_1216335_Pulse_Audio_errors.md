---
title: "Pulse Audio errors"
date: 2009-07-18
forum: Multimedia Software
---

### Post by Stoneface on 2009-07-18
I have had many problems with Pulse audio | ALSA under Ubuntu. Skype sound in works, but out is worthless. Now I just saw some pulse audio errors in user.log:
```
Jul 18 13:31:52 me-laptop pulseaudio[4503]: module-x11-xsmp.c: X11 session manager not running.
Jul 18 13:31:52 me-laptop pulseaudio[4503]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
```

Does anybody know why I have these errors and if they are related to my Skype problems?

Here some intel on my Acer Aspire laptop:
Jaunty Jackalope 9.0.4 with Gnome
2.6.28-13-generic
pulseaudio 0.9.14

Some discussion going on here:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/300275](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/300275)

Still going hrough all the data. Extra tips would be welcome

---

### Post by kiridude on 2009-07-18
I spent ages trying to get skype to work correctly and in the end it still had a delay during conversations. Since Skype does not take the time to create I high quality version for linux (as they have done for Windows), I suggest you drop it and use Ekiga (included with Ubuntu), or any other softfone that suits you for that matter. If you use the SIP protocall, you can communicate with many other different softfones (unlike skype). If you want to speak with people who are on Windows, I would suggest telling them to download Gizmo. It's free, uses SIP, and works well.

---

### Post by Stoneface on 2009-07-18
@ Kiridude Yeah I might just do that. But unfortunately in my line of work I need Skype to communicate with other Skypers. And I hate rebooting into Windows for that. Is it possible to communicate with other Skype users with Ekiga or other Linux software out there? 

P.S. I will check Gizmo out asap.

---

### Post by igorzwx on 2009-07-18
perhaps, this may help:
[http://ubuntuforums.org/showthread.php?t=1215803](http://ubuntuforums.org/showthread.php?t=1215803)

---

### Post by Stoneface on 2009-07-19
@ Igorzwx I am considering your option for a sort of OSS plugin @ [http://insanecoding.blogspot.com/2009/05/perfect-sound-with-oss-version-4.html](http://insanecoding.blogspot.com/2009/05/perfect-sound-with-oss-version-4.html) . But I am not sure yet. I have been playing around with ALSA (Advanced Linux Sound Architecture) and Pulse Audio for a long time and it is a lot of work already. Trying ALSA's predecessor as a replacement of ALSA or as a plugin seems hard for me now.
Furthermore, I will try to optimize audio using ALSA and probably drop Skype for Linux as Ubuntu does not have audio to support it which is a shame. And unfortunately the new Skype for Linux, which was promised a year ago, has not emerged either..

---

### Post by igorzwx on 2009-07-19
You can, perhaps, use Skype on Linux in this way

Visit this site:
[http://www.slax.org/build.php](http://www.slax.org/build.php)

"Create your own customized Slax with all the features you    need, download your ISO or TAR directly from this site. Please note, this page is going to be redesigned, in    order to provide much easier functionality. But it works now, so you    are welcome to try it. We will see if the server gets overloaded."

They have a verified Skype package for Slax.

It takes 5 minutes to get your customized LiveCD.

Click here and there, and download your LiveCD ISO

Best,
Igor

---

