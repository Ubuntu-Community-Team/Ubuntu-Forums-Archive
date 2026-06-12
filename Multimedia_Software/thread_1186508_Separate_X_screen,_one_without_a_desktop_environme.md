---
title: "Separate X screen, one without a desktop environment"
date: 2009-06-13
forum: Multimedia Software
---

### Post by ariel on 2009-06-13
I'm using my desktop PC as a media center with XBMC. I have an NVIDIA 8600 card with dual DVI; I configured xorg manually to have two separate X screens, one is my desktop LCD panel, the other is my 1080p LCD TV.

Currently, when I login to the PC I get two independent desktop environments (I'm using gnome), one in each screen. I'd rather remove the desktop environment from the TV screen, because it is useless there and also bothers me with the screensaver (I want the screensaver only in desktop LCD panel screen). 

Is there a way to prevent gnome (or whatever desktop environment) from loading into my DISPLAY :0.1 ?

---

### Post by xc3RnbFO8P on 2009-06-13
Did you try in Nvidia settings,  separate screens?

---

### Post by ariel on 2009-06-14
> **Ringi said:**
> Did you try in Nvidia settings,  separate screens?

Yup, that's exactly what I am using. 

Now, both "separate screens" load gnome by default. I don't want a gnome in my TV, I just need XBMC there running fullscreen all the time. Right know, gnome in the tv causes some grievance because of the screensaver and some random problem that makes xbmc to startup in a window instead of fullscreen. So first thing, I want to remove gnome from the TV screen, hopefully this is possible... hints anyone?
thxs!

---

### Post by leodp on 2010-11-16
> **ariel said:**
> Yup, that's exactly what I am using. 

Now, both "separate screens" load gnome by default. I don't want a gnome in my TV, I just need XBMC there running fullscreen all the time. Right know, gnome in the tv causes some grievance because of the screensaver and some random problem that makes xbmc to startup in a window instead of fullscreen. So first thing, I want to remove gnome from the TV screen, hopefully this is possible... hints anyone?
thxs!

Hi, have you solved? I reply in case someone is interested.
Some hints: 
-Can you log out of the gnome session in the TV monitor only and login again in a different windows manager (or in XBMCstandalone or whatever its name is)?
-In XBMC there's a  shortcut to go fullscreen. The setting is saved if you quit XBMC that way, so next time you restart it, it will be in fullscreen. If I remember the shortcut is "\". Check on XBMC wiki.

BR
Leodp

---

