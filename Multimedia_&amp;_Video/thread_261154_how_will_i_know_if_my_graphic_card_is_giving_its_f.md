---
title: "how will i know if my graphic card is giving its full feature"
date: 2006-09-19
forum: Multimedia &amp; Video
---

### Post by kellykamay on 2006-09-19
i have NVIDIA GeForce FX 5200 128mb..and a 1 gig physical ram..
i run gimp and its so slow..i think my video card is not giving  its full feature..so how will i know if its running its best or not?..thanks in advance

---

### Post by MetalMusicAddict on 2006-09-19
Do you have the nVidia drivers installed?

---

### Post by enopepsoo on 2006-09-19
Do you mean it draws the images slowly?  I know that before I had my nvidia drivers installed that this happened.  I used the Envy script.  It is super.:KS 

The GIMP does take a while to load though.:-({|=

---

### Post by kellykamay on 2006-09-19
i think the ubuntu live cd installer has automatically installed the driver

i've checked my /etc/X11/xorg.conf and here's what i got

Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "COMPAL V799"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "COMPAL V799"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"

---

### Post by kellykamay on 2006-09-19
> **enopepsoo said:**
> Do you mean it draws the images slowly?  I know that before I had my nvidia drivers installed that this happened.  I used the Envy script.  It is super.:KS 

The GIMP does take a while to load though.:-({|=

Do you mean it draws the images slowly?<--- exactly!!!...so what about this Envy script?..

---

### Post by enopepsoo on 2006-09-19
the driver should say nvidia, not nv.

you can find the envy script and installation details here: [http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

He actually posts here with the name TsElliot and is very helpful. :cool:

---

### Post by kellykamay on 2006-09-19
alright i'll try to change it to nvidia..i'll be back!!

---

### Post by enopepsoo on 2006-09-19
don't just change it to nvidia! [-X  

:D you have to run the script, it will setup xorg.conf for you.

---

### Post by kellykamay on 2006-09-19
BWAHAHAH...i guess u were right...after i change my X server has an error..

failed to load module /etc/X11/xorg.conf

so i've change it back to nv..now im goin to envy script..again i'll be back..

thanks enopepsoo

---

### Post by kellykamay on 2006-09-20
still there's an error..i run the envy script i thought it was doin ok but in the end an error occur..the envy cant find the nvidia driver in my system but when it tries to download it from the net the connection refuses and the md5 aborted the operation..

so what do u think what happen?

---

### Post by tseliot on 2006-09-20
> **kellykamay said:**
> still there's an error..i run the envy script i thought it was doin ok but in the end an error occur..the envy cant find the nvidia driver in my system but when it tries to download it from the net the connection refuses and the md5 aborted the operation..

so what do u think what happen?

It looks like it's time to implement the support for a http mirror (since ftps can be a problem if you are behind a firewall).

I'll update Envy soon.

Stay tuned.

In the meantime you can install the driver by following Method 1 of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by tseliot on 2006-09-20
Try updating to the latest version of Envy which I have just released

---

### Post by kellykamay on 2006-09-20
BWaahahha...its working now and for that mr tseliot i'll give u :KS :KS :KS :KS :KS ...thanks alot guys...

---

