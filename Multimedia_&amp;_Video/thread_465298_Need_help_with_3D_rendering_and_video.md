---
title: "Need help with 3D rendering and video"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by picaro on 2007-06-05
Hello:

I was using XP home edition on my desktop that I purchased last fall and it worked really smoothly. However it ws in Dutch, and could not get it in English unless I purchase another edition in English. I am trying Ubuntu 7.04 and like it except for some problems that I am having with multimedia. Here are the specs on the computer :

Acer  Aspire 136 T97Z
AMD Sempron 3100+  1.8 GHz
512 DDR RAM
200 GB hard drive
Integrated video card VIA/S3 Unichrome Pro VGA Adapter ( K8N800 )

I have downloaded all the codecs and looked endlesslty for a download that would help. Videos on some websites cannot be run or sun really slowly and you cannot forward them as I would be able to with XP. Google Earth takes a million years to load and does not show anything where the Globe is supposed to  be, just black. Computer also freezes when attempting to run 3-D screen saver. 

I am sure that there has to be some way of having my computer perform as it did under XP.  Any help would greatly appreciated,


Chris

---

### Post by ringmaster on 2007-10-16
Hello;
There's a problem with 3D using VIA Unichrome PRO IGP: the entire system freezes ramdomly. Actually there is no maintainer of the Mesa driver for this type of cards :(. If you don't need 3D then install Openchrome driver (it is the state-of-the art) and disable 3D:

**First open the xserver configuration file:**
```
sudo nano /etc/X11/xorg.conf
```

**In Feisty and previous releases put a "#" before this lines:**

```
Section "Module"
       # Load "dri"
        #Load "glx"
EndSection
```

**In Gutsy (7.10) and future releases change this lines:**

```
Section "Module"
        Disable "dri"
        Disable "glx"
EndSection
```

and if there is no Modules section add it.

I am going to try to encourage the developers to fix this (it is a problem of VIA not releasing specifications) by donating money in another threat in ubuntuforums...

---

### Post by ringmaster on 2007-10-25
Another thing, Picaro. It looks like that you are using the generic VESA driver (so the videos run slowly). The better driver for this type of cards is Openchrome (perfect 2D acceleration with XVMC (mpeg2) acceleration support; 3D hangs frecuently.

The last thing to try is to use the Via drivers ([www.viaarena.com](www.viaarena.com)) that have improved a lot from previous versions.

There are manuals and tutorials on the web, I hope you can solve your issues.

---

