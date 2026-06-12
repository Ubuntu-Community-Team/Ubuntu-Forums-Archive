---
title: "Nvidia GeForce 7500LE"
date: 2006-09-29
forum: Multimedia &amp; Video
---

### Post by SpikeyMike on 2006-09-29
Hi

I ran the setup guide at the following link:

[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

to install the drivers for my *Nvidia GeForce 7500LE* card but when I look at the xorg.conf file using the '*sudo gedit /etc/X11/xorg.conf*' command the card is still recognised as a default card, below is the output from the xorg.conf file:

[I]Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection[/I]

should it not be recognised as a 7500LE card instead of default?

Any advice appreciated

Mikey

---

### Post by morphodone on 2006-09-29
I have a 7600GS and here's my xorg snippet


```
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

```

and my card works just dandy.  I wouldn't be too worried about it.

---

### Post by tseliot on 2006-09-30
[QUOTE=SpikeyMike;1561056]Hi

I ran the setup guide at the following link:

[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

to install the drivers for my *Nvidia GeForce 7500LE* card but when I look at the xorg.conf file using the '*sudo gedit /etc/X11/xorg.conf*' command the card is still recognised as a default card, below is the output from the xorg.conf file:

[I]Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection[/I]

should it not be recognised as a 7500LE card instead of default?/QUOTE]
Not necessarily. It's just a tag. The card will work just fine

---

