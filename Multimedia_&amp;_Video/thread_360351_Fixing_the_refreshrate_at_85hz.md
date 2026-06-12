---
title: "Fixing the refreshrate at 85hz"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by RudolfMDLT on 2007-02-13
Hi there,

How can  fix the refresh rate at 85Hz? in the Nvidia settings panel i get the option of 60,75 and 85hz. I set it to 85hz and then press the save to Xorg.conf file button. But it never does! every time I restart  have to manually set the refresh rate again! Under peripherals in KDE the monitor is set to 120Hz? I don't change this cause the only other two options are 50 and 58hz?

Any help would be very much appreciated!

Thanks,

Rudolf

---

### Post by Perfect Storm on 2007-02-13
Any chance that you are runing Beryl?

---

### Post by NoobieDoobieDo on 2007-02-13
Seriously, what's wrong with Ubuntu / Kubuntu ability to change the refresh rate ?

I use the Intel 82865G graphics card and the HP 72 monitor (which Ubuntu calls the HP D8904).

And no matter what I can't change my refresh rate off of 85hz.

	Identifier	"HP D8904"
	Option		"DPMS"
	HorizSync 30-70
 	VertRefresh 50-120

Good luck.

Things like this make Ubuntu feel like Windows.

You do what you're suppose to in order to change the refresh rate but it doesn't change a thing.

Awesome "feature" !

---

### Post by Perfect Storm on 2007-02-13
Well, if he is running beryl this can be a case of problem with beryl and not Ubuntu.



Also - Keep in mind alot of things (drivers etc) have been written by people because the vendors refuses to support linux or give the tech details so the community can make a proper driver.


By the way I read somewhere you need to install a specific libs to handle your problem, NoobieDoobieDo.

---

### Post by NoobieDoobieDo on 2007-02-13
I'll start a new thread ..

Rudolf,

After you save the settings are the changes reflected in your /etc/X11/xorg.conf file ?  If so it may be possible to back that up and then write a simple command which will overwrite the current copy of xorg.conf before xorg loads with the xorg settings you want.

Something like (as root)

cp /home/rudolf/backups/xorg.conf /etc/X11/xorg.conf

Should do the trick.

---

### Post by predator on 2007-02-13
I was about to post the exact same question.. There must be an xorg.conf setting that does it in one. 

Even if I set the refresh to like vertical refresh to 70-160hz, it defaults to 60hz every time :(

It's really annoying as my eyes are really susceptible to the flicker.

---

### Post by RudolfMDLT on 2007-02-14
Hi, Sorry I'm only posting back now! Yeah -  did run Beryl but that has been completely removed! I can read the Xorg file pretty well by now seeing as I was an Ati user for a long time and 1 week into Ubuntu i new the damn thing off by heart. :) 

As far as I know the refresh rate part is this part:

>     Identifier     "Generic Monitor"
    HorizSync       30.0 - 96.0
    VertRefresh     43.0 - 85.0
    Option         "DPMS"

I have a Samsung monitor which I have installed the driver for but I'm not sure whether it is in the actual Xorg file:

> Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24

This part bothers me... I installed the SyncMaster Driver for the  997DF series.

But thanks for all the replies - They are very much appreciated!

---

### Post by Rizado on 2007-03-13
I got the exact same problem. My screen is supposed to run optimal at 1028x1024@75hz but ohh no, thr controlpanel in kubuntu I can choose between 50 and 54, none that my screen support (56 is the lowest it will go). And they both set the screen to 60hz. And now all of a sudden I can choose between 50 and 90! Not supported either.

I can change to the correct settings in nvidia-settings and I then made a few modelines and they do work! But only until I've entered my password and hit enter. Then it changes to 60hz again! This is really starting to piss me off. Running Beryl or not is not the point. It still shouldn't change refreshrate as soon as you try to log in.

---

