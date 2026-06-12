---
title: "Jaunty updates spanked my sound!"
date: 2009-06-26
forum: Multimedia Software
---

### Post by tixetsal on 2009-06-26
A recent (the past week) jaunty update p4wned my audio. I tinkered with reinstalling packages, changing group memberships, alsa, salsa, oss, pulse, and cheese-dip and bean burrito. Heck, I even sacrificed some small animals to the great jackalope, but I can't figure out what went wrong.
I was not sure what the catalyst was, so I reinstalled. The sound worked great until my first update and reboot, so it is definitely related to an update, though I am not sure which one.
I am running 9.04 amd64 on a ECS GF8200A (V1.0) ATX AMD Motherboard with HDMI Audio turned ON in the BIOS, although the audio I am referring to is desired from the audio jack in the back of the computer (not sure if the HDMI BIOS option is a factor), and I switched the video feed over to DVI because I thought that maybe using HDMI was "confusing" the kernel.
Before I reinstalled the only device that would show up was the HDMI audio out, now aplay -l yields this message:

shaun@brpc:~$ aplay -l
aplay: device_list:217: no soundcards found...

My volume control options seem to be much more limited than they were before the updates. I'm going to try reinstalling with the HDMI audio BIOS switch turned off, but I have no guarantee that this will remedy this issue. I am grasping straws...

Meh!
tixetsal is online now Report Post   	Edit/Delete Message

---

### Post by lovinglinux on 2009-06-26
I agree if your assessment. There are several threads posted the last two days complaining about lost sound after an update.

Nobody knows the culprit yet.

---

### Post by RedSingularity on 2009-06-26
Yeah i have been seeing a lot of this same problem with the update.

---

### Post by tixetsal on 2009-06-27
I discovered that by booting 2.6.28-11-generic, instead of 2.6.28-13, my audio was restored, as long as I booted that kernel.
I have reinstalled about 6 times in the past day-and-a-half.  It's time to kick back and watch bladerunner...

---

### Post by lovinglinux on 2009-06-27
> **tixetsal said:**
> I discovered that by booting 2.6.28-11-generic, instead of 2.6.28-13, my audio was restored, as long as I booted that kernel.
I have reinstalled about 6 times in the past day-and-a-half.  It's time to kick back and watch bladerunner...

Thanks for the info. Maybe you should post bug report on Launchpad.

---

### Post by iamajd on 2009-07-07
I encountered this problem too and couldn't find an answer no matter how I worded "2.6.28-13 killed sound" in my Googling.  Then I remembered an old fix I had to do before.  I checked Volume Control and set PCM back to 100%.  Viola!  Good as new.  Maybe (hopefully) this will work for you (or at least someone else who stumbles upon this thread).

---

### Post by tixetsal on 2009-07-07
> **iamajd said:**
> I encountered this problem too and couldn't find an answer no matter how I worded "2.6.28-13 killed sound" in my Googling.  Then I remembered an old fix I had to do before.  I checked Volume Control and set PCM back to 100%.  Viola!  Good as new.  Maybe (hopefully) this will work for you (or at least someone else who stumbles upon this thread).

I appreciate the suggestion, but unfortunately, my sound issue is more complicated than that.  My audio device (sound card) does not even show up as an option.

Here's some more 411:  [http://ubuntuforums.org/showthread.php?t=1197673](http://ubuntuforums.org/showthread.php?t=1197673)

---

### Post by jstnhickey on 2009-07-07
Similar situation here.  My sound became jumpy and now skips just starting last week.  
Any suggestions would be helpful.

---

### Post by tixetsal on 2009-07-24
My sound was miraculously restored about 2 weeks ago, even before all of the PulseAudio updates rolled out.  I did install some codecs for multithreaded encoding / decoding around that time, but I'm not sure if it was an update or my own accidental tinkering resolving the problem.

---

