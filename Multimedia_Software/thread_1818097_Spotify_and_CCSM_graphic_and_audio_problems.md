---
title: "Spotify and CCSM graphic and audio problems"
date: 2011-08-04
forum: Multimedia Software
---

### Post by oli.kerr on 2011-08-04
Hello all,

I'm a relatively new Ubuntu user (only having about 2/3months previous experience) and I'm using version 11.04 and my problem is... Spotify. Its doing my head in.

I am running it through wine (as I am too stingy to pay for premium to use the linux version of spotify) and I configured wine as guided in the following link: 

[http://www.spotify.com/uk/help/faq/wine/](http://www.spotify.com/uk/help/faq/wine/)

Spotify installs and loads alright through wine, however, once I arrive on the Spotify GUI I am greeted by nothing but laggy graphics (taking about 10seconds for the program to respond to a click of the mouse) and an error which simply says there is an error playing the audio. This is annoying seeing as my banshee media player works perfectly and internet audio media works fine.

My desktop has an Nvidia Geforce 8800GT graphics card, and I am beginning to think that I do not have the correct graphics drivers installed as when I am also trying to use desktop effects (ccsm - compiz config settings manager) my desktop keeps crashing and I cannot utilize any of the cool effects. Bummer. In addition to my graphical problems in CCSM and Spotify (which is perhaps caused by my graphics card not being set correctly) viewing videos on youtube or anything using a flash plugin is very temperamental - maybe only working half the time.

Anyone having similar problems? Or have remedied them recently? let me know!

Cheers,
Oli

---

### Post by .... on 2011-08-04
I'm not sure about your video issues, but the guide you link to fails to mentions that recent Ubuntu kernels are built without OSS audio support. The easy workaround is to use padsp for OSS emulation. This is reported to work well for Spotify in wine:
```
padsp wine <program>
```

---

### Post by oli.kerr on 2011-08-11
Helpful stuff but I'm going to have to give this thread a BUMP

---

