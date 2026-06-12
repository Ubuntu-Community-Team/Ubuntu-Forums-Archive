---
title: "GeForce 8600GTS: dualscreen please?"
date: 2008-04-16
forum: Multimedia &amp; Video
---

### Post by sireel on 2008-04-16
Ok, before I start, this is my first post so please forgive any noob mistakes, but do point them out so i don't make them again. I am also relatively new to linux, so if there is a chance I won't know what something means, please take the time to explain it.

First, I'm running Gutsy, with Gnome desktop, hardware is
Intel Core 2 duo, 2.13Ghz
BFG GeForce 8600GTS (can't remember memory amount)
2GB 800Mhz RAM

I updated after the install, and enabled proprietary drivers for the graphics card, and so far all is pretty good (considering), I have one monitor working exactly as intended, at the highest resolution it supports. Unfortunately, looking at the Screens and Graphics preferences, I can't find a way to enable my other monitor, and I'm unsure of how to do this,

In case anyone can explain the lot, I want it set up as two connected but separate screens (can have two app's full screened at once) rather than one virtual screen)

I did check for similar threads, but couldn't find what I was looking for.

Thanks

---

### Post by JRCreations on 2008-04-16
If you've enabled the restricted nvidia driver, this should work:
go to applications -> Other -> Nvidia Settings -> X Server Display Configuration. It should let you activate your second monitor, and the setup you want is TwinView.

---

### Post by sireel on 2008-04-16
Um... in applications -> Other there is no group called Nvidia settings... maybe this is installed with nvidias own driver for the card..?

---

### Post by ad_267 on 2008-04-16
It's not usually in the menu. Open up a terminal and type "sudo nvidia-settings" and enable the second monitor using TwinView. Make sure you save the settings to the xorg.conf file.

---

### Post by ubuntu-freak on 2008-04-16
This doesn't matter all of the time, but use "gksudo" and not "sudo" with GUI apps, just to be on the safe side. 
 
Nathan

---

### Post by sireel on 2008-04-16
Ahhh thankyou all, It now all seems to be working, though it was not twinview that i wanted, but separate screens (I'm not too fussed about moving apps between, but it really annoys me when a game can't go full screen to one screen)

---

### Post by sireel on 2008-04-16
Err actually, for some reason now windows on my second screen appear without a titlebar. I find this moderately odd. any ideas..?

---

### Post by ubuntu-freak on 2008-04-16
> **sireel said:**
> Err actually, for some reason now windows on my second screen appear without a titlebar. I find this moderately odd. any ideas..?

 
That's just weird. Have you logged out and back in?
 
Nathan

---

### Post by ad_267 on 2008-04-16
> Ahhh thankyou all, It now all seems to be working, though it was not twinview that i wanted, but separate screens (I'm not too fussed about moving apps between, but it really annoys me when a game can't go full screen to one screen)

No, you do want TwinView. TwinView gives you separate screens but it uses your nVidia hardware to do most of the work. Selecting separate X screen uses software to do all of this so is slower. You should use TwinView because you can then still use desktop effects and other OpenGL things with two monitors on and it is much more efficient.

I use TwinView and my games go fullscreen on one screen and windows maximize to one screen and can be moved across screens.

Using TwinView will probably also fix your problem with the title bars.

---

### Post by graabein on 2008-04-16
I have an older GeForce card but I have a similar xorg question.

I want to keep my desktop on screen0 (1600x1200 monitor) and add a screen1 (television set) just for  fullscreen from VLC. Is this possible? 

I've tried clone and left-and-right but that messes up my desktop layout or the resolution...



Update:

Some googling led me to these HOWTO pages. I'll try to use nvidia-settings before I manually edit xorg.conf though...

[http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV]("http://gentoo-wiki.com/HOWTO_Separate_x-screens_on_Monitor_and_TV")
[http://gentoo-wiki.com/Talk:HOWTO_Separate_x-screens_on_Monitor_and_TV]("http://gentoo-wiki.com/Talk:HOWTO_Separate_x-screens_on_Monitor_and_TV")

The key options looks to be in **section ServerLayout** dropping left-of, right-of and clone all together:
```
Screen 1 "Screen[1]"
```

And maybe this setting in **section Device** for the television set to avoid resolution problems:
```
Option "ConnectedMonitor" "CRT, TV"
```

---

### Post by sireel on 2008-04-16
I tried twinview, and picked a random game that would fullscreen (the tron lightbike game in the application manager) and it tried to go fullscreen to both screens.. is there something I would have to change to fix this...?

Edit: ignore all that, tried again and it magically full screened to one screen. how bizarre

---

### Post by ad_267 on 2008-04-16
> **sireel said:**
> I tried twinview, and picked a random game that would fullscreen (the tron lightbike game in the application manager) and it tried to go fullscreen to both screens.. is there something I would have to change to fix this...?

Edit: ignore all that, tried again and it magically full screened to one screen. how bizarre

If that happens again then make sure there is a separate meta mode that uses only one screen and has the other set to null. You can do this in nvidia-settings by clicking advanced.

---

### Post by Roque2 on 2008-04-16
Not sure if this will help you out any [http://howtoforge.com/dual-monitor-setup-on-ubuntu7.10](http://howtoforge.com/dual-monitor-setup-on-ubuntu7.10)

---

