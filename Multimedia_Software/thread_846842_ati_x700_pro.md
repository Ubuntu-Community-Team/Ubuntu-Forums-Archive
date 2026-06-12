---
title: "ati x700 pro"
date: 2008-07-01
forum: Multimedia Software
---

### Post by haZZe08 on 2008-07-01
anyone have the same card and got it to work? I've tried enabeling the restricted driver and then restarting but when I restart all i get is a black screen and as a result I have to re-install ubuntu. 

i'm on gutsy and upgrading to hardy.

---

### Post by Melcar on 2008-07-01
Try installing the latest 8.6 drivers.

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

---

### Post by haZZe08 on 2008-07-02
> **Melcar said:**
> Try installing the latest 8.6 drivers.

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")



when I input sudo gedit /etc/X11/xorg.conf , it gives me this:


No protocol specified
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

---

### Post by markbuntu on 2008-07-02
You need to put a space between gedit and /etc/X11/xorg.conf.

---

### Post by haZZe08 on 2008-07-02
> **markbuntu said:**
> You need to put a space between gedit and /etc/X11/xorg.conf.



Tried it. Gives me the same ****.

---

### Post by Melcar on 2008-07-02
Try with nano instead of gedit.

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by haZZe08 on 2008-07-07
> **Melcar said:**
> Try with nano instead of gedit.

```
sudo nano /etc/X11/xorg.conf
```



k, kool that opened up my xorg.cong

then I added this line

Driver "fglrx" 

like this?



Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"                       
        Identifier      "Configured Video Device"
        driver          "fglrx"

---

### Post by haZZe08 on 2008-07-07
i get this now

No protocol specified
Data incomplete in file /etc/X11/xorg.conf
	Device section "Configured Video Device" must have a Driver line.
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Data incomplete in file /etc/X11/xorg.conf
	Device section "Configured Video Device" must have a Driver line.
Segmentation fault


i noticed that it did not save it. How do I save it?

---

### Post by peakshysteria on 2008-07-07
If you upgrade or install Hardy you get rid of the black screen problem (i guess this is the screen out of range problem?). You can also use **_Envy_** which is found via synaptic. A program which has proven to be a big help to several other ATI users.

Or check out: Catalyst Install Guide: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by haZZe08 on 2008-07-08
> **peakshysteria said:**
> If you upgrade or install Hardy you get rid of the black screen problem (i guess this is the screen out of range problem?). You can also use **_Envy_** which is found via synaptic. A program which has proven to be a big help to several other ATI users.

Or check out: Catalyst Install Guide: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)


yea i get a black screen if i enable restricted driver and cant log in.
and i was using that wiki but am running into issues

---

### Post by haZZe08 on 2008-07-08
i downloaded envy and used it and gave me the same **** with the black screen. I just installed again.

---

### Post by peakshysteria on 2008-07-08
Hardy has fixed the blackscreen issue. The problem in Gutsy seems to be that after installing the driver it detects the screen resolution to high. Which makes the screen out of range. This is solved in Hardy. I would advice you to upgrade to Hardy before continuing. Not that installing the driver is simpler. But at least you can see what you do :)

There are several people with X700 which have made it. The forum is full of them. I'm not one of them unfortunately :( For the time being I've given up since everything besides the ATI driver is running very smooth.

I really think [Method 2: Manual Method (installing Catalyst 8.6)]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29") is our best bet.

---

