---
title: "DVI blank screen"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by bulazeem on 2007-09-05
I have read quite a few threads regarding problems with using DVI and having a blank screen.  However, my problem is a bit different.  When i turn on my computer, the screen is black and the monitor can not pick up a signal.  I hold my up arrow on startup for about 10 seconds so that i can scroll up my grub menu to the ubuntu option and then press enter when it seems that there is no more loading going on (i dual boot ubuntu 7.04 and windows xp.  currently winxp is the default os [please dont flame me] because i am an ultra-noob with ubuntu and dont feel comfortable making a full switch quite yet [but i will!]).  I see the lights on my case flickering showing that the hard drive is working and i hear clicks that also confirm this.  Once i get to the login screen, my monitor becomes active and from there on out, everything seems normal.  If i use a VGA cord, i can see everything that is going on.  However, i cant see anything with the dvi cord until i get to the login screen of ubuntu (or the login screen of windows as a matter of fact).  I have to use VGA if i want to change any of my settings in my BIOS however, i dont see anything mentioning DVI in there so i guess it has to do something with the OS.  My motherboard is a LanParty UT NF3 250GB, my monitor is a Dell 2005FPW, and my gfx card is Nvidia GeForce 6800.  Here is my xorg.conf (i hope i uploaded it correctly.  i put it as a .txt file b/c it said xorg.conf wasnt valid)
Thank you very much :)

---

### Post by bulazeem on 2007-09-05
anyone?  :(

---

### Post by Vich on 2007-09-06
Are you saying you don't even see the POST or the GRUB menu?
Until you get to GRUB it hasn't loaded anything from the hard-drive, and even in GRUB the graphics settings are separate from the xserver settings (xorg.conf)

---

### Post by bulazeem on 2007-09-06
Correct.  Until i get to the login screen of either ubuntu or windows, my monitor stays blank and the power light on it stays orange.  I have been using the DVI feature for just a bit over a year and it worked perfect until a week ago.  The only way for me to see the lanparty logo or the grub menu is for me to plug in my VGA cord.
So from what your saying it could be something wrong with my bios?  I have never updated them and i tried setting them back to fail safe defaults.  Still no results :(     Maybe ill just use VGA all the time.  is there much of a difference anyway?

---

### Post by bulazeem on 2007-09-09
anyone?  :(

---

### Post by bulazeem on 2007-09-13
still blank on startup.  any sugguestions?

---

### Post by h0me5k1n on 2007-11-12
Your BIOS wouldn't have an option to set the default display device to "DVI" unless the DVI graphics port was directly on the motherboard.

The BIOS should probably be set to AGP or PCI-E depending on the type of graphics card you have.

---

