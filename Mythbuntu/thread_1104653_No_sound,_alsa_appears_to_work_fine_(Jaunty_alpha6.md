---
title: "No sound, alsa appears to work fine (Jaunty alpha6.1)"
date: 2009-03-23
forum: Mythbuntu
---

### Post by maxim99 on 2009-03-23
I just installed alpha6.1 on my [DG45FC](http://www.intel.com/products/desktop/motherboards/DG45FC/DG45FC-overview.htm) system which I had alpha3. I'm looking to get the 6 channel audio working properly which. With alpha3 I was able to atleast get stereo out of the unit, but with alpha6.1 I get no sound EXCEPT for a Beep when I click "Shutdown" from the Main Menu Logout box. I found this out the hard way by turning the volume up all the way on all of the pots and the pot on my headphones. Bad combination.

Regardless, everything appears normal except for this file here:

```
maxim@mythbuntu:~$ cat /proc/asound/card0/pcm0p/sub0/hw_params 
access: MMAP_INTERLEAVED
format: S32_LE
subformat: STD
channels: 2
rate: 48000 (48000/1)
period_size: 1024
buffer_size: 8192
```The card is a 6 channel on-board card built into the motherboard, however alsa appears to say it's 2 channels?

Alsamixer has all of the channels
I'm able to play things with aplay and it doesn't produce and error
I'm able to install pulseaudio, look at the volume meter and see it move while playing audio.
It's just there is no sound produced when I play anything. It's like everything is being played into null, but it thinks it's being played to the audio jacks.

I've also tried this line here in /etc/modprobe.d/alsa-base:
options snd-hda-intel model=5stack

It doesn't seem to make a difference.

I've used asoundconf, and asoundconf-gtk to set the default card to "Intel". There is no /etc/asound, but instead a /home/maxim/.asoundrc.asoundconf which contains the config for alsa.

I'm at a loss as to why the sound doesn't work except for a single solitary BEEP when I click shutdown through the UI in xfce4.

---

### Post by Nobodyspeshul on 2009-03-24
I'm pretty new to these forums and linux in general, but check out this website, see if it helps any.

[http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto](http://www.mythtv.org/wiki?title=AllensDigitalAudioHowto)

---

### Post by maxim99 on 2009-03-24
Thanks for trying.

---

### Post by dragoster on 2009-03-24
Have you tried to see which programs are using the sound card?

```
sudo lsof /dev/snd/*
```

Also, try reinstalling the latest alsa with [this script]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810").

Good luck!

---

### Post by maxim99 on 2009-03-24
Upgrading Alsa worked out of the box. Thanks for suggesting that! The version that the script upgraded me to is 1.0.19. I had to make no configuration changes in order for it to work. Let there be sound!

Also all six channels work! ohhh so exciting!

Actually I have noticed so far that the LFE channel appears to output full range audio, i'm not sure if that's because i'm playing a stereo source, and it's not setup for that, or if the sound card is actually supposed to crossover the higher frequencies internally. I'll have to look closer to find out more.

---

