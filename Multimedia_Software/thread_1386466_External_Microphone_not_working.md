---
title: "External Microphone not working"
date: 2010-01-20
forum: Multimedia Software
---

### Post by amir.kadivar on 2010-01-20
Hey guys,

I just installed Gnome-Alsa mixer to control what is happening in the different channels of my system's sound. My internal built-in microphone works just fine, but I cannot turn it off and use the external mic (I tested it in windows and it works) that is plugged in the line-in jack.

any ideas?

---

### Post by Revolutionary101 on 2010-01-20
Go to System>Preferences>Sound then change the Input to Microphone 2. That is what fixed my microphone problem.

And congrats on your first post on the Ubuntu forums!

---

### Post by amir.kadivar on 2010-01-20
I had checked there, there is no option there as another input.
The only option is "Internal Audio Analog Stereo" which is already checked. no "external mic" or "mic 2" or sth like that ..

---

### Post by amir.kadivar on 2010-01-20
and thanks for the congrats ;)

---

### Post by Revolutionary101 on 2010-01-20
> **amir.kadivar said:**
> and thanks for the congrats ;)

No problem. Do you know the make and model of your sound card?

---

### Post by amir.kadivar on 2010-01-20
yeah the model is IDT 92HD81B1C5.

---

### Post by Revolutionary101 on 2010-01-20
Update ALSA (Advanced Linux Sound Architecture) by following this tutorial [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

I hope it helps.

---

