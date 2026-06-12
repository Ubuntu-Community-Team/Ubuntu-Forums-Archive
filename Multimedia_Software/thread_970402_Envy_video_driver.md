---
title: "Envy video driver"
date: 2008-11-04
forum: Multimedia Software
---

### Post by sirdouglas on 2008-11-04
I swear, absolutely nothing works with me with Ubuntu.  I know I'm quite the newbie, but seriously, configuring it and getting everything to work has been a month-long process and consumes so much time as nothing gets done.

Okay, enough complaining.  After seeing that video on youtube of compiz fusion, I needed to have it.  So I found a nice tutorial online (which seemed quite straight-forward and easy to do) and went through the process.  First problem, Envy won't install my video drivers.  I ended up just skipping that step, but it must be necessary as the compiz fusion isn't working.  

I didn't know whether I had nvidia or ATI video card.  My laptop is an HP dv1315cl.  After researching on google, I'm pretty sure I have an Intel Graphics Media Accelerator 900 - 128mb (shared).  Well, I still tried Envy with both options and here's the error log I got after trying ATI:

python pulse.py ati 
root@sirdouglas-laptop:/usr/share/envy# python pulse.py ati
ENVY ERROR: ATI card not found

... and the same happens trying Nvidia.  How can I make my video card work?  I haven't noticed it affecting anything on my laptop (I don't game), but it seems necessary for compiz fusion.  Please help, I really love Linux, but I don't want to give up on it as it's causing lots of work for me!

Thanks everyone!

Doug

---

### Post by overdrank on 2008-11-04
> **sirdouglas said:**
> I swear, absolutely nothing works with me with Ubuntu.  I know I'm quite the newbie, but seriously, configuring it and getting everything to work has been a month-long process and consumes so much time as nothing gets done.

Okay, enough complaining.  After seeing that video on youtube of compiz fusion, I needed to have it.  So I found a nice tutorial online (which seemed quite straight-forward and easy to do) and went through the process.  First problem, Envy won't install my video drivers.  I ended up just skipping that step, but it must be necessary as the compiz fusion isn't working.  

I didn't know whether I had nvidia or ATI video card.  My laptop is an HP dv1315cl.  After researching on google, I'm pretty sure I have an Intel Graphics Media Accelerator 900 - 128mb (shared).  Well, I still tried Envy with both options and here's the error log I got after trying ATI:

python pulse.py ati 
root@sirdouglas-laptop:/usr/share/envy# python pulse.py ati
ENVY ERROR: ATI card not found

... and the same happens trying Nvidia.  How can I make my video card work?  I haven't noticed it affecting anything on my laptop (I don't game), but it seems necessary for compiz fusion.  Please help, I really love Linux, but I don't want to give up on it as it's causing lots of work for me!

Thanks everyone!

Doug

Ok what version of ubuntu are your using, Hardy 8.04, Intrepid 8.10?
If you have a intel graphics set you should be able to use compiz.
To verify the graphics card, you can use the command lspci in the terminal located under applications, accessories. Look for VGA.
Also if you look at the FAQ's link in my signature, it has some good info and also compiz-check is a great tool.

---

### Post by sirdouglas on 2008-11-04
Thanks, I'm using version 8.10 of Ubuntu, and after checking in the terminal I confirmed that my video card is: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03).  Woohoo.

So, it should work already you say?  I installed Compiz, hit alt-f2, and typed in compiz --replace for it to run.  The screen flashed and all the applications from my 5 previous desktops compiled into one.  But I don't see any cube like I've seen in the videos.  Also, all the borders from my application windows seem to have disappeared.  I type alt-f2 again, but nothing happens.

Any ideas?

Thanks so much!

Doug

---

### Post by m_duck on 2008-11-04
Yeah check out the FAQ link in overdranks sig. It explains how to enable the cube and a few other bits too.

I *think* the Intel graphics drivers should be installed by default (they are in my laptop) so there is no need for envy as it is for ati and nvidia cards only.

---

### Post by sirdouglas on 2008-11-05
Wooohoo, got it working with that icon.... only problemo is that none of my windows have borders.  Any way to fix this one?

Thanks!

Doug

---

### Post by Spinalcracker on 2008-11-05
Try going to synaptic and installing emerald.  Then with right clicking fusion-icon go to window decorator and choose emerald.  You can get new emerald themes from [gnome-look.org]("http://www.gnome-look.org").

---

### Post by sirdouglas on 2008-11-06
Alright, so I installed emerald and at first everything seemed to work just fine (windows had borders again).  But the I realized the compiz fusion wasn't deactivated.  Ugh, after turning it on my window borders disappeared once again.  Any ideas with this one?

Thanks!

Doug

---

### Post by Mr_Bumpy on 2008-11-06
Sirdouglas,

How did you install Ubuntu?  Standard or alternate CD?  With a standard Ubuntu installation, Compiz-fusion is installed by default (not sure about the alternate CD).  You can enable it by going to System -> Preferences -> Appearances.  Select the visual effects tab and choose either Normal or Extra.  If all is good, you should now have some basic effects to your windows (you will notice a drop shadow effect under each window).  If your hardware or current drivers aren't capable of running Compiz, then Ubuntu will try to search for drivers.

If the desktop effects work, then you can further customize Compiz by downloading CompizConfig (ccsm) to set up the cube, etc.

If they don't work, I would look at your drivers.  I would think Intel would work out of the box, but I don't know much about their graphics chipsets.

---

### Post by sirdouglas on 2008-11-06
I installed Ubuntu Ultimate Edition 1.4 from a torrent website.  I already have compiz set up to work with the cube, and the cube has been working fine... only problem is having no window borders.  No I just went to appearance and changed the visual effect from "normal" to "extra"... after installing some drivers it applied (Ithink), BUT now the cube doesn't work, so I went back to change it to "normal" again and it shows the "normal" is already selected.  Hm.  

Windows borders are still gone, what do I do?  Thanks guys,

Doug

---

