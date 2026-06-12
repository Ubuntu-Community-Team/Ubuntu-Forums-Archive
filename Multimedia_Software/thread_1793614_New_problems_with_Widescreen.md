---
title: "New problems with Widescreen"
date: 2011-06-29
forum: Multimedia Software
---

### Post by dinobottm2 on 2011-06-29
Hi again. I have a brand new issue with my widescreen Monitor since upgrading my Ubuntu. I have the resolution i want avaliable and it works perfectly, but no matter what i do, it resets to a basic 1024X768 everytime i restart my computer. I just cant make it save the screen config. 

My screen is an LG 22" 22lg30r, and an NVidia card with the right drivers. Im posting my xorg file here. And thanks for your help.

---

### Post by BicyclerBoy on 2011-06-29
I take it you upgraded from 10.10 to natty 11.04 ?
This seems to be causing lots of problems with nvidia drivers..

Did you use the jockey additional hardware drivers tool ?

You could post your
/var/log/Xorg.0.log
filas as an attachment.

---

### Post by dinobottm2 on 2011-06-29
Actually, i did the upgrade straight from Lucid to Natty.

And i am using the NVidia driver.

---

### Post by BicyclerBoy on 2011-06-30
The gnome menu tool for Hardware Drivers seem a bit broken esp. with nvidia.

You do know that the gnome display preference tools does not work with nvidia ?
You have to use nvidia-settings.

That error message in the end of your Xorg.0.log may have something to do with/be fixed by this intel bug fix in grub:
intel_iommu=off
or   iommu=soft

[http://oliver.net.au/?p=148](http://oliver.net.au/?p=148)
[http://forums.fedoraforum.org/showthread.php?t=239704](http://forums.fedoraforum.org/showthread.php?t=239704)

Was your Lucid install up to date with "updates" before you distro-upgraded ?
Surprising that error did not show up as Lucid is using kernel 2.6.32 (lucid-proposed)

---

### Post by dinobottm2 on 2011-06-30
I forgot to say it before, but the issue is just with my User. The visitant account i created with this [http://tutafuta.com/2011/05/13/convert-your-ubuntu-into-chrome-os/](http://tutafuta.com/2011/05/13/convert-your-ubuntu-into-chrome-os/) and the Login Screen are working right.


> Was your Lucid install up to date with "updates" before you distro-upgraded ?
Surprising that error did not show up as Lucid is using kernel 2.6.32 (lucid-proposed)     It was, but it took me a whole week and the help of a billion people, including this very board, to make it work. This flatscreen is giving me a hard time...

---

### Post by gnusci on 2011-06-30
I hate to say this, but I had a lot of problems after I upgraded from Lucid to Natty with a geforce 240 gt. Now I am running Lucid LTS again. Everything is working OK.

---

### Post by Duncan Williams on 2011-06-30
I had the same basic issue with a nvidia geforce fx5200 graphics card.
23.6" aoc widescreen monitor, supposed to be at 1920by1080 and would keep dropping back to 1080by768.
It worked fine in windows though.
I tried nouveau drivers and nvidia.
I got another graphics card and the problem has gone (and my monitor is correctly found now (ie/ shows as aoc 23.6")

I think that the nvidia card was not working correctly and I think linux was getting errors reading the vram (128mb) so it defaulted to software drivers and basic graphics mode which seems to max out at 1080by768, but it seems ok in windows but would not use nvidia drivers (used vga generic driver in windows)

So yeah, maybe if you tried another video output (borrowed for a day/hour) and checked if your video is the fault.

---

### Post by dinobottm2 on 2011-07-01
Thanks for the tip, but i dont think its the problem. As i said, my  other user doesnt have this issue. I have two users on my comp. Mine,  which is pretty much the same since i started usinb Ubuntu, and a new  one I created just this week. That is what is puzzling me.

Elaborating, the login screen is working at the right definition. My guest user also have the right definition at Unity, at KDE, at Gnome, AND at my Opengox Chromiun-only session. My standard user ONLY have the right setting at KDE. i have the problem i mentioned at all the others. And Gnome is my main enviroment.

---

### Post by gnusci on 2011-07-02
Just install everything using the installer CD, the problem you got was because you upgraded. Your problem will go away.

---

### Post by SeijiSensei on 2011-07-02
Maybe or maybe not.  If /home is mounted separately from the root (/) filesystem, whatever settings reside there won't be updated during a new installation.

I can't help with GNOME as I use KDE.  I can run 

```
cd ~
mv .kde .kde.old

```

then logout and log back in, and I'll get a fresh KDE desktop.  I suspect you can do similar things with .gconf and .gnome, but you'd need to consult an GNOME expert.

---

