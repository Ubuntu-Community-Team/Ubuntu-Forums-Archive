---
title: "[SOLVED] No sound"
date: 2008-08-21
forum: Multimedia Software
---

### Post by Hyper Tails on 2008-08-21
hi i have vista and hardy installed and in vista theres sound in it but in vista theres no sound at all
i had sound before but for some reason it stopped working :(

help will be thanked

laptop-Acer apsire 5715-4740

---

### Post by vjkeito on 2008-08-21
I presume you mean there is sound in vista and no sound in **ubuntu**

please post the ouput of the following (run it in the terminal)

```
lspci | grep Multimedia

```

and then

```
sudo lshw -class multimedia

```

---

### Post by Hyper Tails on 2008-08-21
this is what i got from it

---

### Post by Hyper Tails on 2008-08-21
Question: do i need to hook up to the internet in order for this to work?

---

### Post by Hyper Tails on 2008-08-21
i fix it now 
thanks for the help

---

### Post by talibanned on 2008-08-21
how did you fix this?? i have the same problem.........

---

### Post by Hyper Tails on 2008-08-21
just go into system settings>sound system>hardware>and have the select the audio device at open sound system

thats what i did

try to see if that works with you

---

### Post by vjkeito on 2008-08-22
yes from your screenshot it shows that you are using the intel card "82801H"

which a quick google serach will tell you is "Intel 82801H HDA"
one of the last people I helped get sound had the same card...

OSS is much more mature than the alsa drivers for now, though due to the fact they are now closed source I believe they are removing them from future releases (you can still install it yourself though)

we really need a massive increase in stability and functionality with the oss alsa/pulse audio combo very soon.

anyway glad you got your system sorted

peace

---

