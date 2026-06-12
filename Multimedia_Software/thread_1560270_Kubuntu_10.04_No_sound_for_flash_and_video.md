---
title: "Kubuntu 10.04: No sound for flash and video"
date: 2010-08-24
forum: Multimedia Software
---

### Post by jurco on 2010-08-24
Hi guys, please help me, I am a newbie.

I installed Kubuntu 10.04 and found out that there is no sound for flash in firefox. Also I here no sound when playing local video files (VLC, KMPlayer).

I checked kMix and everything is on. I tried to install pulseaudio,  but I am not sure about it. Last time I saw it couldnt connect to some server or what... Although I can hear system sound and Amarok 2 plays mp3. I didnt mention that I tried to install libflashplugin and kubuntu restricted extras.

This is bad :( Could someone please instruct me to solve this? I would like to use Lucid, but this annoys me a lot...

---

### Post by slooksterpsv on 2010-08-24
A couple of questions:
1. What kind of computer is it? Laptop or Desktop? Gateway, Acer, Asus, etc.?
2. Open Terminal (KDE Menu -> Accessories -> Terminal) and post the output of the following commands using the # button when you reply to the post:
```

lspci

lshw -C sound

```

Then we can further help =D

---

### Post by LarsUb on 2010-08-24
After you've performed what SLOOKTERSPV told.. that would just indicate your hardware is detected.

Verify the driver modules are being loaded. 
$ lsmod | grep snd       
(if this fails, re-install your card's driver, verify your model and  chip with the output from $ lshw )

Check if the mixers are detecting your card.
$ aplay -l
$ aplay -L

Try a test for your soundcard with this tool (works with alsamixer)
$ speaker-test -D default

Set your preferred mixer for all applications in System > Preferences > Multimedia system selector.

If everything goes OK, just try with the settings/preferences/plugins in your programs.
Good luck!

---

### Post by LarsUb on 2010-08-24
After, your sound is correctly working...

Re-install the flashplayer plugin, for mozilla

---

### Post by lovinglinux on 2010-08-24
[http://www.shcherbyna.com/?p=866](http://www.shcherbyna.com/?p=866)

---

### Post by jurco on 2010-08-25
Wow guys thanks. It was probably pulseaudio problem. I did what lovelinux adviced and now there is sound (on video and flash). Yesterday I tried the same procedure and it didnt work. Probably restart needed .... :-/ Anyway. Thanks a lot.

---

