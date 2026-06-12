---
title: "Problems with Intel 965 Graphics in Ubuntu 7.10"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by Doughy on 2007-10-19
I posted this in the Desktop Effects forum, but copied it here because it probably belongs here...

I just installed Ubuntu 7.10 Gutsy. I am currently running my graphics with the integrated chip on my Intel 965 motherboard. I am having some issues, and wondering if anyone out there knows how I can fix them.

   1. Desktop effects will not enable. Right now, when I look at the driver that is being used it just says it is the "vesa compliant driver."
   2. Is there a better driver that I should be using for the intel 965 chip? I tried changing to different drivers in the new "screens/graphics" control panel, but nothing else worked.
   3. My monitor (ACER AL1916) does not support some of the refresh rates that some of the drivers are trying to put out. How can I make the drivers use only refresh rates that my monitor supports? I tried setting my monitor in the "screens/graphics" panel to my model, but only the "plug n' play" monitor setting seems to work.


I thought X.org was supposed to be way better for intel graphics. I also thought that intel open-sourced their 965 graphics driver, so why is it so spotty? Any help or answers to any of these questions is appreciated. Thanks.

---

### Post by Doughy on 2007-10-19
Furthermore, my computer won't suspend from the GDM, DOH!  I thought Gutsy was going to be much stabler.... :(

---

### Post by cwhitehouse on 2007-10-19
I have a Intel 965 card in my Thinkpad as well.  Sadly it's just currently blackedlisted on the Compiz site due to bugs in the driver.  There are ways around it if you search the forums but it can hose your video playback from what I hear.

---

### Post by crash0 on 2007-10-19
is this some permanent issue or what? and does it affect only compiz(-fusion) or all composite managers?

is there a way to install beryl? (i can't seem to find it in the repositories)

---

### Post by Doughy on 2007-10-19
I am getting fed up with the intel 965 graphics.  Looking on new egg for a nvidia card right now.

---

### Post by cgreydak on 2007-10-21
look into the following

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Release_Candidate_on_a_ThinkPad_T61#Accelerated_Video_and_Desktop_Effects](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Release_Candidate_on_a_ThinkPad_T61#Accelerated_Video_and_Desktop_Effects)

[http://www.realistanew.com/2007/09/23/compiz-in-ubuntu-update/](http://www.realistanew.com/2007/09/23/compiz-in-ubuntu-update/)

I have Sony VAIO VGN-160e/s that works fine with exception of compiz fussion

---

### Post by Doughy on 2007-10-21
Regardless of the fixes, there is a reason the 965 driver is blacklisted.  Besides the desktop effects, I have had other problems with it.

I ordered an nvidia yesterday.  Time to upgrade and get off the integrated graphics.

---

### Post by xerxesb on 2007-10-22
i've got similar problems. If you remove the blacklisting from the compiz config you can get compiz to run, but you will have problems playing media.

Another problem i've discovered is poor performance running WoW under wine. Tried all the hacks, and the only thing left is to re-compile the intel driver incase the Gutsy release is outdated.

could  do with some help in this area!

thx
-x

---

### Post by crash0 on 2007-10-30
> **xerxesb said:**
> i've got similar problems. If you remove the blacklisting from the compiz config you can get compiz to run, but you will have problems playing media.
exactly... i can't get any app to run videos. i've tried totem and mplayer and both crash.

---

### Post by Dai777 on 2007-10-30
I also have these problems running an acer M5600 with an AL1716 monitor. can you get your monitor to change resolutions mine goes into psychedelic mode when I try it.

---

### Post by Doughy on 2007-10-30
Just got a new graphics card and now my problems are gone.  Intel 965 driver sucks.

---

### Post by Crsh on 2008-01-13
I've got a 965 Chipset, and I've also had problems with graphics (screen going blank, error messages). I read on the Intel site that the distros may only have the drivers through the 945 model. Apparently, the only solution is to wait for Hardy Heron or wait for Ubuntu to send out a driver update.

I could simply swap out my integrated card for a proper dedicated card, but I'm running a Lenovo 3000 notebook and don't know how to do it easily. I suppose that it would mean an expensive installment job.

---

