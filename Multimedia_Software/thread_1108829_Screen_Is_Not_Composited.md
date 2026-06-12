---
title: "Screen Is Not Composited"
date: 2009-03-28
forum: Multimedia Software
---

### Post by Drobbins on 2009-03-28
Hey Everyone, 

How can i solve the error message "Error: Screen Isn't composited. Please Run compiz (-fusion) or other compositioning manager" 

I am using a Dell GX240 and am unsure what this error means, 

Cheers
Rich
:guitar:

---

### Post by Taus on 2009-03-28
when do you get that error? sounds like a compatibility problem with compiz if you turn off the visual effects does it still appear?

---

### Post by Drobbins on 2009-03-28
I am trying to get the Avant Window Manager to load, i have been configuring the Mac4Lin package and this error appears as soon as the computer starts

---

### Post by Taus on 2009-03-28
what gfx card do you have?

---

### Post by Drobbins on 2009-03-28
Do you know how you find this out? I think it is onboard to be honest.

---

### Post by Taus on 2009-03-28
i think u also need to enable compiz:
System -> Preferences -> Appearance
click the Visual effects tab
choose normal or extra

you could also install the package simple-ccsm

---

### Post by Taus on 2009-03-28
try 

lspci | grep VGA

maybe that returns your vid card

---

### Post by Drobbins on 2009-03-28
i have installed that now using sudo aptitude install simple-ccsm

Also when i check any options under visual effects i get the message 'Desktop Effects Could Not Be Enabled'

Maybe Reboot?

---

### Post by Taus on 2009-03-28
yah, you need to find out what gfx card you have. i think it has to be 3d accelerated in order to use compiz

did the lspci cmd return anything?

if not, you could try to run lspci and look for anything regarding your video controller

---

### Post by Drobbins on 2009-03-28
Wow how cool - *ATI Technologies Inc Rage 128 Pro Ultra T*f.

---

### Post by Taus on 2009-03-28
is there any drivers in System -> Administration -> Hardware drivers

or else we need to find a driver for your gfx on the ati hp... should be there somewhere just haven't found it yet. but i'll keep looking

---

### Post by Drobbins on 2009-03-28
I did look their last night when i first got the issue, that pane is empty.  Their are no drivers at all in their.

---

### Post by Taus on 2009-03-28
hmm i'm quite sure that the video card driver is the problem. still searching for a driver for you... haven't had any luck yet tho..

---

### Post by Taus on 2009-03-28
try this:

gedit /etc/X11/xorg.conf

find the section device and write it in here. I'd like to know if the driver xorg is using is ati or r128

---

### Post by Drobbins on 2009-03-28
[http://ubuntuforums.org/showthread.php?t=510606](http://ubuntuforums.org/showthread.php?t=510606) :S

---

### Post by Taus on 2009-03-28
awww thats a shame if it doesn't support compiz.. *sigh*

---

### Post by Drobbins on 2009-03-28
Taus thanks for all your help though mate :)

---

### Post by Taus on 2009-03-28
no problem bro, glad i could help at least a little :)

---

