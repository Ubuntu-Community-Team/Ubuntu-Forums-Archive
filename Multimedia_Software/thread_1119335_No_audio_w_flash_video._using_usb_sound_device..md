---
title: "No audio /w flash video. using usb sound device."
date: 2009-04-07
forum: Multimedia Software
---

### Post by mthomps on 2009-04-07
Hello everyone.

I'll try to explain my problem to you as clearly as I can. I've searched extensively and I cannot find anything involving my device on the internet for this problem.

Basically, I use an outboard usb sound device (creative x-fi sb1090) I use it for the optical out which I connect to my stereo receiver. Sound works great for everything, except flash videos. I can see the video no problem, but the sound does not come through the device. 

To test I plugged a pair of headphones into my integrated onboard sound. Flash comes through no problem. The odd thing is that even though my out board sound is selected through the gui, it still goes through the integrated board. An mp3 player played through rhythm box will come through the out board device, but for some reason flash will not.

Today I tried disabling the integrated audio in bios. This did not do the trick. The only difference now is that while sound from all other apps runs through the out board device to the receiver, the volume control on the panel is disabled, and it says it does not detect a device or there is no gstreamer plugin. My out board device IS selected through the sound control gui though. I used apt-cache search to try to find any gstreamer plugins i may not have. None of them help me. 

I've encountered many problems since beginning to use ubuntu. (I love linux so far.) on my own or through research I've been able to get passed them, but this one has brought me to my knees. I do not think I can give up this device, because watching southparkstudios.com on my dual 22inch flat screens with crystal clear sound through my stereo system is very important to me /end bragging :p

---

### Post by mthomps on 2009-04-08
This got pushed to the bottom of page two rather quickly. I'm going to give it a bump in case there's any hope.

---

### Post by mthomps on 2009-04-08
Last bump :-/

---

### Post by uuser3000 on 2009-04-08
Bump!!!

---

### Post by mthomps on 2009-04-08
I appreciate the help :guitar:

---

### Post by markbuntu on 2009-04-09
Do this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Then the nesxt time you play a flash open the pulseaudio volume control/playback tab and right click on the flash stream and choose move stream. You can leave your on-board sound enabled if you want.

---

