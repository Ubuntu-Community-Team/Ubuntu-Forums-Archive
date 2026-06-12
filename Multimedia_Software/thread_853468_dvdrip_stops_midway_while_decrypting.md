---
title: "dvd::rip stops midway while decrypting"
date: 2008-07-08
forum: Multimedia Software
---

### Post by sgr123 on 2008-07-08
I'm on hardy and have all the required libs from medibuntu repository for dvd::rip to work (also have followed medibuntu howto). I am able to view/play dvds fine.

For almost all dvds I try to rip with dvd::rip, the decrypt/rip stops midway, at 70% with no obvious error message. the log when it stalls looks something like this:
Rip - title #1: 70% done
Executing command: execflow tcprobe -H 25 -i /media/sda3/dvdrip/dvd/vob/001/ && echo EXECFLOW_OK

What could be the issue? 
I couldn't get any solution even after extensive search over the net. Hence posting here.

---

### Post by forger on 2008-07-08
just to be sure, try:
> sudo apt-get install --reinstall libdvdcss2 libdvdread3

You could try ripping with thoggen, much easier, could do the trick:
> sudo apt-get install thoggen

---

### Post by switch10 on 2009-12-23
> **forger said:**
> just to be sure, try:


You could try ripping with thoggen, much easier, could do the trick:

I am having the same problem ripping dvd's with DVDRIP.  thoggen works great but the quality is not so good.  

I tried the above and apt couldn't find the above packages in 9.10.  

I did this to install the updated version of libdvdread.
```
sudo apt-get install libdvdread4 vlc && sudo /usr/share/doc/libdvdread4/install-css.sh
```

I am trying to rip a dvd right now, I will post back if this works..

---

### Post by switch10 on 2009-12-23
> **switch10 said:**
> I am having the same problem ripping dvd's with DVDRIP.  thoggen works great but the quality is not so good.  

I tried the above and apt couldn't find the above packages in 9.10.  

I did this to install the updated version of libdvdread.
```
sudo apt-get install libdvdread4 vlc && sudo /usr/share/doc/libdvdread4/install-css.sh
```

I am trying to rip a dvd right now, I will post back if this works..

hmm.  this didn't work.  I am still having this same problem.  While encoding, the process stops at about 75% and thats it.  I have tried many different DVD's, and they always work with thoggen dvd ripper. 

anyone have any ideas on whats going on??  I'm on Ubuntu 9.10..

---

### Post by cboy on 2010-01-17
I'm having the same problem in ubuntu 9.10, stalls after 75% progress.. :(

---

### Post by Rasheeke on 2010-01-28
I do am having this issue on karmic.  

An (unacceptable) fix is I tell dvd:rip to initially rip the movie and then the longer special features.  It stops at 75% but this time 75% is when it's partway through ripping something I don't want to transcode, so I save then close dvd::rip then continue from there.

---

