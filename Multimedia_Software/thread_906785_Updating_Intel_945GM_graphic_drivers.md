---
title: "Updating Intel 945GM graphic drivers"
date: 2008-08-31
forum: Multimedia Software
---

### Post by Dovir on 2008-08-31
I searched everywhere to try to figure this out and my question is like the title says: How do I update my Intel 945GM graphic drivers? I am running Kubuntu 7.10 (gutsy). I tried to install the drivers on: [http://www.intellinuxgraphics.org/](http://www.intellinuxgraphics.org/) but the method to install wasn't working. 


Any help will be appreciated greatly. :)

---

### Post by pytheas22 on 2008-09-01
Why are you trying to upgrade them?  In general the driver that you have on 7.10 should be pretty similar to the one in Hardy.

There are two different versions of the Intel graphics drivers--i810 and intel--and I think (but could be wrong) that 7.10 uses i810 by default.  Performance should be pretty similar on both of them for most Intel graphics cards, although intel is the newer driver.  If you're looking to switch between the two drivers for some reason, however, you can do so using Synaptic (uninstall the i810 package and install the intel one in its place).

If you want to switch to the Hardy version of the driver for some reason, you could probably also do that using Synaptic (by enabling the Hardy repositories), but first please let us know why you want to do this, so that you're not doing something that will give you unexpected results.

EDIT: by the way I see that you're using Kubuntu, so by 'Synaptic,' I mean 'KPackage' or whatever the KDE equivalent is these days.

---

### Post by Dovir on 2008-09-01
The reason why I want to update the drivers is because games appear to be sluggish and I'm assuming it's because of the intel drivers. Although that probably may not be the case, but atleast I'm asking first before I do it.

---

### Post by pytheas22 on 2008-09-01
In that case, you may want to first try switching from the i810 driver to intel (or vice versa, depending on what you're using now).  Open up your package manager and search for 'i810.'  If it's installed, uninstall it and install 'intel' in its place (make sure that you keep at least one of the drivers installed; otherwise X will not start again after you log out).  Then log out and see if the speed performance seems better.

If not, you can try grabbing the Hardy build of the Intel driver.  I don't think that you'll see any remarkable speed increases, but if you want instructions on how to enable the Hardy repositories so that you can use that driver, let me know.

Keep in mind that Intel graphics chips in general are not designed to support heavy-duty gaming.  I have an integrated 945GM card as well and it runs desktop effects fine and can handle most 3D games pretty well if I turn the video settings down, but really intense games don't work well.

Also keep in mind that if the games you're using are running in wine, the problem could lie with wine, not the graphics driver (you can check the [wine database]("http://appdb.winehq.org/") to see if others have experienced performance problems with the same games).  You probably shouldn't assume it's the Intel driver unless you've tried at least two or three native Linux games with the same poor results.

---

### Post by Dovir on 2008-09-01
Yup that fixed it, turns out BOTH of the drivers were installed. So I just uninstalled the i810 and it's not sluggish anymore. Thanks so much. :D

---

