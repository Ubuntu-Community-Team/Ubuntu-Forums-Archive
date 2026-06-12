---
title: "Severe Audio Stuttering in Jaunty"
date: 2009-04-17
forum: Multimedia Software
---

### Post by planegenius on 2009-04-17
I just upgraded to Jaunty tonight and one of the first things I did after upgrading was watch a YouTube video.  While I was browsing in another tab, the audio started to stutter badly.  After closing Firefox, it continued to stutter severely.  After a restart, the audio no longer stuttered, but I was able to reproduce the problem.  However after a second restart, it did not fix the skipping, and my audio stuttered without launching a flash video.  This makes me think its not a flash problem.  I have been looking around and hear that there is an issue with pulseaudio in jaunty.  Is that what needs fixed? 

Can someone please help me fix this issue.

Thanks

pg

---

### Post by marks_linux on 2009-04-17
I can make sound playback stutter by doing other file operations with ease, is it the same problem?

Not yet experimented with buffering in Music PLayer or VLC as yet

---

### Post by planegenius on 2009-04-17
A lot of people seem to be talking about stuttering problems when using the music player, but this seems to be a different problem.  I was in firefox playing a flash video.  When I casually browse the net (in another tab) while the video is playing, the audio stutters badly, and does not stop.

---

### Post by planegenius on 2009-04-18
Anybody? Still no luck...

---

### Post by planegenius on 2009-04-18
Right now, my sound does not work **at all**! Restart after restart, I go into sound preferences and test the aduio, and it just keeps stuttering.  It is constant and does not stop.

Should I go back to Intrepid or is this fixable?

Any help please??

---

### Post by markbuntu on 2009-04-19
There are a few ongoing threads about pulseaudio in the Development and Testing/Jaunty forum. Maybe you should check them out.

---

### Post by planegenius on 2009-04-22
A few days ago, I got onto IRC and asked around about this.  Someone sent me this link-

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/336965/comments/7](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/336965/comments/7)

Instead of adding 'tsched=0' I removed it.  This fixed the audio lockups I was experiencing.  At this point, the audio is still not perfect, I still get some minor scratching and stuttering, but nothing compared to the original problem.

Thanks

---

### Post by weblordpepe on 2009-05-01
Me too here.

I have isolated that it is a software issue, and not a hardware, driver, or even application issue. 

It's something to do with either the PulseAudio framework, or some other audio framework kernel module.

Stuttering occurs with every Application interface: OSS, Alsa and Pulse AND Jack.
Stuttering occurs with both SB Live PCI card and Nvidia CK804 onboard chip.

Every user application skips.
So much it makes sound completely unusable. And its only since I upgraded to Jaunty.

I already have the "load-module module-hal-detect tsched=0" line in my config as suggested by the previous post. 

At the moment, I am yet to try PulseAudio version pinning.

---

### Post by psyke83 on 2009-05-01
See [bug #345627]("https://bugs.launchpad.net/bugs/345627"). There is a test kernel available to resolve this issue.

If stuttering persists, take a look at my PulseAudio guide.

---

