---
title: "Sometimes audio works and sometimes it doesn't"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by dancantong on 2007-05-21
Hi!
I have a little problem with Ubuntu audio playing. Sometimes I start Ubuntu and I can't hear any sound. I have to restart the computer, till I have normal sound playing. This happened from time to time, but it's beginning to happen more frecuently.
I have Ubuntu 7.04 installed, upgraded from 5 to 6 and now to 7.
I don't like the idea of installing again the OS.
Hope anyone help me with this.
Thank you in advance.

---

### Post by dancantong on 2007-05-23
I have two audio cards, one Sound Blaster and another that came with the motherboard and I don't use.
Any help with this, please?:(

---

### Post by BobLand on 2007-05-23
Have you looked at and run 
'Comprehensive Sound Problem Solutions Guide v0.5e'?  [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

I have an nVidia GeForce4 card.  It took a bit of fiddling to get it to work.  I have the same issues with sound going on and off.  

Here's what I do when I loose some sound or all sound.  Run the following 3 lines of code and reboot.  This assumes you ran the procedure from the above linke.

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop

Hope this helps,
bobland

---

### Post by Turgon on 2007-05-23
I had this problem back in horay and breezy. It was caused by my two soundcard, that was switching place as primary and secondary. This can be set in the sound configure-app in the system meny, but you might get it fixed permanently if you just disable the onboard soundcard in the bios.

---

### Post by stchman on 2007-05-23
> **dancantong said:**
> Hi!
I have a little problem with Ubuntu audio playing. Sometimes I start Ubuntu and I can't hear any sound. I have to restart the computer, till I have normal sound playing. This happened from time to time, but it's beginning to happen more frecuently.
I have Ubuntu 7.04 installed, upgraded from 5 to 6 and now to 7.
I don't like the idea of installing again the OS.
Hope anyone help me with this.
Thank you in advance.

Problem is you need to set a default sound card.  I had the same problem with Feisty until I did this:

[http://www.stchman.com/mult_sound.html](http://www.stchman.com/mult_sound.html)

I worked for me.

---

### Post by dancantong on 2007-05-25
Thank you very much, mates. It works.
I think this problem should be fixed by Ubuntu team.

---

### Post by Eddie Wilson on 2007-05-25
Also it should be noted that the audio built into the motherboard may still be detected by Ubuntu even if you disable it in the BIOS. Thats what happened to me.
Eddie

---

