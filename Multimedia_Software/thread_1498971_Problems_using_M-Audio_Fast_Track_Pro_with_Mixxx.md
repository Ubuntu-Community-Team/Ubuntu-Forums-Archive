---
title: "Problems using M-Audio Fast Track Pro with Mixxx"
date: 2010-06-01
forum: Multimedia Software
---

### Post by LetsLinux on 2010-06-01
Hello,

I've installed Ubuntu 10.04 and it works like a charm, pretty much all over. However I seem to have problems using my M-Audio Fast Track Pro with all four channels - primarily when using Mixxx.

I hate to switch between Win7 and Ubuntu just for the use of my VCI-100.

Is there a way to have Fast Track Pro work? I tried almost any of the solutions found around here - but i simply cannot get it to work.

I hope that you can help me.

---

### Post by cchhrriiss121212 on 2010-06-01
Perhaps describe the problem a bit more. Are you using jack? Any error messages etc.

---

### Post by LetsLinux on 2010-06-01
Oh sorry, I'm fairly new to linux... So here goes...

I plugged in the soundcard via USB. Then I started up Mixxx (got it from the repo) and tried to set it up. I could only choose channel 1 and 2 - and not the 3 - 4. :-(

I'm not sure if I use JACK. What is the package name for it?

---

### Post by jangal on 2010-06-01
does the m-audio device show in as a choice in mixx's master/headphone selection menu? 

does your computer even recognize the device? have you tried with other apps?

also jack is not necessary for mixx, it can work with alsa just fine. jack would be needed only if your interface requires it, which might be your case. i think it is safe to say that you are not using jack based on your response above. jack is a real sophisticated way using audio apps and devices, it is basically a sound server program that allows you to route audio signals internally and externally.  

check this thread: [http://ubuntuforums.org/showthread.php?t=846717](http://ubuntuforums.org/showthread.php?t=846717)

---

### Post by daveuu on 2010-12-03
Hi

I've been trying to do the same thing. The problem is that the M-Audio Fast-Track Pro appears as two separate stereo devices in ALSA (and therefore JACK?). At least this is the case using the generic USB driver. So regardless of JACK's sophisticated internal routing capabilities the challenge here is simultaneously using two separate output devices.

Or using a driver/module that sees the FT Pro as a single device with 4 outs. I don't know the solution though . .

PS thanks cchhrriiss121212 for your response to my other thread a while back . . I've been _reeaally_ busy.

---

