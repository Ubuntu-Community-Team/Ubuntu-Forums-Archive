---
title: "Only mono sound in headphone"
date: 2010-08-27
forum: Multimedia Software
---

### Post by Rilion on 2010-08-27
Hello!

I'm new to Ubuntu, this is the second time I've installed it (I had enough of XP). With careful planning and thinking, I managed to get a few things working, like high resolution, java plugin, and flash. But there's a problem I encountered during listening to music:

My headphone has only sound in the left speaker. I took a glance at System>Preferences>Sound, and I tried a couple options, but nothing worked. 

Some generic information:

- I have an integrated sound card (into an ABIT KD7 motherboard).
- My headphone is a Thomson WPD265, which is working perfectly.
- Neither YouTube, nor .flac audio plays in stereo.

I request your help in solving this problem. I tried to google the problem, but this thing seems to be a bit rare. I'm sure this problem is related to software, since everything went fine under different circumstances (XP). 

Thanks in advance,

Rilion

P.S.: It turns out that neither the speaker system is working - only the front left works from the five, and 5.1 output laggs. Any idea?

---

### Post by lidex on 2010-08-28
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by torboxz on 2010-10-18
Hi, first of all I'm sorry for bumping this old thread.

I think I got the same problem. At first I thought my headphone jack is the culprit being broken or something (office desktop) but the same thing happened on my home desktop and my netbook. (Same iso)

Internal speaker output is OK. The problems start when I plugged in my headphone, internal speaker is muted which means OK but my headphone output becomes 'mono-ish'.
I can hear the music but I can not hear the vocal, seems like karaoke mode is on which I don't have anything to do with it.

The interesting part is when I open my sound preferences and slide the balance slider to far left or far right, I can hear it perfectly (that means mono output, right?) but when the slider is in the middle (should be stereo, right?) it will becomes like karaoke sound; music but no vocal.

My headphone is good (logging into win7).

Here is my alsa link
```
http://www.alsa-project.org/db/?f=cb5a798e9a65aa7dc6022aa57e7ce0147ccf843a
```

Please help me.

---

### Post by P4man on 2010-10-18
lidex is the expert on this, Im just guessing, but it sounds like you are ouputting 5.1 audio to your headphone. Try going to sound preferences, hardware, profile, and set it to analog stereo duplex.

---

