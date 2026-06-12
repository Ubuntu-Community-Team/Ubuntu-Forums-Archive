---
title: "smplayer with vdpau has hiccups"
date: 2010-09-29
forum: Multimedia Software
---

### Post by misterspider on 2010-09-29
I'm using Ubuntu 10.04 and have it hooked up to my HDTV. My GPU is an 8600 GT and I am using the current nvidia driver. Mother board is GIGABYTE GA-MA78GM-S2H, CPU is AMD 4850e, using 2x1G ram 800MHz.

Everything I have installed on it comes straight through Synaptic. Smplayer seems to work fine with the VDPAU selected (cpu usage is nice and low during HD playback), but there is a slight problem that really annoys. 

Every 2-3 seconds the picture seems to have the hiccups, its as though it gets stuck on one frame for a split second and then jumps to the next.

I'm looking for some suggestions to try and fix this.

---

### Post by cchhrriiss121212 on 2010-09-29
Do you have any desktop effects enabled? Try turning them off if so.

---

### Post by Linuxforall on 2010-09-29
Did you install smplayer and mplayer from the ppa?

---

### Post by misterspider on 2010-09-29
> **cchhrriiss121212 said:**
> Do you have any desktop effects enabled? Try turning them off if so.
I've tried to enable/disable vsync already through compiz. I need vsync enabled, otherwise there is tearing.

---

### Post by misterspider on 2010-09-29
> **Linuxforall said:**
> Did you install smplayer and mplayer from the ppa?
No, both of these through Synaptic.

---

### Post by SeijiSensei on 2010-09-29
Do you have the same problems viewing the videos with mplayer alone?

If you have experience compiling software from source, I'd recommend building an mplayer binary from one of the daily source code releases at [http://www.mplayerhq.hu/](http://www.mplayerhq.hu/).  In Ubuntu, you'll need to run "sudo apt-get install build-essential" and "sudo apt-get build-dep mplayer" to get the necessary tools and libraries.

Another option is to add [rvm's repositories]("https://launchpad.net/~rvm/+archive/ppa") and use his versions of mplayer and smplayer.  (rvm is the author of SMPlayer.)

---

### Post by cchhrriiss121212 on 2010-09-29
> **misterspider said:**
> I've tried to enable/disable vsync already through compiz. I need vsync enabled, otherwise there is tearing.
Try to actually turn them off, switch to metacity using CSM or go to preferences>appereance and select "none" in the effects tab.

---

### Post by misterspider on 2010-09-29
Thanks, I will try these options and report back.

---

### Post by andrew.46 on 2010-09-29
There is another option:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

The writer of that guide is usually fairly approachable too :).

Andrew

---

### Post by misterspider on 2010-10-01
I'll give that a try too.
Turning off desktop effects didn't solve it.

---

### Post by misterspider on 2010-10-04
I think I am having deeper issues than just VDPAU. It seems that any video (.avi, .mkv and .iso etc) are having problems using vlc, mplayer and smplayer.

I'll try swapping from an NVidia card to an ATI that I have at home, see if that helps.

---

