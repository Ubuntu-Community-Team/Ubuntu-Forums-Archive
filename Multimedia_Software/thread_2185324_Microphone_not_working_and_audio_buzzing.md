---
title: "Microphone not working and audio buzzing"
date: 2013-11-02
forum: Multimedia Software
---

### Post by LK_gandalf_ on 2013-11-02
Hi all, I just installed the new Kubuntu 13.10 32bit and I got problems with my microphone, and with audio in general. I have used Kubuntu for many years without having these issues before. 

The first issue: the microphone doesn't work, to activate it I have to run alsamixer. Here I have three options:
Mic
Internal mic
Internal mic 1

The only one working is Internal Mic, but at every reboot it switches back to the Mic 1.

The second issue: sometimes, randomly apparently, the speakers, both internal or external doesn't matter, start to buzz and make horrible sounds. I can only reboot to hopefully solve this. But it happens almost every day.


This is my lspci output:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

I have a Dell XPS M1530. Any idea and help on how to fix this would be appreciated.
Thanks :)

---

### Post by LK_gandalf_ on 2013-11-15
Hi, anyone could help?
Here the sound that comes out from the speaker. I noticed that it is made when Skype is open, if I close Skype then it disappears.

[https://dl.dropboxusercontent.com/u/27941815/Buzzing%20audio.m4a](https://dl.dropboxusercontent.com/u/27941815/Buzzing%20audio.m4a)

---

### Post by dave0109 on 2013-11-16
I've experienced similar issues for quite a while now.  Things got better when I got rid of pulseaudio and resorted to just using ALSA.  However, I still have issues with the mic, such that in order to hear anything that the mic picks up, I need to increase the gain, but increasing the gain creates large amounts of white noise, making it unpleasant through the headphones, so doing any kind of VoIP isn't practical.

It's one of the few things that I specifically have to fire up my laptop for, where the mic appears to be handled perfectly.

Same version of xubuntu is on both.

---

### Post by SeijiSensei on 2013-11-16
Make sure Kubuntu is using the right devices.  System Settings > Multimedia > Phonon > Audio Hardware Setup.

---

### Post by LK_gandalf_ on 2013-11-24
Hi and thanks for the reply. In settings I only see analogic internal audio for all entries, and in the tab "backend" there is only Gstreamer.

The main issue I'd like to solve is the microphone, it's very annoying that I have to change it at every reboot.

---

