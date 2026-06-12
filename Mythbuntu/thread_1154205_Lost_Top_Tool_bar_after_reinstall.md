---
title: "Lost Top Tool bar after reinstall"
date: 2009-05-09
forum: Mythbuntu
---

### Post by phroman on 2009-05-09
Hi, I had to re-install Mythbuntu 9.04 today.  When I got to the desktop, there is no toolbar at the top.  I'm talking the first desktop screen you ever get to with a fresh install.  I tried to adjust my monitor, thought maybe it was not centered or something, but that didn't work.  It seems the toolbar is just gone.  I can access everything that would normally be there by right clicking on the desktop, but I won't have a clock or network icon like I did in the upper right corner.  I ran all the updates, rebooted, no toolbar, any ideas?  Thanks  :)

---

### Post by pastalavista on 2009-05-09
Right-click the panel (toolbar) you still have and click 'new panel'. Then right click the panel, select 'preferrences' and change the orientaion to 'top'. Then right-click it again and select 'add to panel'. You'll see a list of applets. Select 'menu toolbar', 'notification area', 'clock' and 'user switcher' to make it like the default panel. Or you can customize it however you like.

---

### Post by phroman on 2009-05-09
Hi, I don't have any toolbar at all on my desktop right now.  I can't find any settings/controls for one either.

---

### Post by pastalavista on 2009-05-09
Ah, ok. I didn't realize mythbuntu only had the one panel. You could try running in terminal ```
sudo apt-get install mythbuntu-desktop
```. I just looked and I believe mythbuntu is built on xfce insted of gnome. Sorry, my bad

---

### Post by phroman on 2009-05-09
Well, I fixed it but I didn't really solve it...  I think something is screwey with my video card/monitor.  I put the Mythbuntu install cd in, got to the live cd desktop, half the top toolbar was up above the visible screen.  I fiddled around with the monitor  and got the desktop centerd properly so I could see the top toolbar.  Installed from within the live desktop environment, and everything is fine.  :confused:   Anyway, thanks for the help.  :)


how do I mark this to show up as [SOLVED] on the main page?

---

### Post by nickmayfield on 2009-05-20
i'm having the same problem. there is no toolbar at all after a fresh install. i've been trying to figure it out and have no luck. i installed the ubuntu desktop from the mythbuntu control panel and still no luck. any ideas
thanks

---

### Post by SiHa on 2009-05-20
If you're viewing on a TV, it's probably the overscan. In other words, the menu bar is there, but the TV is displaying it off the top of the screen.

If you go into the setup screens, are 'OK' 'Next' 'Cancel' buttons nearly off the screen? If so, it's definitely the overscan.

If you have **nvidia-settings** installed, there's an overscan slider where you can reduce this so that the display fits on the visible part of the screen. If you have a newish TV, you may be able to turn off overscan in one of the setup menus.

Both of the above will enable you to see the whole desktop, and everything full-screened will fit.

Failing the above, you can go into Setup -> TV Settings -> Screen Size Wizard (or something like that). There you can move a couple of markers to the corners of the visible screen. This will resize the Mythtv output, but nothing else.
**Note** after adjusting the screen size with the wizard, the frontend will exit and restart - this is normal.

---

### Post by nickmayfield on 2009-05-20
its not an overscan problem. i'm using a 19" lcd/monitor. my mouse cursor doesn't even go off the screen. i just have no toolbar at all. i want to put it back. it hasn't even been hooked up to a tv yet cause i haven't finished setting it up. please help. off to work now. my the end of the day i'll be throwing the disk in again and restarting again

---

### Post by carrucha on 2009-06-06
Any resolution to this?  I have the same issue on the hdtv AND the monitor I have hooked up as well.  Seems like I just need to turn on some toolbar somewhere.  Makes life difficult since I can't get to my wireless network to make it work.

---

### Post by silverdulcet on 2009-06-07
> **nickmayfield said:**
> its not an overscan problem. i'm using a 19" lcd/monitor. my mouse cursor doesn't even go off the screen. i just have no toolbar at all. i want to put it back. it hasn't even been hooked up to a tv yet cause i haven't finished setting it up. please help. off to work now. my the end of the day i'll be throwing the disk in again and restarting again

1. Try the keyboard shortcut to the Applications menu, Ctrl-Esc. To see if the panel really is just off the screen.

2. The name of the panel applet is xfce4-panel, unless you've loaded the gnome desktop, then it would be gnome-panel. I have had experiences with the desktop version of Ubuntu where the gnome-panel disappears because it freezes/crashes and when I kill the panel it reloads itself automatically. The first step is to check to see if xfce4-panel (gnome-panel if using gnome instead) is running. From a terminal window.

```
ps -A | grep xfce4-panel
```

It should return something similar to this, if its running.

```
mythuser@mythbox:~$ ps -A | grep xfce4-panel
 6594 ?        00:00:01 xfce4-panel
mythuser@mythbox:~$ 

```

Then try killing it to see if it restarts, remember the process id number will be different when you run the above command.
```
kill -s 1 6594
```

If it doesn't load up then or you find its not running at all, you can try starting it from the terminal.
```
xfce4-panel
```

As far as fixing it so that it loads on its own as it should, I'm not sure, a work around might be adding it to the Autostarted Applications/Session Management. Anyway, just thought I'd post how to see if its running and how to restart it manually to see if you can get it to run.

---

