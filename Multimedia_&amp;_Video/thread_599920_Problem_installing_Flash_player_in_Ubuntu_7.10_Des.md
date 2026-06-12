---
title: "Problem installing Flash player in Ubuntu 7.10 Desktop"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by Wonka on 2007-11-01
I have tried to install the Flash player, but without success.

First I went to a website that uses Flash. Firefox asks to install a missing plugin. I can then choose from the Adobe Flash Player or the Gnash Player. None of them can be installed as I get an error message like "can not find flashplugin-nonfree".

I have tried to reload the synaptic package manager and try install it again, but no success.
[http://ubuntuforums.org/showthread.php?t=596351](http://ubuntuforums.org/showthread.php?t=596351)

I have tried it with the synaptic package manager, but it could find flashplayer-nonfree.

I also tried to install it within the terminal with the command ```
sudo apt-get install flashplayer-nonfree.
``` I get the message "Couldn't find package flashplugin-nonfree".
[http://ubuntuforums.org/showthread.php?t=462624](http://ubuntuforums.org/showthread.php?t=462624)

I hope somebody can help me.

---

### Post by Yellow Pasque on 2007-11-01
I'm not sure why that's happening to you, but you could just download the player from adobe's site.
[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)

---

### Post by DWells55 on 2007-11-01
I'm having the exact same problem.  I try to download the plugin using Firefox and I receive an error telling me [package name] not found.  This is a fresh install on a laptop dual booted with Windows XP.

---

### Post by rsambuca on 2007-11-01
Make sure you have all of your package repositories activated.  Go to your top menu panel and select "System -> Administration -> Software Sources".  On the first "Ubuntu software" tab, make sure that all of the repositories are checked (main, universe, restricted, and multiverse). 
Close the window, and select "Reload" when prompted.

You should then be able to install the flash plugin using Synaptic Package Manager, or via the command line.

---

### Post by DWells55 on 2007-11-01
After doing the steps you listed, Firefox was able to retrieve and install the package for Flash player and it appears to be functioning properly.  Thanks a bunch.

Is it normal to have to do this, or did something go wrong during my install?  The install was hanging at 82% (scanning mirrors) for a pretty long time, so I had to pull the ethernet cable out to get the installation to continue.  Think that had anything to do with it?

---

### Post by rsambuca on 2007-11-02
> **DWells55 said:**
> After doing the steps you listed, Firefox was able to retrieve and install the package for Flash player and it appears to be functioning properly.  Thanks a bunch.

Is it normal to have to do this, or did something go wrong during my install?  The install was hanging at 82% (scanning mirrors) for a pretty long time, so I had to pull the ethernet cable out to get the installation to continue.  Think that had anything to do with it?

I'm not sure if that is normal or not.  Out of habit, I just activate all of the repositories as soon as I install or upgrade.

---

