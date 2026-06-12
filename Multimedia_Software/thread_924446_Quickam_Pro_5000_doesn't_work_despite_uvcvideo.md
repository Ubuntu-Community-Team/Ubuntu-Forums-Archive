---
title: "Quickam Pro 5000 doesn't work despite uvcvideo"
date: 2008-09-19
forum: Multimedia Software
---

### Post by Pavle on 2008-09-19
Hi all,
I found quite a lot of posts about installing this cam and I followed the tutos but something goes wrong at the end. I'm running 8.04 so I had the uvc drivers installed by default. I checked dmesg and everything seemed fine the cam and the audio both got detected. But when testing with luvcview I get:

luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Unable to set format: 5.
 Init v4L2 failed !! exit fatal 

I then went back to dmesg and got a bunch of errors like:
[23850.002128] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23881.987873] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23885.860472] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[24033.906360] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).

I saw other ppl had similar problems but I saw no solution to it. I also tried with Ekiga but it doesn't work either:

Error while opening video device UVC Camera (046d:08ce)
...
Your driver doesn't seem to support any of the color formats supported by Ekiga.

So I'm stuck.
Any ideas ?
Thanks a lot!

---

### Post by Pavle on 2008-09-20
I see other ppl have similar problems w/ logitech cams (recent posts) however ekiga seems to work for everybody which is not my case.

Anybody?

Edit:
I just stumbled across similar posts:
[http://ubuntuforums.org/archive/index.php/t-532852.html](http://ubuntuforums.org/archive/index.php/t-532852.html) --> unanswered

[http://lists.berlios.de/pipermail/linux-uvc-devel/2007-February/001360.html](http://lists.berlios.de/pipermail/linux-uvc-devel/2007-February/001360.html) --> bad news they're talking a about a Logitech hardware bug.

The strange thing is that I think it worked on Feisty (not to mention that it works on Windows)...

---

### Post by jazzgossen on 2008-10-28
I have a similar problem. 

I'm grabbing frames from my Logitech with uvccapture once per minute (from cron), and it works for a while. I've used the camera in cheese and ekiga with no problem (but I've only tried it for short periods). 

When I grab images, it will work for 20-40 minutes, but then it stops grabbing, and I start getting these "uvcvideo: Failed to query" messages in dmesg. When I unplugged and replugged the USB cable, it worked again for 40 minutes or so, but then started failing again.

After it has started to fail, running uvccapture from the command line says

Unable to set format: 5.
 Init v4L2 failed !! exit fatal 

Your second link, to the berlios forum, isn't really related to this, is it? The poster there only complains about /dev/video not found. In my case, there is no /dev/video, but the camera is at /dev/video0.

---

### Post by Kheops_74 on 2008-11-22
Any news. I think i have the same problem.

I think it's related to the speed of the usb port. If i try this it's better 

rmmod ehci-hcd

---

### Post by freesofts on 2008-11-22
> **Pavle said:**
> Hi all,
I found quite a lot of posts about installing this cam and I followed the tutos but something goes wrong at the end. I'm running 8.04 so I had the uvc drivers installed by default. I checked dmesg and everything seemed fine the cam and the audio both got detected. But when testing with luvcview I get:

luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Unable to set format: 5.
 Init v4L2 failed !! exit fatal 

I then went back to dmesg and got a bunch of errors like:
[23850.002128] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23881.987873] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[23885.860472] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
[24033.906360] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).

I saw other ppl had similar problems but I saw no solution to it. I also tried with Ekiga but it doesn't work either:

Error while opening video device UVC Camera (046d:08ce)
...
Your driver doesn't seem to support any of the color formats supported by Ekiga.

So I'm stuck.
Any ideas ?
Thanks a lot!

Upgrade software !

---

### Post by jazzgossen on 2008-11-25
Update: I found out that there's a firmware bug with this camera and it doesn't work reliably with the Linux UVC driver. Check [this list]("http://linux-uvc.berlios.de/"). Too bad.

---

