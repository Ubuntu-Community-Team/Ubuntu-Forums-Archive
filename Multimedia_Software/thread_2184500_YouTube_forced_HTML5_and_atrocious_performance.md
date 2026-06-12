---
title: "YouTube forced HTML5 and atrocious performance"
date: 2013-10-29
forum: Multimedia Software
---

### Post by gbrandon on 2013-10-29
So I don't see many people talking about it, but it would appear YouTube's HTML5 player is starting to come out of beta:  youtube.com/html5 says I am not opted in to the HTML5 trial, and I get the HTML5 player for all videos that don't have advertisements.

I really think this is great, except the performance I get is just terrible.  The framerate is like 3FPS and even the audio starts stuttering.

A while back, I had poor performance in VLC, and fixed it by disabling hardware video decode.  I don't understand why it would be slower, but it certainly is, for me.  In chrome:flags, there is an option called "Disable hardware-accelerated video decode," but it's disabled, apparently only available for Windows and ChromeOS.

I'm glad they're going forward with replacing Flash, but unfortunately I need to find a workaround to get acceptable performance.  Perhaps one of the following:

a) Preferably, some way I can disable hardware video decode for the entire system.  Obviously, it doesn't work well for me.  Other graphics-accelerated stuff, including WebGL, works very well for me, so I don't want to end up with too broad of a fix.

b) Reluctantly figure out how to override and be opted out of the HTML5 player, again.  I know they'll probably stop supporting the Flash player, eventually, so this would be a sad and temporary solution, but I can't think of other options.

By the way, this is my first post.  Been putting off joining for way too long.  Glad to be here. I started using Ubuntu and haven't booted Windows in over a year.  I'm currently on Ubuntu 12.04 LTS, and [here is the output of lshw]("http://pastebin.com/1HVjZYV0").

Any help on this will be very much appreciated!

---

### Post by stevenrobertson on 2013-11-02
Are you using the proprietary NVIDIA drivers or the standard ones? Which version of Chrome? Can you right-click on the HTML5 player, choose Copy Debug Info, and paste it here? Can you also try going to chrome://flags, enabling "Override software compositing list", and restarting Chrome?

---

### Post by tgalati4 on 2013-11-02
Can you zoom in and out of the video to make it different sizes?  Sometimes resizing the video can improve the performance.  Try running the video at several different sizes for the same stream rate (say 360p).

---

### Post by Yellow Pasque on 2013-11-02
> **gbrandon said:**
> In chrome:flags, there is an option called "Disable hardware-accelerated video decode," but it's disabled

If it's "disabled" (I assume you mean grayed-out), then that means hardware accel is not on, so there's no need to disable it...

---

### Post by Yellow Pasque on 2013-11-02
Can you give the output of vainfo and vdpauinfo commands?
```
sudo apt-get install vainfo vdpauinfo
vainfo
vdpauinfo
```


> **stevenrobertson said:**
> Are you using the proprietary NVIDIA drivers or the standard ones?

Proprietary:
> configuration: **driver=nvidia** latency=0

---

### Post by gbrandon on 2013-11-12
Sorry so delayed.  It is the nvidia driver 319.32 currently, with Chrome [COLOR=#303942][FONT=DejaVu Sans]30.0.1599.114[/FONT][/COLOR].  Here's all the details people asked for: [http://pastie.org/private/aiyiqepdacoip4ai1qjqea](http://pastie.org/private/aiyiqepdacoip4ai1qjqea)

I couldn't tell a difference when enabling "Override software rendering list" or in conjunction with overriding "GPU compositing on all pages."

Also stuttering seems the same between small, large, or full screen player.

---

### Post by Yellow Pasque on 2013-11-12
Install vdpau-va-driver package and look at vainfo again. Chrome/chromium uses VA-API and it's geared towards intel GPU's, though the vdpau-va-driver package should theoreticlaly allow it to work on nvidia GPU's or other open-source drivers using vdpau.

---

### Post by tgalati4 on 2013-11-12
Does your system stutter when playing videos with vlc?  Perhaps it is an audio issue.  You can run vlc in a terminal and see both information messages and error logs.  If downloaded videos stutter, then there may be a hardware or audio configuration error.

---

### Post by gbrandon on 2013-11-12
> **Temüjin said:**
> Install vdpau-va-driver package and look at vainfo again. Chrome/chromium uses VA-API and it's geared towards intel GPU's, though the vdpau-va-driver package should theoreticlaly allow it to work on nvidia GPU's or other open-source drivers using vdpau.

```
vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/i386-linux-gnu/dri/nvidia_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems VDPAU backend for VA-API - 0.7.3
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD

```

I found some Google results about "extension XFree86-DRI missing on display," but it seemed to be ATI people.  For people having issues it looked like va_openDriver() returned -1, so it's unclear whether this is even an issue.

> **tgalati4 said:**
> Does your system stutter when playing videos with vlc?  Perhaps it is an audio issue.  You can run vlc in a terminal and see both information messages and error logs.  If downloaded videos stutter, then there may be a hardware or audio configuration error.

VLC plays HD videos smoothly.  I remember turning off hardware acceleration to stop stuttering in VLC, but that was a long time ago and I actually can't get it to stutter with any setting, now.  I also see the same Xlib and libva messages from above when running VLC with hardware acceleration enabled.

---

### Post by tgalati4 on 2013-11-12
So the basic hardware works when a local, encoded video is played.  What network connectivity do you have?  DSL, cable, fiber optic?  Wired network?  1000 Gigabit, 100 Mbit?  It may be a network or router issue that is stumbling with html5 traffic versus Flash traffic.

---

### Post by brons2 on 2013-12-14
> **Temüjin said:**
> Install vdpau-va-driver package and look at vainfo again. Chrome/chromium uses VA-API and it's geared towards intel GPU's, though the vdpau-va-driver package should theoreticlaly allow it to work on nvidia GPU's or other open-source drivers using vdpau.

This is interesting.  I was having the same problem as the OP, but using Firefox.  I have a Core i3-2350M with Sandybridge mobile graphics (or whatever) and the performance on YouTube and other video sites was terrible.  Per your statement I tried Chromium and it works great, go figure!  Guess I'm switching to Chromium in on my Linux boot side.

---

