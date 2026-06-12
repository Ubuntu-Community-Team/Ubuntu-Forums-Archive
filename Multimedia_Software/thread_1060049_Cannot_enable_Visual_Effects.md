---
title: "Cannot enable Visual Effects"
date: 2009-02-04
forum: Multimedia Software
---

### Post by peterthegeek on 2009-02-04
Hi there, I'm new to the Ubuntu forums, and pretty new to Ubuntu. The other day I was trying to get AWN working, but I needed to enable the visual effects (Compiz). When I tried to enable it, it say "Cannot enable desktop effects." (or something like that). I have checked restricted drivers in case it was my graphics card, but there aren't any available. I have also tried installing xserver-xgl, but that didn't work. Any help would be greatly appreciated :D

---

### Post by Therion on 2009-02-04
Do you know what graphics card or integrated graphics chip you have on your PC?

Take a look at Compiz-Check:  [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

Let us know what it tells you.

---

### Post by peterthegeek on 2009-02-04
I have an Intel X3100 integrated graphics card.

I ran compiz-check, and this is what it outputted:

> Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card.

When I told it to check if there is an alternate driver available, it found none.

---

### Post by redroad55 on 2009-02-04
In looking at your post as well as looking in inte's imfo this is what I come up with 
[http://support.intel.com/support/graphics/sb/CS-010512.htm]("http://support.intel.com/support/graphics/sb/CS-010512.htm")
also this link
[http://intellinuxgraphics.org/]("http://intellinuxgraphics.org/")
best I can tell the driver is in the works .. you will have to do more research .. there are many looking for it's developement Post back ..Best to you..

---

### Post by Therion on 2009-02-04
Compiz-Check is reporting you have an Intel 965 integrated chipset; that's the mobile version of the X3100 series.  It's not impossible to get Compiz running on that chipset, but it's not going to be easy either.  

Do a forum Search on your chipset, I'm sure you'll find some help with getting Compiz running.
 
Best of luck to you.

---

### Post by peterthegeek on 2009-02-04
I realized that whenever I start up the computer, it says something like "Could not find graphics something something blah blah." Then it gave me a few options. I usually click "Boot in Low-Graphics mode" or something, but this time I chose to use a default something to reconfigure the graphics. Now it works. :D:D:D

---

### Post by redroad55 on 2009-02-04
That"s great .. The Gnomes fixed it..You got to have them on your side or you'll be posting here alot..Best to you

---

