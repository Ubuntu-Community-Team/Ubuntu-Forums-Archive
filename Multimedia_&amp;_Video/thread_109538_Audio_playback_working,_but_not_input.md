---
title: "Audio playback working, but not input"
date: 2005-12-28
forum: Multimedia &amp; Video
---

### Post by harisund on 2005-12-28
Hello everyone

My sound output is working, as in I am able to hear everything played on my computer. However, apparently it is not taking any sound from the microphone. 

I have a built-in ESS Maestro 3i sound card. 

I tried using Audacity and Skype and it doesn't record my voice. 

I know I am not giving enough details here, but does anybody know whether Ubuntu can not read the microphone by default and whether something needs to be done? 

Thanks !

---

### Post by paulmilliken on 2006-01-12
[QUOTE=harisund]Hello everyone

My sound output is working, as in I am able to hear everything played on my computer. However, apparently it is not taking any sound from the microphone. 

I have a uilt-in ESS Maestro 3i sound card. 

I tried using Audacity and Skype and it doesn't record my voice. 

I know I am not giving enough details here, but does anybody know whether Ubuntu can not read the microphone by default and whether something needs to be done? 

Thanks ![/QUOTE]
Type "alsamixer" and check that the volume is not zero on your microphone and that it's not muted.

---

### Post by harisund on 2006-01-14
[QUOTE=paulmilliken]Type "alsamixer" and check that the volume is not zero on your microphone and that it's not muted.[/QUOTE]

Wow .. paulmilliken.. thank you so  much.. you have just allowed me to use Skype on Linux and have saved me so many reboots ! 

I don't know why I didn't even think of this.. probably because a Windows installation automatically enables the microphone. Yes, my microphone was muted !

Thanks a ton again .. 

Hari

---

### Post by galgoz on 2006-01-15
I have this exact problem on two systems.  One one of them I actually tried a couple of different distros.  It was broken on Ubuntu and Mepis.  It did work on Debian.  The first two were using the same Kernel and Debian was using an older one.  I did read on several forums that people were having this problem.  It seems to be sorta widespread.

---

