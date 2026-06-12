---
title: "You Tube sound?"
date: 2009-03-24
forum: Multimedia Software
---

### Post by rodney757 on 2009-03-24
I just switched over to Ubuntu and am having trouble getting sound from Youtube or other flash players. I get sound on startup just not from flash players. I've tried the stickie and it didn't work. In pluse audio it says that there is no output device? Advice would be appreciated.

---

### Post by khelben1979 on 2009-03-24
What flashplayer are you using? 

The flashplayer from [the Adobe website]("http://www.adobe.com") definitely have the best one.

---

### Post by rodney757 on 2009-03-24
Yeah I'm using that one but I have no sound. I get video but no sound.

---

### Post by miegiel on 2009-03-24
I'm guessing it's 1 of 2 things. You're missing an audio codec or another program (some player for example) has hijacked the sound for itself alone.

---

### Post by gandaran on 2009-03-24
> **rodney757 said:**
> I just switched over to Ubuntu and am having trouble getting sound from Youtube or other flash players. I get sound on startup just not from flash players. I've tried the stickie and it didn't work. In pluse audio it says that there is no output device? Advice would be appreciated.
can you provide details, which ubuntu version 8.04 or 8.10, 32-bits or 64-bits? and which flash package have you installed!
usually you get flash sound problems if you are using adobe flash 9, flash 10 can fix those problems, if you still have flash sound issues with flash 10 then you have to fix[ pulseaudio]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by rodney757 on 2009-03-25
Sorry for not giving that info. I'm running 8.10 and I believe its the 32-bit. How do I make sure? I have adobe flash 10 installed. I tried setting up pulseaudio but it says I have no output device? Thanks

edit: When I type the command uname -a I get this, which I believe is 32bit correct?

Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

edit 2: Okay, I tried the pulseaudio guide again and I got it to recognize my output device, but when I logged out and then back in, pulseaudio said that I didn't have an output device installed. I guess it didn't save my settings. How do I get pulseaudio save my settings?

---

### Post by gandaran on 2009-03-25
> **rodney757 said:**
> Sorry for not giving that info. I'm running 8.10 and I believe its the 32-bit. How do I make sure? I have adobe flash 10 installed. I tried setting up pulseaudio but it says I have no output device? Thanks

edit: When I type the command uname -a I get this, which I believe is 32bit correct?

Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

edit 2: Okay, I tried the pulseaudio guide again and I got it to recognize my output device, but when I logged out and then back in, pulseaudio said that I didn't have an output device installed. I guess it didn't save my settings. How do I get pulseaudio save my settings?
heres another guide for fixing sound problems 
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by rodney757 on 2009-03-25
Sweet, I got it working now. Thanks alot for the links.

---

