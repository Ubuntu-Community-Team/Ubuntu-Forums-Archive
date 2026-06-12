---
title: "Desktop doesn't show up 11.04"
date: 2011-04-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by DylanRush on 2011-04-17
I just installed 11.04 to see how that is, and I changed a few settings in compiz.  I wanted the cube.  So did all that, and then everything just disappeared.  Just the wallpaper shows up now.  I've tried to just restart, log in and everything is fine.  It just loads up to my wallpaper though.  If I run in safe mode and with low graphics, that works just fine.  Any ideas on how to fix this or should I just reinstall?

---

### Post by The Woozy Fieldmouse on 2011-04-17
a) have you tried reinstalling your graphics driver?
b) have you tried reinstalling GNOME (assuming your using GNOME)?

Idk what card or driver you're using, but the command for reinstalling the desktop is:

sudo apt-get install --reinstall ubuntu-desktop

Here's a nice instructional page on using apt in general, if you would like to enrich your mind on the subject: [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

good luck!

---

### Post by Blasphemist on 2011-04-17
Hold on, hold on, hold on. You don't need to reinstall anything.

I did this to myself too. From the login screen, choose classic at the bottom of the screen. This will take you into a gnome desktop session. If you don't already have ccsm (CompizConfigSettingsCenter) installed, do so from the software center. In the desktop section, what is selected? My guess is that the unity plugin is not. I know it seems like you wouldn't want it to be while in classic but to get the unity back, this is where you'll have to add it back.

Regardless of how things now look in classic, logout or reboot and go back into the unity DE. If you have to do this a couple times, go into classic and make changes and then test unity, do so. You'll get unity back and when you do, remembering not to de-select the unity plugin, work with any other settings in ccsm that may need tweaked.

When all is good in unity, logout and go back to classic. Now you should be able to un-select unity in the classic DE (desktop environment) and generally make sure classic looks as you want.

I wasn't always sure logout and login did the same as reboot when I fixed mine so if I didn't get what I expected I restarted and started whatever I was doing right then again.

Let me know if questions come up.

---

### Post by DylanRush on 2011-04-17
I ended up making a launcher for the terminal because alt + F2 didn't work and I ran the gnome-panel from there and was able to gain access to the compiz settings.  I got it all working, it was just the unity plugin.  I can't really change any settings at all in there though or else everything just crashes.  Can't have the cube because that forces you to turn of the unity plugin. I tried to turn wobbly windows on, and then that messed things up and somehow managed to change the resolution of my screen and the monitor settings are now just unknown for my computer and I can't change them.  Is this really just that buggy or am I just having some horrible luck here?

---

### Post by howefield on 2011-04-17
Thread moved to "*Natty Narwhal Testing and Discussion*"

---

