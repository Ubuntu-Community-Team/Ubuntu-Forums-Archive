---
title: "ALSA not working"
date: 2009-04-02
forum: Multimedia Software
---

### Post by vish91 on 2009-04-02
I have YMF-724F [DS-1 Audio Controller] sound-card connected to my pc. The driver didn't came with my ubuntu installation[gusty-7.10]. My sound card is supported by ymfpci module of ALSA.

So I downloaded latest release of ALSA from ALSA-PROJECT official site. I followed the instructions provided 
 1. by ALSA documentation for module ymfpci. 
 2. [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
 3. [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
 4. [https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard](https://wiki.ubuntu.com/UbuntuStudio/HowToInstallTheLastAlsaDriverForProSoundCard)

Though it installed and compiler without any error, it still didnt detected my card. 

A weird thing that happened yesterday that everytime I boot it sometimes detected and sometimes not(now its not happening). I removed he package completely and tried using debian packages from ubuntu repository using apt-get and also downloading sources using apt-get and then compiling. But still didnt worked, it compiled, installed nicely, but didnt detected my card. 

I also used **alsaconf** which detected my sound card and configured it, but still when I tested it with **aplay -l**, it show no devices found.

Right now I'm using OSS and its working fine, but still I want to troubleshoot this problem with ALSA. Please help me out!

---

### Post by johnjohn2 on 2009-04-02
Alsa was problematic for me and that is now why i am running pulse.

If oss is working as it should it would be prudent to mess around whilst you do have sound.

---

