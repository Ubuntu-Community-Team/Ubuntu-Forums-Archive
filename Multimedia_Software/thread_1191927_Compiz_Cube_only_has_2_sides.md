---
title: "Compiz Cube only has 2 sides"
date: 2009-06-19
forum: Multimedia Software
---

### Post by brew1brew on 2009-06-19
It's not a CUBE, it's a piece of paper!!

So how do I reconfigure Compiz for a 4 sided cube?

I'm running Kubuntu 9.04 on 

HP 6930p laptop
running ATI Catalyst 9.6 from AMD's site. and yes I did *aticonfig --initial*

Thanks

---

### Post by markbuntu on 2009-06-19
You need 4 desktops to make a cube. In Kubunut you can set that in System Settings somehwere I think.

---

### Post by brew1brew on 2009-06-19
> **markbuntu said:**
> You need 4 desktops to make a cube. In Kubunut you can set that in System Settings somehwere I think.

Yes, I have 4 desktops configured. before starting Compiz. Compiz still only displays 2, rotates like a sheet of paper. it's really weird.

---

### Post by boof1988 on 2009-06-19
> **brew1brew said:**
> Yes, I have 4 desktops configured. before starting Compiz. Compiz still only displays 2, rotates like a sheet of paper. it's really weird.

Are your desktops set-up as...

1x4
-or-
2x2

...this may be a clue.  Does it have to be 1x4 in order to use the *cube*?  *dunno*

---

### Post by Chris Musampa on 2009-06-19
The cube works for me but as markbuntu says that is using KDEs own (kwin I think) desktop effects, I've never installed compiz.

System Settings, Desktop, Enable desktop effects then open "All Effects" and select the cube.

---

### Post by Therion on 2009-06-19
> **boof1988 said:**
> Does it have to be 1x4 in order to use the *cube*?  *dunno*
Pretty much, yeah.  Since a cube has six sides and you want to use four of them as desktops you need to reconfigure your desktops from a total of 2 to 4.  You also need to enable the Cube plugin as well as "Rotate Cube" to spin it.  In Gnome this is done via the CCSM (Compiz-Config Settings Manager).  I'm not sure what the equivalent application is for KDE.

---

### Post by brew1brew on 2009-06-19
> **Therion said:**
> Pretty much, yeah.  Since a cube has six sides and you want to use four of them as desktops you need to reconfigure your desktops from a total of 2 to 4.  You also need to enable the Cube plugin as well as "Rotate Cube" to spin it.  In Gnome this is done via the CCSM (Compiz-Config Settings Manager).  I'm not sure what the equivalent application is for KDE.

Thanks, I've done all that, and the cube rotates like a sheet of paper, with 2 sides.

---

### Post by randyklein99 on 2009-06-20
I've noticed that with a 2x2 it rotates as you say, a sheet of paper.  If I change it to a 1x4, it's a cube.

---

### Post by dazman19 on 2009-06-21
really easy for any1 else who reads this thread with compiz do the following:

1) Open compiz config settings manager.
If you dont have it search for it in synaptic, i cant remember the apt-get command to get it. 
2) choose general options under the general category.
3) choose desktop size tab.
4) by default on ubuntu 9.04 Horizontal virtual size is set to 2. I assume this is the same for kubuntu/edubuntu.
Change this setting to 4. You do not need to increase the number of desktops. Mine is set to 1. And my cube has 4 sides. :D

---

### Post by brew1brew on 2009-06-22
> **dazman19 said:**
> really easy for any1 else who reads this thread with compiz do the following:

1) Open compiz config settings manager.
If you dont have it search for it in synaptic, i cant remember the apt-get command to get it. 
2) choose general options under the general category.
3) choose desktop size tab.
4) by default on ubuntu 9.04 Horizontal virtual size is set to 2. I assume this is the same for kubuntu/edubuntu.
Change this setting to 4. You do not need to increase the number of desktops. Mine is set to 1. And my cube has 4 sides. :D

Dazman, DUDE! that was exactly what I was looking for! Thank you very much, I was having a hard time locating that config. 

My cube is no longer a sheet of paper! :D

---

