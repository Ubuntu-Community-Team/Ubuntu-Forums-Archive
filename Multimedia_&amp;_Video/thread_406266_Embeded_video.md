---
title: "Embeded video"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by Word on 2007-04-10
How/what can i use something other than totem to view embeded videos in firefox. Totem either does not work or the controls dont work.  I remeber in 5.04 i had mplayer or xine play based on video. It worked and worked well.

Thanks for your help.

---

### Post by zenwhen on 2007-04-10
Use Automatix from [http://getautomatix.com](http://getautomatix.com) to install "Mplayer and Firefox Plugin". That should work fine.

---

### Post by Word on 2007-04-10
does that still work if my mplayer does not play videos. I get an error

Error opening/initializing the seclected video_out (-vo)

---

### Post by RomeReactor on 2007-04-10
Hi. Right-click on Mplayer, select "Preferences", and on the "Video" tab choose the **xv   X11/Xv** driver. Close Mplayer and open it again, and see if the error is gone.

---

### Post by Word on 2007-04-11
thanks RomeReactor that worked but I still dont know how to change totem from embeded player in firefox. I install the automatix plugin no luck

---

### Post by r4ik on 2007-04-11
Try remove the totem-mozilla plugin.

---

### Post by Word on 2007-04-11
you cant remove it because it say's its going to remove ubuntu-desktop

---

### Post by RomeReactor on 2007-04-11
Synaptic says this about ubuntu-desktop:

> This package depends on all of the packages in the Ubuntu desktop system
It is also used to help ensure proper upgrades, so it is recommended that it not be removed.

I always uninstall the totem plugin in favor of the mplayer plugin right after I do a clean install, and it does take ubuntu-desktop with it, but I haven't noticed anything wrong: Updates work just fine, no programs crash. So I suggest you go ahead and remove the totem plugin to install the one from mplayer.

---

