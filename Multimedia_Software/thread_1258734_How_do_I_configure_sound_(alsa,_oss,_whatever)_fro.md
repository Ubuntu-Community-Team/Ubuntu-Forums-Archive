---
title: "How do I configure sound (alsa, oss, whatever) from the command line?"
date: 2009-09-05
forum: Multimedia Software
---

### Post by pythonscript on 2009-09-05
I'm using a command line only ubuntu with icewm stacked on top, and I can't get my sound to work. I downloaded the oss deb from their website, and that "works," but when I plug in headphones, external speakers, etc to my headphone jack, sounds still comes out the laptop speakers! This is clearly not desired. 

I ran ```
sudo apt-get install alsa-base alsa-utils
``` but when I run
```
sudo alsactl init
``` I get an error message: "alsactl: init:1708: No soundcards found..." and no sound works at all! The only tutorials I can find aren't really helpful, and they all refer to working with this gui, or that gui in gnome/kde, etc, and that doesn't really do me any good. My laptop's specs are below. My HP has an interface on the front with a mic jack, headphone jack, and SPDIF headphone jack, if that helps anyone. I love this lightweight configuration I have, but I'd really like to get stuff working...

---

### Post by RedRat on 2009-09-05
Have you tried to run alsamixer in the command line?

---

### Post by pythonscript on 2009-09-05
alsamixer crashes with a set of error messages. When I'm back at my laptop, I'll pull those up again.

---

