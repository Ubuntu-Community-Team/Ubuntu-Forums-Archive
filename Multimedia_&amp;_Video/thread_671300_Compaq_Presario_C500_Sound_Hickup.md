---
title: "Compaq Presario C500 Sound Hickup"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by ldclan on 2008-01-18
I have read that the Compaq C500 has issues with headphone sensing.  Basiclly when you plug in your headphonea the main speakers are still on. 
I have read on the forum that people had to recompile the audio drivers to correct it, because it is a bug in ALSA.

Well I am a newbie and I have this model laptop with Ubuntu 7.10 installed.
Would any body give a detail walkthough to fix the problem for me.
I am quite unsure about doing it. Any help would be greatly appreciated.
Thank you.

Regards,
ldclan

---

### Post by dfort on 2008-02-01
It doesn't need to be that complicated.

 echo 'options snd-hda-intel model=laptop' >> /etc/modprobe.d/alsa-base
 Reboot.

Basically, you need to tell the ALSA driver that you're running a laptop and that will mute the speakers when you plug in headphones.

So you've got sound working on a Compaq C500? I used to have sound working but apparently an automatic kernel upgrade killed it and I haven't been able to get it back. I went through building the ALSA components from source but that didn't work. Even a complete re-install didn't do it.

In other words--my speakers are on mute!

---

### Post by sethmoyer on 2008-02-10
Have you tried running alsamixer?  That happened to me before until I turned "PCM" up the whole way.

---

### Post by dfort on 2008-02-11
Yes, I tried turning up PCM and Master on the alsamixer to 100 but still nothing. 

Funny thing is that the sound worked on my first install then it went away and nothing I tried fixed it so I did a complete re-install. At first the new install didn't have any sound either but then after one of the ubuntu updates it started working--hurray! All was fine until I needed to boot into Vista (which I keep on a separate partition) and ever since then the audio on ubuntu is once again dead. Everything else works fine and the audio works in Vista so I know that the hardware isn't dead.

---

