---
title: "Sound not as loud as it should be?"
date: 2011-08-18
forum: Multimedia Software
---

### Post by Son of MaxVK on 2011-08-18
I've started using Ubuntu more that WindowsXP on my dual boot recently and I have noticed that the sound on Ubuntu is never as loud as it is in XP, all of the options in the settings are at full but the sound never gets any louder now and I have no idea about how to fix this. Anyway off making it louder would be appreciated, its nightmarish not being able to deafen myself.:(

---

### Post by PeteAsdf on 2011-08-18
Same issue here on Kubuntu 11.04 64bit. The weird thing also is that when I try to adjust the sound volume via the sound icon in the GUI, the volume level doesn't change at all. I can only adjust the volume on my external speakers.

Thanx

---

### Post by lidex on 2011-08-20
Try pulse audio manager. You'll probably need to install it:
```
sudo apt-get install paman
```
When you run it, select the sink on the deice tab, click 'Properties' and adjust the level there or do it via sources on the same tab.

---

