---
title: "Graphics Issue"
date: 2008-12-28
forum: Multimedia Software
---

### Post by raskell on 2008-12-28
Hey all

Just switched from windows to linux and ran into a graphics snag I just cant figure out.

Running Acer Travelmate 2313LCI, 1.5ghz, 3/4gb RAM, 100gb HDD, SiSM661MX
Ubuntu 8.10

Im trying to run 3d games and some apps, the rendering and movement is very very choppy even when I drop quality and framerates. Also seems like something is really hogging the memory but I was looking up things and found that this laptop in general has alot of issues running ubuntu. 

Only thing is these people say whats wrong, dont at all point in directions for fixes. the only thing I got left to fix is graphics anyone here know whats going on? Even if there is a link to an up to date proprietary driver available somewhere, I havent been able to find a stable one yet.

Thanks in Advance!

---

### Post by gettinoriginal on 2008-12-28
Run these two in terminal, one at a time:

```
 sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list 
```

```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update 
```

Then:
System > Admin > Hardware Drivers, let it search for driver then activate it
System > Pref > Appearance > Visual Effects, should be set to Extra or Custom

---

### Post by raskell on 2008-12-29
Ran those lines in the terminal and everything looked ok, but the driver isnt showing up in hardware drivers. I tried enabling extra anyway and it wouldnt work, guessing because the driver didnt show up.

I know something came in on those terminal commands is there a way to perform a driver check again it seems as though hardware drivers isnt searching at all, the only thing showing up is the Atheros support.

Thanks

---

### Post by gettinoriginal on 2008-12-29
In terminal type:    ```
lspci
```  that will tell you what your vid card is so you can look for the driver.

---

### Post by raskell on 2008-12-29
Hit that got output 

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

Unfortunaly after doing a search this driver seems to be hard to find or non exisitant, Which is what I figured the first time I tried searching for it. 

has anyone run into this problem and fixed it? if so how? or maybe if anyone has a driver they could send it over to me?

thanks

---

### Post by gettinoriginal on 2008-12-29
Check this one in Synaptic, its and SIS display driver.

xserver-xorg-video-sis

---

### Post by raskell on 2008-12-29
Its showing already installed, I marked for reinstallation, searched and still not showing in hardware drivers, Im starting to wonder if this issue can be fixed, Im finding alot of other people with the same problem but im finding no solutions beyond what we have already tried..

However, Im very stubborn.. :)

---

### Post by gettinoriginal on 2008-12-29
Well, no more solutions here yet, but like you, I am stubborn, so will keep looking ](*,)

---

