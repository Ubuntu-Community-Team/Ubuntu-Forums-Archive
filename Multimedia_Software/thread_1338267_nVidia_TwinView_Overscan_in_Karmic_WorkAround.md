---
title: "nVidia TwinView Overscan in Karmic WorkAround"
date: 2009-11-26
forum: Multimedia Software
---

### Post by ncpokrt on 2009-11-26
I have been messing around with nVidia X settings and TwinView.  My system is working fairly well so far.  I have a CRT and LCD TV.  The TV overscan caused my cursor to fall behind the monitor on the edge of the screen.  I tried to fix it in Jaunty by using the "TVOverScan" option.  That made xorg crash on reboot.  That wasn't my only problem and since I really didn't have anything on this new system to loose, I made a fresh install of Karmic.

I used the nVidia X Server Settings to set up my TwinView.  There is an option (that you only get after you enable the TV and Apply) that allows you to set the overscan compensation dynamically, which is very nice.  Only one problem, when I reboot the overscan compensation goes away.

The work around is to start nVidia X Server Settings and immediately quit.  The overscan compensation then takes effect.

---

### Post by phony on 2009-12-17
Would that really count as a work around? If I understand correctly, it would mean going into nvidia X server each restart and setting the overcale compensation.

I'm using a TV exclusively, and this is a bit exhausting. There has to be a way to make Nvidia X server save our overscale compensation preference for good?

---

### Post by ncpokrt on 2010-01-07
You don't have to reset anything.  If you just invoke the NVIDIA X Server Settings it works fine. The overscan is set where is was when you shut down.  I put Server Settings as one of the Startup Applications and I just quit when it shows up. 

This is not elegant.  That is why it is a workaround and not a solution.

---

