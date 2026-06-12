---
title: "microphone working once, then not at all"
date: 2016-06-05
forum: Multimedia Software
---

### Post by Jeremy_LeFevre on 2016-06-05
Hi, I installed Xubuntu 12.04 a while ago (CAE version of linux). I can't use updates without losing access to terminal. So, I'm kind of stuck with this version if I want all the nifty add-ins and such. My computer is an HP G70 laptop (HP G70 463CL).

So, I was hoping to record audio with my microphone for a video. Normal sound output has never given me a problem (output through speakers or headphones).

Microphone (internal and line-in both not working), on the other hand, is kind of not working, at all so far as I can tell. I've tried the following fixes recommended on forums:

1. Install/run alsamixer, edit lines in alsa-base.conf, using "sudo medit /etc/modprobe.d/alsa-base.conf" minus the quotes of course. Attempts include:
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto
options snd-hda-intel position_fix=1 enable=yes
I have tried various options for the "model=" field, including auto, hp, dv5, and a few others.
2. I've tried installing and reinstalling pulseaudio and pavucontrol various ways, with no results that have worked.
3. I've tried unmuting (default is unmuted for me), changing sampling rate from 44100 to 96000 Hz (which is what the hardware on my system seems to default to, while the software defaults to 44100 Hz even after I have changed/updated it to 96000 Hz). Of course I've also tried unlinking the channels, lowering the volume in one channel, still nothing.

I had it working one night before I went to sleep, and when I came back the next day to record my video, no sound. I can't remember what I changed right before it started working, but it was no longer working when I came back the next day. Basically, when I pull it up in pulseaudio for a test, it shows a low level of noise, then stops trying to receive input altogether (audio input bar freezes up). I've recorded it from terminal using arecord, and it's a low buzzing noise. I've tried tapping the microphone or speaking really close into it, with the input volume up, but it doesn't respond to anything, just a low buzzing noise.

Any suggestions? I noticed on this forum a suggestion for what troubleshooting steps to take before posting, but I'm not sure how up to date it was, and it said something about 3 hours of work just to get things working correctly. Like most reasonable people, I don't want to waste another 3+ hours just to find out it still won't work at the end. Plus, my sound itself is working, just the microphone is having issues. Again, not excited about a 3 hour tutorial/instruction for troubleshooting, but I might try it out. If that fails, I think I'll say goodbye to Ubuntu, and trade it back for Windows Vista. If that doesn't motivate people to help me, I don't know what will. (Truth is, I'll probably just find another version of Ubuntu that works with my hardware and just manually install the software I use, but just pretend I'm going to reinstall Vista or some other OS that linux users hate, so you feel the need to find a solution).

---

### Post by Jeremy_LeFevre on 2016-06-05
Oh, by the way, I found [this one]("http://ubuntuforums.org/showthread.php?t=1043568") the most helpful for determining what lines to add to alsa-base.conf, and I haven't tried all of the hp ones, just ones I thought most likely to be similar to my G70. No real luck though.

Ironically, I read [here]("http://voices.canonical.com/david.henningsson/2012/07/13/top-five-wrong-ways-to-fix-your-audio/") that changing the model is exactly one of the things not to do.

So, with all the conflicting information and the methods that I've tried, as recommended by forums, have not really got me anywhere on this. Being as new to linux as I am, I have very little feel for how to go about troubleshooting, and usually need to know exactly what command to run or what to install in order to fix a given problem. Usually it's straightforward, but when it comes to making sure the correct drivers are in, this goes beyond my current level of experience.

---

### Post by Autodave on 2016-06-05
I have no answer for you: sorry. But, I can't hep but wonder why you don't upgrade to the newest version (16.04) before going through all of this.  Your version is pretty much dead now.

---

### Post by Jeremy_LeFevre on 2016-06-05
Right, that's kind of what I'm leaning towards anyway. However, it means I have to give up using the CAE built-in nifty stuff. However, I'm finding I don't use most of it, so I'll probably end up installing the newest version, then installing the specific tools that I use, unless somebody comes up with some sort of genius plan to fix it as is. I'm not sure why, but the CAE version bricks terminal upon upgrading. Why on earth would they think it's a good idea to set it up like that, I don't know. CAE version looks like it's all but dead, as they haven't bothered to keep it current to any new version of Linux GUI OS, so far as I can tell.

---

### Post by howefield on 2016-06-06
Have a look at this thread if you haven't already.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Scroll down to the "* Restore Default Configurations*" part.

---

### Post by gfloria-edoctores on 2016-12-01
Im having the same issue.

Mic was working great an suddenly stopped working. No I have to push up the mic level for it to record my voice, but then it records white noise and is unconfortable, to the point that is useless.
My current Ubuntu version is 16.04 TSL.
According to lspci, my Audio devices are:

00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)


Im using an external headset that works fine on other computers.

Thanks in advance

---

