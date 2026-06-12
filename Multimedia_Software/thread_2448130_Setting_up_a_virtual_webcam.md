---
title: "Setting up a virtual webcam"
date: 2020-08-02
forum: Multimedia Software
---

### Post by thedarkangelqc on 2020-08-02
I've been trying to find a solution for this for days. I need to set up a virtual webcam to be able to stream my desktop to Google Meet, Zoom, Jitsu and other websites.

On Windows, it's super easy, download OBS-Studio, click play and you're set up. On Linux, there's something I'm not figuring, cause it has been a total hassle.

I did try both with Webcamoid and OBS, downloaded and compiled all the extra plugins, v4lslooback, etc.

I was able to set up a dummy webcam that Webcamoid and OBS-Studio does see:

v4l2-ctl --list-devices
Dummy video device (0x0000) (platform:v4l2loopback-000):
    /dev/video2

HP HD Webcam: HP HD Webcam (usb-0000:00:14.0-7.2):
    /dev/video0
    /dev/video1

But when I stream, it only streams a black square. Please help.

---

### Post by TheFu on 2020-08-03
Jitsi has a built-in app/desktop sharing capability.  You can put your talking head in the lower right-hand corner too - after sharing the app or desktop, click on the webcam button (next to the red button) for an overlay to be displayed. And use a chromium-based browser. Firefox support for Jitsi isn't nearly as good as for Chromium/Chrome/Brave browsers.

I've never used any of the other meeting tools in you list. Sorry.

[https://github.com/floe/deepbacksub](https://github.com/floe/deepbacksub) is what I've looked into. Obviously, for a different purpose, but similar. 

I've played with obs-v4l2sink and v4l2loopback-dkms. Never got them working, but only tried for about 30 minutes each time. Seems the packaged version of v4l2loopback on 16.04 isn't current enough to be used with the current obs-v4l2sink (only available as source). I compiled the sink and tried to get anything working in OBS and failed.  Also had to force a re-install of the v4l2loopback-dkms - the module wouldn't load since a few kernel updates have happened since the last time and the automatic DKMS isn't working.

I fear the entire stack has to be compiled from source on the same day for these things to work together, but I really don't know. It probably isn't THAT bad, just feels that way now.

---

### Post by thedarkangelqc on 2020-08-06
I'm bumping this up, I need help, I really need this to work for next week for my work, or else, I will be forced to switch back to Windows, which I really don't want to.

---

### Post by TheFu on 2020-08-24
> **davidjaxon58 said:**
> Can we do that from kali linux. If some one has experience please guide me.

Never use Kali for anything other than the intended use, which we can't discuss here.
Kali isn't secure enough to use on most networks and certainly never over the internet.  You've been warned. When the system gets completely pnw'd, you'll understand.

And ... davidjaxon58 this thread is for thedarkangelqc's issue.  If you have help for that, fantastic!  We'd all love it.
Otherwise, it is called thread hijacking. Open a new thread for your issue.  Linux systems are complex enough that problems that may seem similar on the surface seldom are. Every system is different ... especially one hacked so much like kali.

---

