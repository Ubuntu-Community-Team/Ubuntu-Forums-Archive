---
title: "NVidia GeForce 8200 w/ Realtek ALC888 Sound Problems Resolved"
date: 2008-09-19
forum: Multimedia Software
---

### Post by resonantfreq on 2008-09-19
I have an Ubuntu 8.04 system on a NVidia GeForce 8200 MB that has a Realtek ALC888 sound system.

I have had problems ranging from:

No sound
Cracking and popping sound
GStreamer errors
etc etc

There is support for realtek hardware in Linux 2.6 kernels available from realtek, goto [www.realtek.com](www.realtek.com), choose drivers, search for HD Audio Codec Driver.  You need to have this file downloaded and ready to go.

If you look at the install, you will notice they do a lot of things with alsa.  I had in the past installed, re-installed, etc., alsa, pulseaudio, gstreamer pugins, esd, etc etc etc.

So what I did to get sound working is this, and I am not claiming that all of these steps are necessary, its just what I did:

dpkg -l | grep gstreamer
dpkg -l | grep alsa
dpkg -l | grep pulseaudio

then I did 

sudo aptitude remove --purge

for each package.

Note: at one point, the remove logic got screwed up and it thought I didn't need a lot of my gnome-desktop apps and utils and it removed them, so be careful and look at the text of what it is going to do before blindly pressing 'Y' in response to the remove script.

I was not successful in removing every last package, but I did as many as I could.

Next I went to see if esound was running by

lsof | grep dsp

and sure enough esd was running; I killed the process and removed esound packages from my install

<*> see below

Then I ran the realtek install as per their directions, it found the HD audio stuff, and got to the very end, where it did not play the text sound.  This turned out to be OK for me.

<*> As it turned out, I needed to

sudo apt-get install libasound2-plugins
sudo apt-get install alsa-utils

before the realtek program would work cleanly, if you do this before, you might save a step or two.

At this point, the realtek install would run through cleanly up until the very end where it would not play the test sound.  By scrolling up thru the text, I found it was complaining about PULSEAUDIO.

I found a thread somewhere that suggested:

sudo asoundconf unset-pulseaudio

This did the trick, and everything worked fine at this point.

I will point out that sound from VLC still had some slight pops and crackles, but it is a VLC problem; audacious runs perfectly.

This is from memory as I did not take notes, so hopefully it will help someone or two... the whole sound ordeal took me about 3 weeks of off and on attempts.

Good luck.

---

