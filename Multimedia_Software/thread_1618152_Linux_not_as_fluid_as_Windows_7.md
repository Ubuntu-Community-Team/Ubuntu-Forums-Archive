---
title: "Linux not as fluid as Windows 7"
date: 2010-11-10
forum: Multimedia Software
---

### Post by neu5eeCh on 2010-11-10
I have Ubuntu and Win7 installed on the same VIAO - 64bit Nvidia. I notice that watching DVDs on Linux is never smooth (using movie player or VLC). There are artifacts and it seems that the bottom half the screen is sometimes trying to catch up with the top half.

The same video on the Win7 side is seamless and flawless (if you don't mind being interrupted by ANTI-V, Malware, Windows, Secunia, etc. etc. updates every Chr---stly two minutes).

Is this just a Linux limitation? Will the move to Wayland help with this?

---

### Post by qamelian on 2010-11-10
More likely a result of how Linux interacts with your specific hardware. My Win7 Media Center PC actually works better with Linux with less artifacting and no skipping during playback. Results will vary from one system to another, just like they wil with any OS.

---

### Post by neu5eeCh on 2010-11-10
Thanks qamelion. 

I'm sorry to hear that (because it means there's not much I can do about it). What software do you use on the Linux side? And have you installed any proprietary video drivers?

(And I'm off to work. I'll check in tonight...)

---

### Post by gradinaruvasile on 2010-11-10
> **VTPoet said:**
> I have Ubuntu and Win7 installed on the same VIAO - 64bit Nvidia. I notice that watching DVDs on Linux is never smooth (using movie player or VLC). There are artifacts and it seems that the bottom half the screen is sometimes trying to catch up with the top half.

The same video on the Win7 side is seamless and flawless (if you don't mind being interrupted by ANTI-V, Malware, Windows, Secunia, etc. etc. updates every Chr---stly two minutes).

Is this just a Linux limitation? Will the move to Wayland help with this?

Try mplayer/smplayer - if you use nvidia card make sure you install the proprietary driver and set vsync to on for the xvideo device. And use VDPAU if available on your card - that uses vsync by default.

Also, disable the graphic effects, sometimes interfere with video playback.

---

### Post by qamelian on 2010-11-10
> **VTPoet said:**
> Thanks qamelion. 

I'm sorry to hear that (because it means there's not much I can do about it). What software do you use on the Linux side? And have you installed any proprietary video drivers?

(And I'm off to work. I'll check in tonight...)

My MC PC has a Nvidia GT220 video card with the proprietary drivers installed. I get perfect DVD playback using both Totem and MPlayer.

---

### Post by neu5eeCh on 2010-11-11
> **gradinaruvasile said:**
> Try mplayer/smplayer - if you use nvidia card make sure you install the proprietary driver and set vsync to on for the xvideo device. And use VDPAU if available on your card - that uses vsync by default.

Also, disable the graphic effects, sometimes interfere with video playback.

Good information and I [found the post]("http://ubuntuforums.org/showthread.php?t=1037625"), but it looks like a freakin' minefield! :(

---

### Post by I'mGeorge on 2010-11-11
> **VTPoet said:**
> I have Ubuntu and Win7 installed on the same VIAO - 64bit Nvidia. I notice that watching DVDs on Linux is never smooth (using movie player or VLC). There are artifacts and it seems that the bottom half the screen is sometimes trying to catch up with the top half.

Hey have you ever tried xbmc for video DVD's and for playing the most multimedia files ? I agreed it looks kinda fancy but I find it very good for multimedia in many ways. You could just cache it out and see how it goes.

---

### Post by SeijiSensei on 2010-11-11
> **VTPoet said:**
> Good information and I [found the post]("http://ubuntuforums.org/showthread.php?t=1037625"), but it looks like a freakin' minefield! :(

Just use the built-in application that comes with Ubuntu to install the  proprietary Nvidia driver.  It's called "Hardware Drivers" in versions before 10.10, and "Additional Drivers" in that version.  It will search your hardware, detect the video card, and offer to install the matching driver.  It's always worked fine for me.

Install smplayer if you don't already have it, then go to Options > Preferences, click on the Video tab, and choose the vdpau driver if it's not already the default.

If that doesn't fix the problem entirely, there are a few other tweaks we can add, but the default settings seem to work well for me with a 9500GT card.  I can watch 1080p H.264 encodes without glitches.

---

### Post by cchhrriiss121212 on 2010-11-11
DVD playback on Linux is not at the same level as Windows. I find that some DVDs are perfect on both OSs whereas others (usually animation) are near unwatchable on Linux. Tearing is present during motion, and any kind of pan will look awful. My system has the necessary power: Athlon II 245 @2.9GHz, Nvidia 9600GT, 4GB RAM @ 1066MHz. 
I don't use compiz and have tried various distros. I have tested all the main players/ouputs : xv, vdpau, xine, mplayer etc. They all have the same issue, so I assume it is down to libdvdcss2 not being good enough. Or maybe my hardware is just not the right combination? 

Because only a few of my DVDs are affected, I have learned to rip these few to my HD with Handbrake, which is the best solution for me.

---

### Post by neu5eeCh on 2010-11-11
> **SeijiSensei said:**
> Install smplayer if you don't already have it, then go to Options > Preferences, click on the Video tab, and choose the vdpau driver if it's not already the default.

If that doesn't fix the problem entirely, there are a few other tweaks we can add, but the default settings seem to work well for me with a 9500GT card.  I can watch 1080p H.264 encodes without glitches.

I already installed the NVidia driver a while back hoping that would fix the problem. It didn't. I haven't tried SMplayer. Just installed it and set vdpau as the default. I'm watching Cosmos with the kids tonight, so I'll get back to y'all so you know how it worked.

---

### Post by neu5eeCh on 2010-11-11
Update: SMPlayer was much improved but still not fluid or comparable to Windows... unfortunately. 

I'll be interested to see if Wayland improves Linux's (Ubuntu's) video performance.

For the time being, at least, I'll be watching videos on Win7 - at least on **this** machine.

---

### Post by neu5eeCh on 2012-07-08
Sorry. Just marking this old thread solved, with [a link to the solution.]("http://ubuntuforums.org/showthread.php?t=2013413")

---

### Post by oldos2er on 2012-07-08
And with that, I'll close it. Thanks for the solution!

---

