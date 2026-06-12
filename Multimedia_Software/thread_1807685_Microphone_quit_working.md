---
title: "Microphone quit working"
date: 2011-07-19
forum: Multimedia Software
---

### Post by Benchrest on 2011-07-19
My internal microphone has been working fine till last night. Would not work on skype. Found it doesn't work at all. Was working two days ago. I have not intentionally messed with it.  I do know I had a gstreamer update yesterday and I hooked my laptop up to a TV with twinview for the first time since it last worked. The hardware is ok as it works in dual boot with indows. Now I am afraid I have changed so many things trying to get it to work I may have really screwed it up. I am going to try and external microphone later today. 
I have used alsamixer to make sure volumes are ok plus set volumes from top bar (I use Gnome) My laptop info is at bottom of screen.  I believe I have conexant audio chip.

---

### Post by Benchrest on 2011-07-19
I've tried an external microphone and it doesn't work either. I tried both internal microphone and analog microphone settings.  

Is there a way to reinstall the new installation configuration files for sound short of a complete reinstall? Just reinstalling the software will not change the configuration files I would assume. I say that because my microphone worked right out of the box with 11.04 32 bit.  I am assuming some parameter got changed.  I did reinstall Alsa and Pulseaudio with no help.

---

### Post by Benchrest on 2011-07-19
I booted up the Natty installation disk and the microphone works fine.  But all the installation files appear compressed somehow so I couldn't see folder etc which I think contains my configuration files.

---

### Post by Benchrest on 2011-07-19
Oh the evil webs we weave when using the keyboard.  I found my problem.  When my skype call came in last night I was using audacity to edit an audio file.  Nothing todo with the microphone.  But I hurriedly shut it down to take the skype call.  I just brought up audacity to edit that file and noticed my input device was "default:ExtMic:0"  That didn't look right so I looked at the options and saw "pulse: IntMic:0" and set to that.  Now my microphone works.  Somehow I changed it.  But I question how making a change to Audacity for the application should make a system wide change.

---

