---
title: "Avi Video Display Problems"
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by IndoorRiot on 2008-02-15
I have just downloaded Kino and have tried to play an .avi file that was imported from my camera. The sound is fine, but the display is essentially just a bunch of moving vertical lines.  I tried opening it with Movie Player as well and the same happened. I have now tried it with various .avi files, to no avail. Does anyone have any suggestions? I am very new to Ubuntu and am not sure what to do! Thanks!:confused:

---

### Post by xc3RnbFO8P on 2008-02-15
Install codec from here:
> 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
> 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

In terminal (Application> Accessories> Terminal): 
> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Then in Synaptic Package Manager (System> Administration> Synaptic Package Manager), install **Mplayer** and **VLC**.
You can use the search function in Synaptic Package Manager to find these programs.

---

