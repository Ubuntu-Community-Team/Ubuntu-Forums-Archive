---
title: "High quality sound recorder?"
date: 2011-05-03
forum: Multimedia Software
---

### Post by Antarctica32 on 2011-05-03
What is the highest sound quality sound recorder for ubuntu? Sound recorder does not recorder as high quality as the original at all and I really need that.

---

### Post by Antarctica32 on 2011-05-05
*bump* anyone?

---

### Post by ron999 on 2011-05-05
Hi
When you use the Ubuntu sound recorder,
where it says:- **Record as**
What options does it give you?

---

### Post by Antarctica32 on 2011-05-05
Just the more popular 0nes, why? I tried them all they all give the same rather poop quality.
m4a
flac
ogg
mp2
mp3
wav
spx

---

### Post by ron999 on 2011-05-05
> **Antarctica32 said:**
> Just the more popular 0nes, why? I tried them all they all give the same rather poop quality.
m4a
flac
ogg
mp2
mp3
wav
spx

Choose flac or wav.
They are the lossless formats - high quality.

---

### Post by tgalati4 on 2011-05-06
You can customize sound output file properties including defining your own high definition sound files.  You will have to search the forums for the correct "magic" notation to accomplish this. Search gnome sound profiles.

With audacity, you can record at any rate supported by your soundcard.  My M-Audio Delta66 can record at 24-bits, 96 kHz WAV files which is better than CD (16-bit, 44.1 kHz).

---

### Post by NightwishFan on 2011-05-06
Unless you have very specific needs just about any recorder that records to flac or wav will do fine. I recommend audacity, jokosher, or ardour.

---

### Post by tgalati4 on 2011-05-06
Of course poop is a relative term.  If your sound recording equipment is poop, well then everything will sound like poop.  And I'm surprised that poop isn't *** out like other four-letter words such as **** and ****.

---

### Post by Jordanbadangayon on 2011-05-06
or you can adjust the sensitivity of your recorder... go to sound preference.. :)

---

### Post by Antarctica32 on 2011-05-06
this is g0ing to sound either strange or stupid, I'm not really into this whole media player thing yet. So I looked into recording with audacity and whatever I record when I play it back it always just gives me silence and about 4 seconds in a rather loud 1 second long beep. Could this have anything to do with the "project rate" being at 44100hz?

---

### Post by tgalati4 on 2011-05-06
What is the output of:

aplay -l

Sounds like audacity is not set up correctly.  You can change the project rate, but it must be supported by your sound card.  44.1kHz is CD sampling frequency and is supported by most (if not all) cards.  So something else is going on.

Try running audacity in a terminal:

audacity

And see if it spits out any error messages.

---

### Post by shantiq on 2011-05-07
> **Antarctica32 said:**
> What is the highest sound quality sound recorder for ubuntu? Sound recorder does not recorder as high quality as the original at all and I really need that.



to record your[ voice]("http://ubuntuforums.org/showpost.php?p=10545528&postcount=1")

to record desktop sound with [audacity]("http://ubuntuforums.org/showpost.php?p=10552830&postcount=1")

---

