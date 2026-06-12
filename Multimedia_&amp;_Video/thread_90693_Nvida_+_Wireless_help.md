---
title: "Nvida + Wireless help"
date: 2005-11-15
forum: Multimedia &amp; Video
---

### Post by Night on 2005-11-15
So I just installed Ubuntu onto my computer and have been having some difficulties. So first I have no internet currently I need to install the NDIS Wrapper (sp?) so I can load my windows drivers for my wireless card. 

My next problems is that Xserver dosent have the driver to use my Geforce Mx 4000 card Due to this problem it wont launch I need all help doable throught the command prompt.

Ok so my questions are:
1. How do I get a working Nvidia driver without internet?
2. If its much harder without internet how do I install a .deb and set up NDIS (sp?) Wrapper throught command prompt?


If its absolutly nessacary I might have enougth cable to run the lan downstares to my comp.

Thanks for the help and sorry bout any spelling mistakes.

---

### Post by tseliot on 2005-11-15
[QUOTE=Night]So I just installed Ubuntu onto my computer and have been having some difficulties. So first I have no internet currently I need to install the NDIS Wrapper (sp?) so I can load my windows drivers for my wireless card. 

My next problems is that Xserver dosent have the driver to use my Geforce Mx 4000 card Due to this problem it wont launch I need all help doable throught the command prompt.

Ok so my questions are:
1. How do I get a working Nvidia driver without internet?
2. If its much harder without internet how do I install a .deb and set up NDIS (sp?) Wrapper throught command prompt?


If its absolutly nessacary I might have enougth cable to run the lan downstares to my comp.

Thanks for the help and sorry bout any spelling mistakes.[/QUOTE]

1) Try this:

```
sudo nano /etc/X11/xorg.conf
```

Then find the section Device and make sure the word I put in red is &#8220;vesa&#8221;:

```
Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR="Red"]vesa[/COLOR]"
BusID "PCI:1:0:0"
```


```
CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit
```

Then type:

```
sudo startx
```

---

### Post by Night on 2005-11-15
thanks ill try that when I get home.

---

