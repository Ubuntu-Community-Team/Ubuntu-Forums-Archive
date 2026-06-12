---
title: "Nvidia Overscan Issues"
date: 2007-11-10
forum: Mythbuntu
---

### Post by TheJacksonians on 2007-11-10
Hello all,

We officially have tried everything we could possibly find and now offer ourselves up the the Gods of Mythbuntu for a solution to our problem.

I am attempting to connect a Mitsubishi WS-55135 TV to a 7600 GT via DVI. The overscan is terrible in 1920x1080i, I am unable to see either the top or bottom of the screen, which makes doing anything outside of the front end nearly impossible.

I have tried reinstalling the build from the Live CD on up, reconfigured the x-server, and have tried several different Modelines, including those that are are written for my TV.

I am using the Nvidia proprietary drivers.

I first tried connecting with component and still had terrible overscan. A quick search of the forums indicated to me that people have better luck solving DVI overscan.

If you need any more information or a copy of any .conf files please let me know.

Thank you for your time, I really appreciate it.

---

### Post by superm1 on 2007-11-10
Well do you have the option for VGA on your TV instead?  Its common that you will be able to get a resolution with no overscan over VGA.

Otherwise, you have three options:
1) Adjust the size and placement of myth on the tv.  This can be accomplished in the settings->appearance menu on the resolutions page.
2) Go in the TV's service menu.  See what you can do from there.  Some TV's can adjust overscan in it.  Note: the service menu is not the same as the regular menu.  You'll have to google on how to get in on it with your particular tv.
3) A modeline that works around the overscan which you've already tried

---

### Post by TheJacksonians on 2007-11-10
Thank you for the quick reply!


The service menu does not offer a overscan function. It did offer forcing 1080i, but only to the digital TV slot, where it should also expect the V & H  sync. 

Further, the TV only accepts Component and DVI. Also, after looking at the user manual [here,]("http://www.mitsubishi-tv.com/j/i/18326/WS55315.html?cid=17") the DVI input on the tv is made not seemingly designed for direct video card output, but rather a receiver output. So it seems we are back to Component for now. We will do a fresh install of mythbuntu with the Nvidia Prop. drivers tomorrow morning and with the component cables going to the TV. 

We'll let you know how we go from there and probably post our xorg.conf. Thanks again!

---

### Post by roseway on 2007-11-11
I've had this problem too, and I was able to (sort of) fix it by using method (1) but the problem with this solution is that if I exit from MythTV the Mythbuntu desktop is still overscanned, so it's difficult to get at the menus.

Method (3) would be the ideal solution for me, but I'm going to have to learn about modelines.

---

### Post by TheJacksonians on 2007-11-11
We fixed it via the appearance menu. We ended up shaving 200px off the width and 120 off the height, with a 100 offset to x and 60 offset to y. This gave us 1720x960. This will work for now. However, at some point I want to fix this issue. I've read up on modelines, and I think the one I need to use is 
```
Modeline "1920x1080@60i" 77.60 1920 1952 2240 2272 1080 1104 1110 1135 interlace
``` However, I haven't found much on actually implementing that change. Then again, we could just be noobs here and be missing something obvious. 
Thanks again and I appreciate the help so far.

---

### Post by superm1 on 2007-11-12
> **TheJacksonians said:**
> We fixed it via the appearance menu. We ended up shaving 200px off the width and 120 off the height, with a 100 offset to x and 60 offset to y. This gave us 1720x960. This will work for now. However, at some point I want to fix this issue. I've read up on modelines, and I think the one I need to use is 
```
Modeline "1920x1080@60i" 77.60 1920 1952 2240 2272 1080 1104 1110 1135 interlace
``` However, I haven't found much on actually implementing that change. Then again, we could just be noobs here and be missing something obvious. 
Thanks again and I appreciate the help so far.
To use the modelines you will have to read up on how to force the nvidia driver to ignore checks, edid, etc.  I don't know of a good guide for this stuff, but the different things that can be disabled are detailed in the nvidia driver readme on their website.

You can be a first to author this guide if you are so inclined :)

---

### Post by TheJacksonians on 2007-11-12
All right. I've got a oral exam next week, but after turkey day, my roommate and I will start putting together a guide. Hopefully we'll get it right without destroying our TV. I'll put the update on this thread as well as some questions that I might encounter.

---

### Post by roseway on 2007-11-13
I don't know if this is of any value, but there's a modeline calculator at [http://www.bohne-lang.de/spec/linux/modeline/index.html.en](http://www.bohne-lang.de/spec/linux/modeline/index.html.en) . Using Tool 1 you just pick your resolution from a drop-down list and specify the refresh frequency, and the calculator prints a modeline for you. I won't know if it works until I've read up on the nVidia stuff mentioned above.

---

### Post by TheJacksonians on 2007-11-27
Just checking back in. Passed the orals so I'll be free to review documentation and the such for a while.

---

### Post by Vincent_Lin on 2007-11-28
I use component out from Nvidia card to a Mitsubishi TV set, almost the same setup as yours.  The overscan has been killing me for over 2 years.  Prior versions of Mythtv only allowed you to use a "cropped" area in the middle of screen, as someone said, trimming about 200x120 pixels of worth around.  It is still like this for mythbuntu 7.10.  And yes, there is no overscan adjustment in service menu for Mitsubishi I have.

Outside, mythtv frontend, I set the, I think that's what it is called, "Fullscreen size" or "Maximize size' property, right in some of the desktop-right-click-menu entries, so that no portion of any window could go outside the trimmed down desktop as well.  Prior to this property in mythbuntu, I would simply have to enlarge gnome panel size so that the items on the panel are accessible to me.  I think current mythbuntu is a much better improvement.

Hope this helps.  I also think that the best is if you can really find the working "Overscan" option to set in xorg.conf, as this, I think, is the ultimate solution.  You know, true 1080i resolution inside out of mythtv frontend and desktop, and everything is within the screen.

Vincent

---

### Post by Breakablec on 2008-11-22
If you found this thread, vote this up:
[http://brainstorm.ubuntu.com/idea/8811/](http://brainstorm.ubuntu.com/idea/8811/)

---

### Post by ap90033 on 2009-07-20
Uh I have overscan using Nvidia. Works GREAT in Widows so why not in linux???

---

### Post by ap90033 on 2009-07-20
Seems like there would be an easy way to adjust this.

---

### Post by newlinux on 2009-07-20
what kind of connection are you using between your TV computer? Are you using the nvidia propietary driver? Are you looking fix desktop overscan or mythtv overscan?

---

### Post by Kalanac on 2011-07-20
As this is the top result from google I figured I'd update this issue:

The nVidia X Server Settings utility now has an Overscan Compensation function.  You can find this in the GPU 0.  The section is listed as DFP-1 (FOS LCDTV***) on my computer, but it may vary for others.

There is a slider near the bottom of the options, just slide it to the right slowly until you can see all your screen.  I've got mine set to 100 (half of what's possible).  The slider adjusts the scan to stop it cropping the display.

---

