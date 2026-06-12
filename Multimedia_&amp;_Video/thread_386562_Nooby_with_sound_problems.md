---
title: "Nooby with sound problems"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by kiterguy on 2007-03-17
Hey all, I am a having some problems with sound on my laptop. I have an NEC with Edgy, hda-intel sound card and Realtek ALC260 chipset.  I have installed Alsa driver & lib 1.0.14rc3 and utils 1.0.14rc2 but I can stil ont get my sound to work on my latop.  I have been through all of the forums and tried what I could work out how to do, but all to no avail.  I am pretty frustrated with my lack of knowledge of Linux (I am trying to learn as fast as I can on my own) and the 2 weeks trying to get my sound working.  anyone out there willing to give me a hand?

---

### Post by iamthemonkeyman on 2007-03-17
Hello,

have you checked everything isn't muted?
I ran across this problem when installing a few times when upgrading...
try running 

```

sudo /etc/init.d/alsa-utils reset 

```

to re-initialise all the levels....

if this doesn't work, do you see anything at all when you run
```

sudo alsamixer

```
?

did you specify anything when configuring alsa driver?
 such as :

```

sudo ./configure --with-cards=hda-intel   

```

if none of this works do an 

```

aplay --list-devices 

```
and a 

```

lspci -v

```

and post the output here...

hope this helps..

---

