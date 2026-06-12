---
title: "Lirc question (Repeats)"
date: 2012-03-01
forum: Mythbuntu
---

### Post by Al_Vampyre on 2012-03-01
Hi Guys,

This one is driving me nuts, I would like to set up repeats on some of my buttons on my MCE remote (Vol+, Vol-, Up and Down specifically). I've edited ~/.lirc/mythtv and every other lirc file I can find but nothing seems to make these buttons repeat. They work fine in XBMC though.

My remote is the MCE Remote v2 1039 without the TV Power button, running 10.10 and 0.24 fixes. The remote was setup using Mythbuntu Lirc Generator.

If you need anymore info please let me know as I'd love to get this sorted.

---

### Post by AlecJ on 2012-03-03
```
sudo nano ~/.lircrc 
``` putting 5 as your repeat value.

---

### Post by Al_Vampyre on 2012-03-03
> **AlecJ said:**
> ```
sudo nano ~/.lircrc 
``` putting 5 as your repeat value.

Thanks for responding, my ~/.lircrc looks like this ```
#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa 
```

That suggests that the repeat options should be in ~/.lirc/mythtv which they are, but altering them makes no difference whatsoever. It seems such a simple thing but I just can't seem to get it to work.

---

### Post by AlecJ on 2012-03-04
Yes I remember that file.

I would rename it out of the way for the time being.
Try my ~/.lircrc file in it's place.

[http://ubuntuforums.org/showthread.php?t=1691425](http://ubuntuforums.org/showthread.php?t=1691425)
Both files worked upto before 11.04, then after a fresh install to 11.10 the files changed some but I still had to edit lircrc to add repeats.

You could cut and paste the contents of the included files from the old file if necessary, but I never had too.

These files contain the remote codes in hex and the names of button's functions
/etc/lirc/lircd.conf
and hardware type, note the driver needs to be addressed in each button function i.e remote = mceusb in lircrc
/etc/lirc/hardware.conf
worth having a look at, to pass some time.

Hope that helps I was using these files for years until a new DVB-S2 card forced major upgrades. the card when back but 11.10 is here to stay.

---

### Post by Al_Vampyre on 2012-03-05
AlecJ, thanks very much for your help but changing the ~/.lircrc hasn't made any difference, running irw shows the buttons repeating but no changes I make to lirc seem to be working. I'm wondering if the addition of the drivers to the kernel means lirc is effectively being ignored?

---

### Post by pblarry49 on 2012-09-26
Though my problem is "stopping" repeats, my symptoms are the same. Since upgrading to 12.04, lirc seems to completely ignore .lircrc. I have tried placing it in /etc/lirc and /home/mythtv (including the links) as well.

It seems no matter what I do, .lircrc is ignored.

Any help would be most appreciated.

---

