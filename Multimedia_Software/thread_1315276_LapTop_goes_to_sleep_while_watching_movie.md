---
title: "LapTop goes to sleep while watching movie"
date: 2009-11-05
forum: Multimedia Software
---

### Post by Icusnik on 2009-11-05
Hi,  everyone 
after upgrade from 9.04 to 9.10 I've expecting some problems with movie watching:
Tested on : VLC, Mplaye, Totem, Gnome, Xing, Banshee...
While watching a movie for 10 minutes (in power management set sleep display after 10 minutes and suspend Laptop after 30 minutes of idle. )and my display go to sleep, but sound still going, after 30 minutes PC just suspending.
Already tried to reinstall all those programs after clean remove, check all settings they the same as was in 9.04, 
I cannot figure out is media programs not reporting to gnome-power-management that pc is not idle ? 
How to cure this? 
Will appreciate any help :)

---

### Post by Icusnik on 2009-11-05
> **Icusnik said:**
> Hi,  everyone 
after upgrade from 9.04 to 9.10 I've expecting some problems with movie watching:
Tested on : VLC, Mplaye, Totem, Gnome, Xing, Banshee...
While watching a movie for 10 minutes (in power management set sleep display after 10 minutes and suspend Laptop after 30 minutes of idle. )and my display go to sleep, but sound still going, after 30 minutes PC just suspending.
Already tried to reinstall all those programs after clean remove, check all settings they the same as was in 9.04, 
I cannot figure out is media programs not reporting to gnome-power-management that pc is not idle ? 
How to cure this? 
Will appreciate any help :)


need help couse its really annoying

---

### Post by Icusnik on 2009-11-06
Need help pls

---

### Post by megamania on 2009-11-06
I'm not at home now so I can't check, but if I remember correctly most programs have a "disable screensaver when playing" option... 

That could do the trick.

---

### Post by darshana on 2009-11-06
Goto System>Preferences>Screen Saver there put a tick on "activate screen saver when computer is idle".. try this

---

### Post by Icusnik on 2009-11-06
> **megamania said:**
> I'm not at home now so I can't check, but if I remember correctly most programs have a "disable screensaver when playing" option... 

That could do the trick.
  Unfortunately there is no option like this :(

---

### Post by Icusnik on 2009-11-06
> **darshana said:**
> Goto System>Preferences>Screen Saver there put a tick on "activate screen saver when computer is idle".. try this
ticket already, looks like movie players do not report to gnome-power-management that pc is not idle while playing :(

---

### Post by megamania on 2009-11-06
> **megamania said:**
> I'm not at home now so I can't check, but if I remember correctly most programs have a "disable screensaver when playing" option... 

That could do the trick.

> **Icusnik said:**
> Unfortunately there is no option like this :(
In VLC, Settings > Preferences > click "show all settings"
Video -> the 10th option is "Disable screen saver"

---

### Post by Icusnik on 2009-11-07
> **megamania said:**
> In VLC, Settings > Preferences > click "show all settings"
Video -> the 10th option is "Disable screen saver"

Yep its there :) and its checked (active)
but doesn't work :(

---

### Post by Pabster on 2009-11-07
Hi there,

I have experienced the same screensaver problem when watching videos on Karmic 64 with a clean build.

Apparently, this is a bug in gnome-screensaver.  Here's the page explaining it:

[https://bugs.launchpad.net/ubuntu/karmic/+source/vlc/+bug/428884](https://bugs.launchpad.net/ubuntu/karmic/+source/vlc/+bug/428884)

The workaround I WAS using is to just turn off the screensaver before watching a video from System->Preferences->Screensaver.  You just uncheck Activate screensaver when the computer is idle and set the Power Management to never put the display to sleep.  Then turn it back on after the movie.

That workaround was annoying and so I tried out a modified gnome-screensaver package from this PPA which was mentioned in the comments of the bug report:

[https://edge.launchpad.net/~motumedia/+archive/ppa]("https://edge.launchpad.net/%7Emotumedia/+archive/ppa")

I just downloaded the .deb for gnome-screensaver 64, force installed it from the command line and rebooted.

Once I installed that modified package, it completely solved the problem for me with VLC.  Now the screensaver stays off when watching a movie but still works when it is supposed to without having to toggle the settings.

I gather from some of the comments that this is not a perfect patch and I don't fully understand all the implications of using it, but I am satisfied with the end result, it is working for me.  The only other option I think we have is to wait for a proper fix from Ubuntu.

-Pabster

---

