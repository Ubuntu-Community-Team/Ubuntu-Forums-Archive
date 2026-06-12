---
title: "Netstumbler replacement for site survey"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by e24ohm on 2009-03-07
Folks

I am currently running Ubuntu 7.10 on my workstation, and Fedora 10 on my notebook. I am currently doing a site survey of my home network from my notebook. I need a replacement for Netstubler, which will show the dbi, channels and all the other goodies Netstumbler gives.

Does anyone know of a app in the repository, which will give the same amount of information?

Thank you
E

---

### Post by andersja on 2009-12-09
Not quite the same but how about wifi-radar ?

[http://wifi-radar.berlios.de/](http://wifi-radar.berlios.de/)

---

### Post by MunksterMan2 on 2010-04-12
I'm also looking for a suitable tool.  WiFi radar is OK but much more basic compared to netstumbler.  The feature I really would like is a graph of all visible wifi networks with their channel and power level.  Any other suggestions?

---

### Post by chili555 on 2010-04-12
How about Kismet? Please see attached.

---

### Post by mark bower on 2010-04-14
i am new to Kismet so the following may not be accurate.  Kisment does not appear to simultaneously display surrounding APs and their signal strengths in a bar graph form.  it does have a single graphic bar which displays signal strength, but in each new capture the bar is updated for that AP.  i cannot see how to make use of it in that mode. 

however, there is an option to lock onto one AP at a time and 1) graphically display signal strength as a horizontal bar, 2) digitally display its signal strength & noise in dB, and SNR.  also, and what i needed it for, it will display hidden SSIDs.  this is needed to keep channel separation (if possible) from surrounding neighbors.

in my case, the graphic (signal strength) jumps a whole lot while displaying because i get strengths anywhere from -68 to -91db, and noise at about -100db.  thus the SNR is anywhere from 11 to 30.  i am guessing that this is do to a lot of reflections based on my 3 wall traverse.  i am going to play with some parabolic reflectors and see if i can improve things a bit.

mark

---

