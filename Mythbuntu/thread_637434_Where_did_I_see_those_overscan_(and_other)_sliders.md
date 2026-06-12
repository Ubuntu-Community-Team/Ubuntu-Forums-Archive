---
title: "Where did I see those overscan (and other) sliders?"
date: 2007-12-10
forum: Mythbuntu
---

### Post by wilberfan on 2007-12-10
I've installed myth a few times (long story--don't ask), and on at least two occasions I've seen a screen that allowed me to adjust--via horizontal sliders--things like overscan (i can remember how cool it was watching the image get larger and smaller) and something that seemed to make the text on the screen sharper...

I must have spent half-an-hour today looking for that screen again!   I've been through every front- and backend setup/config option I could find...

Does anyone remember where those sliders are--and how I can get to them?

---

### Post by stevetv on 2007-12-11
its not in the mythtv fe or be settings.  its nvidia settings.  you can get there from the mythbuntu control settings... either accessable through the mythtv frontend.. or from gnome

---

### Post by wilberfan on 2007-12-11
> **stevetv said:**
> its not in the mythtv fe or be settings.  its nvidia settings.  you can get there from the mythbuntu control settings... either accessable through the mythtv frontend.. or from gnome

Ah, yes...the nvidiia settings!   I was beginning to wonder if it might be in that end of things...   Thanks!

The problem I'm trying to solve is a series of faiint grey bars that are constantly drifting from bottom-to-top on my TV.  The nvidia sliders didn't affect that.   

What could be causing those?   The refresh rate?   Interlace?   Could it be due to some kind of interference?  

Kinda new at all of thiis...

---

### Post by mthaddon on 2008-03-20
I'm also looking for this. I've brought up the nvidia-settings dialog, but can't find it. Can someone point out exactly where it is for the blind like myself?

---

### Post by majoridiot on 2008-03-20
> **mthaddon said:**
> I'm also looking for this. I've brought up the nvidia-settings dialog, but can't find it. Can someone point out exactly where it is for the blind like myself?

unfortunately, the overscan settings are not implemented for all of the nvidia gpus yet.  i'm still
waiting for nvidia to add them for my 8600GT.

---

### Post by mthaddon on 2008-03-20
Is there any way of setting it in xorg.conf?

---

### Post by majoridiot on 2008-03-20
> **mthaddon said:**
> Is there any way of setting it in xorg.conf?

you might post the model of your gpu, in case someone has had success with this.

i tried every "fix" and "work-around" i could find, but could find no way of forcing overscan from
xorg.conf settings... a slew of custom modelines, included.  i work around it on my plasma
by adjusting the workspace borders, etc. so that windows are placed on the viewable area of the
screen when working on the desktop.  there are a lot of settings you can adjust to compensate,
until nvidia finally gets it together and implements it into nvidia-settings... like it is in windoze.

---

### Post by mthaddon on 2008-03-20
Sure, it's a 128MB NVIDIA GeForce 8300GS.

Definitely interested if anyone has any work arounds fort that.

Cheers, Tom

---

### Post by laga on 2008-03-20
> **wilberfan said:**
> 
The problem I'm trying to solve is a series of faiint grey bars that are constantly drifting from bottom-to-top on my TV.  The nvidia sliders didn't affect that.   

What could be causing those?   The refresh rate?   Interlace?   Could it be due to some kind of interference?  


You're probably experiencing something called "ground hum" or "ground loop".. Google knows how to get rid of that. Make sure to apply some common sense, I've seen "solutions" involving rather unsafe modifications to power cords :shock:

---

