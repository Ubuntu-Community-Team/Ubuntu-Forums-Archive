---
title: "Trying to install mythtv feisty fawn but craches after gdm start"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by kopite on 2007-07-23
Hey guys.

Ive been following the guide here : [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend)

Everything seems to go alright until I do ```
sudo apt-get install ubuntu-mythtv-frontend
```

THe files seem to install although there seems to be some lines about not being able to create some directories for fonts. Everything else seems to install fine.

I then do ```
sudo /etc/init.d/gdm restart
``` and the hard drive seems to do something and then the screen goes into standby as though the graphics card isnt sending a signal and the keyboard lights start flashing.

I have redone the guide a couple of times but each time the same thing happens.

The setup of the box is 

NFORCE LANPART Ultra mboard
ATI Radeon x800
Hauppage pvr 350
HAuppage hvr 110
1 gig crucal ram
AMD 64 3000 cpu

64bit feistyfawn.

ANy help would be brilliant. I`m pulling my hair out here and havent got a clue what is causing this.  Plus my family is getting really annoyed with computer parts being all over the front room

---

### Post by kopite on 2007-07-24
Come on guys. Surelly someone has an idea what could be causing this.

Wondering if it could be the ati x800 graphics card as when I try and install From the standard live cd it crashed out when  trying to load the gui.

I can log on to command line as root in recovery mode so was wondering if anyone has any ideas where I can look for clues as to what is causing the problem.

---

### Post by dabl on 2007-07-24
24 hours -- no answers -- OK, I'll offer two cents' worth (and that's doubtful ...).

I would say you need to nail your video display issue first, if there is one.  I don't speak "ATI" so I can't help you with your x800, but you can be pretty sure MythTV isn't going to act right if there is a display issue going on.

Also, if you can capture those errors that come up when you install the front end, they might be instructive regarding the remaining problem with running it.

HTH  :)

---

### Post by kopite on 2007-07-24
Right I`ve used recovery mode and looking in the xorg log and also the log in the gdm folder.

both have the following line

AIGLx: screen 0 is not DRI capable

COuld this be what is causing the crashes?

---

