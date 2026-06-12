---
title: "Horizontal Lines - any moving graphic"
date: 2009-02-08
forum: Multimedia Software
---

### Post by rockinstlouis on 2009-02-08
currently I'm using 8.10 64-bit.. I have a NVidia 8600 gt..  the issue is that I see horizontal lines whenever a fast moving graphic goes past the screen.. screensavers, DVDs, etc

I've done everything I can think of.. switching the DVI cable, tried another video card, switching the driver.. playing with the driver settings.. tried using Ubuntu 8.04.. even a different distro (Fedora).. and they all do the same thing..

My Vista drive does not have this problem..

what in the heck am I missing here?

---

### Post by rockinstlouis on 2009-02-09
may I add that someone here said it was "interlacing artifacts" I believe them, however I don't see how it's possible to adjust / disable it for X, or the driver level..

is there anything I should look at for X?

---

### Post by nibus on 2009-02-10
> **rockinstlouis said:**
> may I add that someone here said it was "interlacing artifacts" I believe them, however I don't see how it's possible to adjust / disable it for X, or the driver level..

is there anything I should look at for X?

I think that I have the same problem... check the image...
[[IMG]http://widget.slide.com/rdr/1/1/3/W/31000000029d1316/1/38/MCT5tqykqT_0dwL1kJLdMp377X9WeRjz.jpg[/IMG]](http://www.slide.com/s/TnoZ029V3j_eOroxJY0y5XO4P1t3MNRo?referrer=hlnk)
its happens every time i'm seing a movie... i&#7743; looking for help too..

---

### Post by rockinstlouis on 2009-02-10
yes.. that's exactly it.

In my case, I think it's a driver problem.  I can re-create the issue on my Vista drive by gearing the card for better performance, than quality, in the driver.  You give it more quality and it goes away, for all applications.  

However this slider for Ubuntu, doesn't do anything.

Do you have a 3D accelerated card?  It would be interesting if the problem can be recreated with a different 3D card, like an ATI, with it's appropriate driver.

---

### Post by nibus on 2009-02-10
> **rockinstlouis said:**
> yes.. that's exactly it.

In my case, I think it's a driver problem.  I can re-create the issue on my Vista drive by gearing the card for better performance, than quality, in the driver.  You give it more quality and it goes away, for all applications.  

However this slider for Ubuntu, doesn't do anything.

Do you have a 3D accelerated card?  It would be interesting if the problem can be recreated with a different 3D card, like an ATI, with it's appropriate driver.

I have a great grafic card. its a nvidia 9600M GT. yes, on vista i run crysis without any problems. it was perfect.but in ubuntu have this problem... i've tried to adjust some configurations in the nvidia driver grfics but it doesn't do nothing... yes, i heard tha ati video cards are better support in ubuntu that nvidea... sorry for may bad english. i'm portuguese...

---

### Post by nibus on 2009-02-10
Try to change the driver to the older one and give me the feedback please...

---

### Post by nibus on 2009-02-11
i instaled the brand new drive nvidia 180 but it didt change nothing... if yu get something, tell me please.

---

### Post by rockinstlouis on 2009-02-11
Well I bought a NVIDIA 9800 GT last night and I have the same problem.  It's definitely a driver problem with NVidia.  This card also behaves on my Vista drive.

I heard the same thing that NVidia has troubles.  Maybe I'll see if an ATI will do a better job.

---

### Post by rockinstlouis on 2009-02-11
Both the 177 and 180 NVidia drivers have the same issue.

---

### Post by nibus on 2009-02-11
well i cant change my grafic card. its a laptop... but good luck with ati... ;)

---

### Post by nibus on 2009-02-14
hey. i found the origin of the problem... its on compiz fusion. but i dont know where...

---

### Post by mfarewell on 2009-03-02
I experience the same problems. The lines are most visible when playing fast screen savers (e.g. polyhedra), but any fast sequence in flash or on a DVD causes them to appear. They were very pronounced in Flash but updating to the latest 10,0,22,87 really improved the quality, the lines still appear but now to the same extent as the other media sources. Turning off compiz has no effect for me, so I doubt that compiz is the cause. 

I upgraded the Nvidia driver from nvidia-glx-177 to nvidia-glx-180 it made absolutely no difference to the problem. I changed the quality slider in nvidia-settings likewise no effect.

My system:
Intrepid 32 bit
Nvidia 8600GT
Intel Quad Core 3.2GB RAM

---

### Post by nibus on 2009-03-08
turning of all the efects of ubuntu solve the problem... the lines realy desapear... but me and you want the efects, so its not realy a solution... but when i want to see a movie i do that...
until now i dont get any improvement...but i hope that in ubuntu 9.04 this is solved... our machines are good so isnt a hardware prolem:
dual core 2.4ghz
9600m gt
3gb RAM DDR2

---

### Post by Macintosh SE on 2009-03-08
What did you set the refresh rate at? My TV, which displays at 60 Hz, shows some minor "tearing" like this.

---

### Post by nibus on 2009-03-15
> **Macintosh SE said:**
> What did you set the refresh rate at? My TV, which displays at 60 Hz, shows some minor "tearing" like this.

my display is 50hz
but there is a configuration on compiz fusion manager that the refresh rate are 50 ...but i can change it. but nothing happens

---

