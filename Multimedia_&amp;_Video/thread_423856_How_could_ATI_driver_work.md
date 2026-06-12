---
title: "How could ATI driver work"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by Beliar on 2007-04-26
Hello,
I have installed the ATI driver with the restricted drivers manager. Of course it didnt work, X wouldnt start. so I'm using the free ati/radeon driver.

How ever, I downloaded the latest driver from ati.amd.com and the setup and also the website say, that it is not compatible with kernel 2.6.20 and only with xorg <= 7.1.
Feisty has kernel 2.6.20-15 and xorg 7.2. No wonder it doesnt work and it wont until ATI releases a new one.
But what driver is that on the repository? Is it patched anyhow?? (how, the driver is just a blob?)

So, am I right, you just cant make it run yet, or has anybody a working fglrx driver??

Btw, I have a mobile radeon x700 if  thats anyhow relevant.

greets,
Beliar

---

### Post by Ferrat on 2007-04-26
> **Beliar said:**
> Hello,
I have installed the ATI driver with the restricted drivers manager. Of course it didnt work, X wouldnt start. so I'm using the free ati/radeon driver.

How ever, I downloaded the latest driver from ati.amd.com and the setup and also the website say, that it is not compatible with kernel 2.6.20 and only with xorg <= 7.1.
Feisty has kernel 2.6.20-15 and xorg 7.2. No wonder it doesnt work and it wont until ATI releases a new one.
But what driver is that on the repository? Is it patched anyhow?? (how, the driver is just a blob?)

So, am I right, you just cant make it run yet, or has anybody a working fglrx driver??

Btw, I have a mobile radeon x700 if  thats anyhow relevant.

greets,
Beliar

The new ATi driver is 7.2 compatible, they just haven't updated that information everywhere 
Im running the latest driver on Feisty 

```

navcom@space:~$ fglrxinfo
     display: :0.0  screen: 0
     OpenGL vendor string: ATI Technologies Inc.
     OpenGL renderer string: RADEON X800 XT Platinum Edition
     OpenGL version string: 2.0.6458 (8.36.5)

     display: :0.0  screen: 1
     OpenGL vendor string: ATI Technologies Inc.
     OpenGL renderer string: 
     OpenGL version string: 2.0.6458 (8.36.5)

```

there is no problem just generate the Ubuntu/Feisty .debs as you did with all others :)

---

### Post by Beliar on 2007-04-26
äh lol, i never created debs,  I just installed it with the script :/

---

