---
title: "TV tuner Studio TV Terminator (saa7131 chip)"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by Vladimir_BG on 2006-06-02
I have managed to make this infamus card work under Dapper, but I still have an issue.
The problem to make it work is that the card does not contain EEPROM, there fore Ubuntu loads saa7134 module, but with bad parametars. I fixed that by unloading the module:

> sudo rmmod saa7134_alsa

then
> sudo rmmod saa7134

and after unloading bad module I loaded one with proper parametars:
> sudo modprobe saa7134 saa7134 card=65 tuner=54

after that xawtv, TvTime and FM radio work ok.

The issue I have is that I need to do the above mentioned procedure each time I boot up.](*,) 

Is there any way to make the proper module load by default?

Also, how do I make the remote that came with the card work?(at least volume and channel +/-)

---

### Post by ersplus on 2006-06-03
Try this :

sudo gedit /etc/modprobe.d/saa7134

With the lines :

options saa7134 audio_ddep=10
options tuner secam=l

Change the right of this file :
sudo chmod 644 /etc/modprobe.d/saa7134

---

### Post by Vladimir_BG on 2006-06-03
> options saa7134 audio_ddep=10
options tuner secam=l

I need it to run at PAL_BG

---

### Post by manu0510 on 2006-11-03
manu@manu-desktop:/$ sudo rmmod saa7134_alsa
ERROR: Module saa7134_alsa is in use

How can i unload the module?

---

### Post by JeffreyRatcliffe on 2006-11-15
> **manu0510 said:**
> manu@manu-desktop:/$ sudo rmmod saa7134_alsa
ERROR: Module saa7134_alsa is in use

How can i unload the module?

I have exactly the same problem - I can rmmod saa7134, because of saa7134_alsa, and I can't rmmod saa7134_alsa because it is in use.

Have you got any further?

---

### Post by ljubomir on 2007-01-08
> **JeffreyRatcliffe said:**
> I have exactly the same problem - I can rmmod saa7134, because of saa7134_alsa, and I can't rmmod saa7134_alsa because it is in use.

Have you got any further?

I had to quit kmix, and it worked. 
To be sure, you can go to init 1 and rmmod it from there.

---

### Post by JeffreyRatcliffe on 2007-01-08
> **ljubomir said:**
> I had to quit kmix, and it worked. 
To be sure, you can go to init 1 and rmmod it from there.

I'm sorry, I don't follow - what do you mean, go to init 1 and rmmod it from there?

---

