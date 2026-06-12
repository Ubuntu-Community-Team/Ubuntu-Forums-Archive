---
title: "No Sound on Speakers and Headphones for 11.10 onHP dv6"
date: 2011-10-25
forum: Multimedia Software
---

### Post by Kreme191 on 2011-10-25
Hello,

I just installed 11.10 and I no longer have sound from my speakers and headphones. When I first installed 11.10 my speakers worked fine, including a heat sync button on my keyboard which changes color when I mute the speakers. I read other forums trying the fix the headphone problem, but that just made it so my speakers no longer work. I went to the sound settings and tried every possibility, both in the hardware tab and output. Since my mute button no longer changes color as well, I think I made it so my sound card is not longer recognized but I don't know, I'm pretty new to Ubuntu. Below is the command I entered before that I think killed my speakers.

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-kareem -r linux-ubuntu-modules-kareem -r libasound2

Thanks in advance cause I really miss my tunes.

---

### Post by mundbora on 2011-11-15
I had no sound through my headphones until I set my output to Analog Speakers. Now it's perfect. You might have messed up something now though...maybe a repair and then try this.

---

### Post by normworthy on 2011-11-15
I had sound until a couple days ago, then I had nothing. 
I think it may have been an update on 11.04.
I upgraded to 11.10 and have no sound.
I used an earlier version 8.04 I think it was and sound was OK.
My settings are CA0106 Soundblaster
1 output/1 input
Analog Stereo Duplex
this is what it was in 8.04 and the same in 11.10

any ideas?

---

### Post by zholistic on 2011-11-15
What application are you using to listen to sound?

---

### Post by NewReformist on 2011-11-16
> **normworthy said:**
> I had sound until a couple days ago, then I had nothing. 
I think it may have been an update on 11.04.


I have the same problem, but atleast I still got sound from my headphones. Seeing I'm not alone I'm pretty sure now it has to be an update in 11.04, but which one? Is there a chance to reverse that one?

[http://ubuntuforums.org/showthread.php?t=1879728](http://ubuntuforums.org/showthread.php?t=1879728)

---

