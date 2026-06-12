---
title: "[Gdk-CRITICAL] Hulu Desktop Not Loading (errors included)"
date: 2011-12-09
forum: Multimedia Software
---

### Post by Rikeshar on 2011-12-09
Hey everyone, when I try to launch Hulu Desktop I'm getting the follow errors:


```
(huludesktop:2368): Gdk-WARNING **: gdk_window_new(): parent is destroyed


(huludesktop:2368): Gdk-CRITICAL **: IA__gdk_window_get_display: assertion `GDK_IS_WINDOW (window)' failed

(huludesktop:2368): Gdk-CRITICAL **: IA__gdk_x11_get_xatom_by_name_for_display: assertion `GDK_IS_DISPLAY (display)' failed

(huludesktop:2368): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.6/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window

(huludesktop:2368): Gdk-CRITICAL **: IA__gdk_x11_display_get_xdisplay: assertion `GDK_IS_DISPLAY (display)' failed
Segmentation fault
```

Would anyone out there happen to know what this could be?

---

### Post by jerrrys on 2011-12-11
I don't use it, but got some hits here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Hulu+Desktop+Gdk&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Hulu+Desktop+Gdk&sa=Search&cof=FORID:9)

---

### Post by Rikeshar on 2011-12-11
Thanks for the reply. I've been doing some research too and I don't think it's an issue with the application so much as GDK. I had this application installed before and it would run. I recently removed it and reinstalled it, because when it started locking up the computer when it was ran, and after reinstalling this is what I see.

---

### Post by jerrrys on 2011-12-11
I don't see Hulu in the repositories, how did you download it?

---

### Post by Rikeshar on 2011-12-11
It's downloaded from their website. They provide a .deb.

[http://www.hulu.com/labs/hulu-desktop-linux](http://www.hulu.com/labs/hulu-desktop-linux)

I did choose the 32bit version, which is what my system is.

---

### Post by jerrrys on 2011-12-11
It says that Hulu DT is designed for 9.04.  So even thou you had it running, it will probably always be buggy in 11.10.

---

### Post by Rikeshar on 2011-12-11
It's designed for 9.04 and up. I'm concerned that it won't run because of these GDK errors though, before it would at least load up. I dont' think it's something to do with the application, but GDK.

---

### Post by jerrrys on 2011-12-11
They also ask for 

[LIST]
[*]GTK+ 2.12 or higher
[*]GLib 2.16 or higher
[/LIST]
I can't see this flying, but tell you what.  Its too late tonight, but I will load this and if it flies I will attempt to recreate your problem.  goodnight

---

### Post by Rikeshar on 2011-12-11
Thank you, I appreciate your help! I'll look into those two things too, maybe I accidentally removed them through auto-remove.

---

### Post by jerrrys on 2011-12-11
I couldn't get it to load in 11.10, but it would install in 10o4 and seems to be working.

[ATTACH]208912[/ATTACH]

This doesn't verify anything though.  Im running a pretty bare copy of 11.10 and it could be Im missing a required package.

Reloading it in 10o4 has no effect.

I have one last suggestion.  Manually remove all packages and reinstall.

[ATTACH]208913[/ATTACH]

Goodluck

---

### Post by Rikeshar on 2011-12-12
Did you get the same errors as I did when you tried to run it in 11.10? 

Maybe I will have to manually remove all the files, if I can find them!

---

### Post by Rikeshar on 2011-12-12
Well, I removed them, reinstalled... same thing. *sigh*

---

### Post by jerrrys on 2011-12-12
New idea:

Create a new account (new user) and install hulu there.  Will it work?

---

### Post by Rikeshar on 2011-12-12
Well, I'm at a loss now. I tried installing it on a clean install of Mint 12, and I'm getting the exact same errors.

---

### Post by jdk82 on 2011-12-18
Hi Rikeshar,

What version of flash player are you using and how did you install it? The about:plugins page in Firefox shows Shockwave Flash 11.2 d202 which I just installed using the Flash-Aid plugin for Firefox. I'm going to try another install and see if it helps.

Josh

---

### Post by Rikeshar on 2011-12-21
Hey jdk82, sorry it took me so long to respond. I've actually found out what was causing the errors. Using flash-aid for firefox I installed the beta version of flash, and this caused hulu desktop to give out those GDK errors. I tried using the plugin to install the stable version and now it's doing the same thing it was which caused me to start messing with it (and thus get the GDK errors in the first place), it's freezing up my computer when navigating the screen. 

Did you get it to work?

UPDATE: The version that causes Hulu Desktop to freeze (on startup of the program now) is: Shockwave Flash 11.1 r102

The version that causes the GDK errors: Shockwave Flash 11.2 d202

I'm not sure what version was on there when I freshly installed Ubuntu 11.10, but it would allow Hulu Desktop to run, but would cause the video to be choppy when in full screen. On previous version of Ubuntu, running the Flash Aid plugin would install a new version of flash that fixed that issue. Not so anymore :(


UPDATE 2: I removed the libflashplayer.so from /usr/lib/mozilla/plugins (where the 11.2 d202 flash gets installed) and I removed it from /usr/lib/flash-installer (i think that's what it was [where the 11.1 r102 version gets installed]) 

I then installed the "Adobe Flash 10" plugin from the Ubuntu Software Center, and it installed to /usr/lib/adobe-flashplugin   When using this one, Hulu Desktop will run, but the video is back to choppy again. Any ideas?

---

