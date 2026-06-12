---
title: "Skype audio and missing volume indicator. Help!"
date: 2011-07-13
forum: Multimedia Software
---

### Post by K1251 on 2011-07-13
Ok, basically I was having some problems with the audio in skype, and as per the instructions on [this page]("https://help.ubuntu.com/community/SkypeTroubleshooting#Audio Problems"), I ran ```
sudo apt-get purge pulseaudio && sudo apt-get install esound
``` (note: using apt-get not aptitude). 

The only effect this had was to remove the volume indicator/menu from unity's top panel and didn't fix the sound in skype.

So I did ```
sudo apt-get purge esound
sudo apt-get install pulseaudio
``` and the volume indicator is still missing. And the audio still doesn't work in skype.

Help?

---

### Post by K1251 on 2011-07-13
Update: I got the volume menu back by doing ```
sudo apt-get install indicator-sound
```

So now the main problem is the audio in skype. Any sounds made through skype, whether it's the sign in sound or someone talking, even the test call, are really distorted and crackly. And it's only skype that does it, sound is fine everywhere else.

---

### Post by K1251 on 2011-07-14
Bump.

---

### Post by lidex on 2011-07-14
Have you disabled the option to allow skype to control audio levels?

---

