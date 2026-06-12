---
title: "No sound on acer 6920g"
date: 2008-12-25
forum: Multimedia Software
---

### Post by Hardist on 2008-12-25
Hey peepz,

I've just installed Ubuntu on my notebook, an acer aspire 6920g. I'm a complete newbie to linux and haven't been able to fix my sound. I believe it has to do with the driver. Could someone help me out? Also, what to set when going to System -> Preferences -> Sound ?

Thanks in advance!

---

### Post by Hardist on 2008-12-26
Anyone?

I've tried to follow several topics on these forums and re-installed my ALSA driver, also downloaded the realtek HD audio driver and tried to install that, without any success.

---

### Post by Kevbert on 2008-12-26
Welcome to Ubuntu.
You may need to edit a file.
Go to Applications-Accessories-Terminal and enter the following:
```
sudo gedit /etc/modprobe.d/alsa-base
```
Enter your log-in password when prompted (it won't be visibly shown in terminal). Now add the following to the end of the file
```
options snd-hda-intel model=acer
```
Now save the file via the menus and then reboot the PC.
Please note all text is case sensitive in Ubuntu.

---

### Post by Hardist on 2008-12-26
Thanks,

I've done what you said, but without any succes. I might have overwritten some ' good'  drivers when trying to install the ' new'  ones? Maybe someone could post a link to which drivers I should install, or doesn't that matter?

---

### Post by Kevbert on 2008-12-26
You shouldn't need to install any extra drivers for sound. The other thing you could check is the speaker in the top right-hand corner of your screen. Right-click on it with the mouse and select Open volume control. Check that the sliders for Master, PCM, CD and PC Speaker are set to at least 50%. If any of these have a crossed speaker symbol, click on the symbol to remove the cross.
Good luck.

---

### Post by Hardist on 2008-12-27
Thanks, but that was the first thing I've checked ;-)

I have installed an older version of Ububtu, my friend helped me out. Also, the ALSA driver is installed succesfully and everything is enabled. I have installed the codecs to play mp3's and movies, but I do not hear any sound. It's frustrating :-)

---

### Post by dream_coder on 2009-09-13
put model=auto then reboot :)

---

