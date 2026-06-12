---
title: "Composite Input"
date: 2009-04-14
forum: Multimedia Software
---

### Post by zarqoon on 2009-04-14
I tried getting the Composite Input of my Geforce 7800GT to work but i have no clue how to. I Installed Mythtv and got that to work but it did not seem to be able to find anything an the Composite In of that card.
I hooked my PS2 up to that Input and the only thing i want is to be able to see its Picture on my Screen because i do not have a TV to hook it up to.
I did a lot of Googling but most articles dealing with Composite refer to TV Capture Cards at not to the simple little yellow Composite Video Input my Graphics Board has that I try to use.

After some further googling i noticed that Composite Input Connectors in Graphics Cards seem to be quite rare. But my Card got one. It has a SVideo Input Connector too as well as output for both.
The Manual tells me to Install the nvidia wdm drivers to be able to use the inputs. But i could not find anything similar for Linux.

I am now fairly certain that the if there is no driver for Linux yet there never will be one. Apparently Nvidia discontinued VIVO support for their Cards after the 7 series. Seems like i will have to fire up windows to get this to work.

---

### Post by zarqoon on 2009-04-15
I tried using windows installed the drivers and voila i can play Playstation in a VLC player window. I would really like doing that using linux though.

---

### Post by xc3RnbFO8P on 2009-04-15
I dont know this, but I would try:
> sudo nvidia-xconfig --composite
restart
then install **Tvtime** in Add/Remove (all available application)
In Tvtime right click,  choose >input configuration>change video source> composite

---

### Post by zarqoon on 2009-04-15
That did not change anything. And as far as i understand the composite option in the xorg.conf does not have anything to do with a composite video port.
TvTime says that it can not open /dev/video0 and thats probably because it does not exist on my system.
I have come to thinking that the video in option is not included in the regular driver. Its not included in the windows driver either i had to install the nvidia wdm driver on top of the usual forceware. The windows driver makes a direct show stream available that the vlc player can read.

I read something about a old driver named rivatv that seems to be doing exactly what i need but for older nvidia cards. But that wont compile on my system for some reason ./configure seems to think i dont have a kernel newer than 2.4

---

