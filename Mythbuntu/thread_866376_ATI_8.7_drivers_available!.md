---
title: "ATI 8.7 drivers available!"
date: 2008-07-21
forum: Mythbuntu
---

### Post by dsbw on 2008-07-21
The July drivers are out on the ATI site.

I'll report back when I try 'em out. Anyone else feel free to use this thread to report their experiences.

---

### Post by dsbw on 2008-07-21
[duped from the Smooth ATI thread, in case people check here]

Well, I'm more-or-less in the same boat. Horizonal line displacement, so I get two half images.

For a brief moment, it adjusted itself and worked. DVD play worked (though some TV trouble)...and then when I exited and came back it was back to double-vision.

I think this can be resolved; but no clue as to where to look. Maybe an xorg.config thing. AMDCCCLE isn't providing any intersting options.

---

### Post by The Tronyx on 2008-07-21
No real problems so far but there is still some issue with fglrx and wine.  This has been something that a lot of people have been experiencing from what I have seen and if anything changes in the next few days I'll report back.

Other than that small hiccup the drivers seem to be working great =D

---

### Post by Lindsay.Mathieson on 2008-07-22
Any luck with hardware accelerated video playback?

---

### Post by Canis familiaris on 2008-07-22
Should I try it in my ATi x1250?
Does it stop video flickering without patch?

And does it stop OpenGL flickering?

And also does it support Radeon 3870 X2?

---

### Post by ihancioglu on 2008-07-22
@*Anurag_panda ; videos still flickering with new version , opengl as well..

Also screen corruption is still remain when start OpenGL applications.
One of new features is introduction support of ubuntu 8.04 , what is the support means? All problems are still remains :confused:

---

### Post by Canis familiaris on 2008-07-22
> **ihancioglu said:**
> @*Anurag_panda ; videos still flickering with new version , opengl as well..

Also screen corruption is still remain when start OpenGL applications.
One of new features is introduction support of ubuntu 8.04 , what is the support means? All problems are still remains :confused:

So I will not try it.

---

### Post by External on 2008-07-22
Alright, everything for the community. **So I DID try Ati Driver 8.7 for Linux.** It was a ***VERY BAD*** idea. I installed it on my fresh Gutsy distro, thinking that if Ati 8.4 worked well previously, as it did, this might be even better. I was wrong.

I have an x700 Ati Mobility Radeon card in my laptop. I am using Gusty, because having tried Hardy I was forced to realize that it is giving me, along with a whole buch of other people, unfortunately, totally random lockups that make any work on the computer impossible.

As usual I went by the Unofficial ATI Linux Driver Wiki, and followed the method described for Gutsy, which is mostly identical to that of Hardy. Even though the guide refers to driver 8.4 for Gutsy and 8.6 for the dreaded Hardy, for you to be able to create .deb packages from the downloadable .run package, you not only need to install fakeroot, debconf and the like, as detailed in th guide, but also, you will need to install cdbs, too, like this:

> sudo apt-get install cdbs

Once again, this is NOT in the guide, but I was smart enough to figure it out. Hurray. Finally, 5 distinct .deb files were created, the recommended install order for which is, as I experienced, starts with the kernel component, and the rest (I followed it with the driver itself and finally installed the catalyst menu as the 5th necessary item.)

I was supposed to restart the computer at this point. I never returned to the same Ubuntu install again. I waited 10 minutes straight when rebooting, did this twice and then I lost my temper and patience and reinstalled the whole distro.
So if you are brave enough to risk your OS and find it adventurous trying to recover your data embedded in your personal forlders in recovery mode or a rescue cd (fortunately I didn't have anything important saved in my system yet), then go ahead and try Ati Driver 8.7, if not, stick with 8.4 or the one in the repo, whichever version it may be. You may, or may not experience the same disaster, but **you have been warned!**

---

### Post by seapahn on 2008-07-22
I was running 8.5 since 8.6 was rather unstable on my dual head (HDMI and DVI) x1250 running ubuntu 8.04. Catalyst 8.7 seems to be doing good. XV works fine. Mplayer doing good. glxgears and fgl_glxgears working fine on both displays.

The only problem I had was when running mythtv, I get the dual image corruption thing on the main display (there is basically 2 copies of the image all distorted, on each half of the screen). When I VNC in it's fine so it has to be some sort of driver/X problem.

But running mythtv in window mode (not full screen) is doing the trick for now. Seems to be more stable than the 8.5 as I was having problems with 8.5 starting up (had to switch back and forth from text console to graphics to get the HDMI display to show up).

All in all, I plan to stick for 8.7 for now. It's almost there where I can say it totally works for me :)

---

### Post by External on 2008-07-22
Ok, additional note: before installing the driver I uninstalled a certain package which might have caused the trouble, but I'm not gonna repeat the experiment now; at the moment I don't feel like staring at progress indicators for the next 2 hours. But, I do acknowledge at this point that **I** might have caused the problem. Still, be careful y'all.

---

### Post by seapahn on 2008-08-22
As an update, with 8.8, all my problems seems to have been fixed. Dual displays work great ... HDMI and DVI no problem ... full screen mythtv and f-spot (picture viewer) also no longer cause any corruption ... xv video fairly smooth.

At this point, I am willing to say that finally with 8.8, I have a fully working driver and everything is as it should be (as far as I have seen). I don't run any crazy 3d things but basic opengl stuff also seem to be working fine.

As a bonus, my HDMI audio also finally works with the latest alsa drivers. Whooo hooooo.

---

### Post by chalewa on 2008-08-22
excited to try when i get home. i just hope that xorg 7.4 support comes soon

---

