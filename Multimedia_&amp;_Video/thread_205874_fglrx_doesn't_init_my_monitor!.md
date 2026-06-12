---
title: "fglrx doesn't init my monitor!"
date: 2006-06-29
forum: Multimedia &amp; Video
---

### Post by JavanBuddhi on 2006-06-29
All right guys very strange problem here.

I run a Gigabyte 9600XT on a KT400 board with a SyncMaster 730B monitor.  My problem is, whenever I install fglrx and tell xorg.conf to use it, my screen doesn't load.  It gets to the splash and all that stuff, but when it is supposed to start gdm, the screen goes black for a while, and then it starts trying to find a signal between its vga and dvi ports.  Continues for about 15 seconds, and then goes to standby.  

I do all this on a 2.6.25-k7 kernel

weird thing is, before I did a system update (pristine dapper install w/ automatix)  fglrx would work but i couldn't see everythuing.  It was like only a part of the screen would refresh until the cursor moves over the rest of it (this example was in gedit).  that was with a 2.6.23-386 kernel.  Now I get absolutely nothing

Xorg.0.log tells me that 9600XT isn't supported. Instead, fglrx found a 9600 Pro.  also, I noticed that it said that it couldn't find anything on BusId 1:0:1.  Thing is, vesa works perfectly with BusId 1:0:0, the thing that xorg config found.  

Please help me get video back onto my Computer!

btw, if it is of importance, I could never get ati drivers working for more than a day in XP after I did a repair install (before i installed  dapper)

---

### Post by harishg on 2006-06-29
I think flgrx driver does not work with your ati graphics card.You can restore the  x the following way.Go to /etc/X11 and look for some file named xorg.conf_backup or something similar assuming you backed up your xconfig file.

If you find something like that do 

sudo  cp  xorg.conf.backup  xorg.conf

If you are not sure post the contents of your /etc/X11 folder.

---

### Post by harishg on 2006-06-29
I forgot to mention.Enter in the recover mode and check it.When the root prompt comes up type 

cd /etc/X11
ls 

hopefully the config file should have been backed up.
then 

cp xorg.conf_back  xorg.conf

---

### Post by JavanBuddhi on 2006-06-30
Thanks for all your help, but well...that si how i am working right now.  BTW, i think that my card does work, because jgcamp somehow got it working.  Also, i must add that the "ati" driver never worked. I am forced to use the "vesa" driver.

---

