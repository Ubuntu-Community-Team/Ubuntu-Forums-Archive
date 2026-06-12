---
title: "Gnome wallpaper keeps popping up in KDE."
date: 2009-04-05
forum: Multimedia Software
---

### Post by shayguitarra on 2009-04-05
OK, I've done a few searches for this particular problem over the past few weeks and nothing turns up, I think because my search terms are very general. I keep finding myself at threads instructing how to install the kubuntu desktop.

This problem is not really effecting functionality but it is starting to get a little irritating.

So here it is. I originally installed Ubuntu in September 2008 and switched to the kubuntu desktop in January of this year. Currently I'm on kubuntu 8.10 with kde4. I am running a 256mb ati video card which doesn't seem to have a model number but it uses the FGLRX proprietary driver.

Occasionally, when I am doing certain video or image based things my old Gnome wallpaper pops up.
Examples: Before vlc goes into fullscreen I get a two or three second flash of my Gnome wallpaper.
In other programs (eg gmusicbrowser) when I place the cursor over the ratings stars in fullscreen the gnome wallpaper flickers on and off for a few seconds. (I know that very few people use gmusicbrowser and even less with the custom layout I use but I hope the general behaviour will sound familiar.)

Also, when I play a video file in vlc it jumps to fullscreen and out again two or three times with the sound playing before I see any video. This lasts about five seconds.

Aside from this I have no problems.

Is there any tinkering I can do to solve this? Otherwise I'll wait for the full release of Jaunty and hope it magically fixes itself. :)

---

### Post by mickie.kext on 2009-09-24
I have exact same problem. Duno how to fix it, exept to set same wallpaper both in GNOME and KDE. That solves the anoyance, but GNOME is still runing in the background of KDE... I gues that some programs need parts of GNOME running in background.

---

### Post by dyrvere on 2010-10-19
I'm not sure bumping this thread is necessary, on the other hand it was one of the first results I found while searching, but the solution sure is nice to have. :)
If this ever happens to you, simply run this command either terminal/konsole or alt+F2 and type in / copy n paste..

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false

and:

gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true

before switching back into gnome :) you could also make this a script or desktop shortcuts.. any way you please.

---

### Post by FerroPower on 2011-08-23
I know this is an OLD thread but I too had similar problem playing VLC player in kubuntu. 

I figured it out and want to share the solution with others please ignore if this solution was posted earlier. 

go to System Settings > Desktop Effects > Advanced and 

uncheck the option [COLOR=Blue]Suspend Desktop Effects for Fullscreen Windows[/COLOR] and click **[COLOR=Lime]apply[/COLOR]**.  Thats it your gnome wallpaper wont keep popping in your vlc player in Kubuntu

---

