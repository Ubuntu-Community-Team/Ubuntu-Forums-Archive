---
title: "ati radeon mobility 1350 driver problem"
date: 2010-01-06
forum: Multimedia Software
---

### Post by marin123 on 2010-01-06
hello!
i have a problem with my graphic card...
my desktop effects and compiz work fine, but i cant find xorg.conf file (it seems i dont have a driver installed??).. i want to play games, but i cant (warsow, and other via wine).. my computer cant start a game.. help!

---

### Post by marin123 on 2010-01-07
i did sudo apt-get install xorg-driver-fglrx and now my desktop effects stopped working, but i cant start a game... and i'm still missing xorg.conf file..
i'm on karmic 64 bit...

---

### Post by del_diablo on 2010-01-07
FGRLX/CATALYST DOES NOT LONGER WORK! ATI dropped the support of their drivers on cards older than "Radeon 2xxx"(there is some drivers that is 100% working in the kernel, which is not provided by ATI), it before the new x server was out so......... in 8.10 ATI was a mess for pre-2xxx cards.
Now that we got the mess out of the system:
*Head to the IRC of #archlinux or #gentoo and ask how to get the experimental/stable kernel included drivers to work. Remeber to say that you want to use the stable ATI driver.
*Why is there not a sticky on this? Its NEEDED!

---

### Post by marin123 on 2010-01-07
i will try to go to irc... this is such a mess, i dont mind linux open source drivers, but i cant start games, the rest works fine (without ati drivers)..
if you get a solution, please post here..
thanks!

---

### Post by marin123 on 2010-01-07
finally!!
i screwed everything up :(
i installed envyNG to install ati driver and messed with drivers and now i can enable desktop effects and i cant get maximum resolution (1440x900, im stuck with 1152x864 and in Display i see Monitor: unknown.
can i get video back the way it was (default ubuntu driver)?

---

### Post by Yellow Pasque on 2010-01-07
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by marin123 on 2010-01-08
tried this, but no change...
is there any way to install ubuntu drivers that are installed automatically?
ati drivers dont work for me...

---

### Post by marin123 on 2010-01-27
this is what i found out... if i install xorg ati binary driver from the repository, my panel looks nice (all of the icons look ok, right now my amsn does not look nice), and i cant enable desktop effects...
without this driver installed, desktop effects can be enabled but i cant start any games (or anything that requires good graphic performance)...

does this mean if i want to play games on my ubuntu i have to buy a new graphic card?? because my is no longer supported by ati??
omg, i guess i'm stuck with dual boot... :(

---

### Post by sports.car.guy on 2010-01-27
> **marin123 said:**
> this is what i found out... if i install xorg ati binary driver from the repository, my panel looks nice (all of the icons look ok, right now my amsn does not look nice), and i cant enable desktop effects...
without this driver installed, desktop effects can be enabled but i cant start any games (or anything that requires good graphic performance)...

does this mean if i want to play games on my ubuntu i have to buy a new graphic card?? because my is no longer supported by ati??
omg, i guess i'm stuck with dual boot... :(

There is a driver installed. Otherwise you would have no GUI to look at. Odds are you are using the default driver shipped with X. On the note of xorg.conf, every, and I mean every Linux machine with Xorg's X server on it has that configuration file. It is needed for Xorg to load.

It is in:

/etc/X11

There should be little need to use the solution the other poster talked about, unless you are looking to use something that is actually GPU intensive beyond normal use. AMD / ATI has been moving towards having the Open Source community support the driver side. It is a great thing, but due to how UVD / UVD+/ UVD2 were implemented, it won't be likely the Open Source drivers will support hardware decoding and acceleration of video as the proprietary drivers are now finding support for.

Regrettably this is because in the design of UVD and extending on it, DRM was tied closely into all of the code on the GPU die and AMD is bound by confidentiality agreement not to divulge code or specifications on it. This is mostly due to HDCP and Blueray, both incorporated, and both long since cracked. HDCP actually was known to have gaping security holes in it well before it's implementation.

Depending on which of the free drivers you use, there are pros and cons, then there are also option flags that help out one performance wise but not the other. A little reading on both should help you decide which of the two free drivers will suit your needs.

---

### Post by marin123 on 2010-01-28
i'm looking for gaming performance... in windows i could play call of duty 2 and batman arkham asylum, but in ubuntu i cant even get warsow working (cant start), urban terror barely works (slow graphics), and counter strike 1.6 and motocross mania (over wine) are a shame (i can get to the menu but cant play-screen flashes and when i shoot, the shot gets fired 2 secs after)...

---

