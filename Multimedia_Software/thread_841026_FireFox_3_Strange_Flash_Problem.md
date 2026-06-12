---
title: "FireFox 3 Strange Flash Problem"
date: 2008-06-26
forum: Multimedia Software
---

### Post by FGazerro on 2008-06-26
Hey guys, 

I'm running Ubuntu 8.04

I recently upgraded to firefox 3. Now any site with flash content first appears as a solid gray box with a huge play button. I have to click the play button to make the flash content appear (even if its just a nav bar). Then sometimes the content works, sometimes it doesn't. Any ideas?  

I've tried uninstalling and installing libflash and flashplugin-nonfree in Synaptic and a direct download from Adobe. Nothing seems to fix it. 

What do you think?

---

### Post by gandaran on 2008-06-26
you have swfdec flash installed, just remove it so adobe flash can take over, and don't install libflash or anything else to do with flash, just adobe flash.
if you happen to have any firefox flash sound problems with adobe flash 9, don't install libflashsupport, just remove all flash installed flashplugin-nonfree or the adobe tarball you installed, and install adobe flash 10 beta.

---

### Post by peter_babeone on 2008-06-26
> **gandaran said:**
> you have swfdec flash installed, just remove it so adobe flash can take over, and don't install libflash or anything else to do with flash, just adobe flash.
if you happen to have any firefox flash sound problems with adobe flash 9, don't install libflashsupport, just remove all flash installed flashplugin-nonfree or the adobe tarball you installed, and install adobe flash 10 beta.

I have the same problem and when I installed adobe flash 10 beta, I could use libflashsupport again with adobe flash. There was a problem between adobe flash 9 and libflashsupport before. So my firefox3 often crashed. But now it doesn't crash anymore with adobe flash 10 beta.

But now my FF3 is back to FF3.05b and I can't use some new plugins.

Is there any way to make libflashsupport and adobe flash 9 working together? 

Thanks lots

Peter

---

### Post by gandaran on 2008-06-26
> **peter_babeone said:**
> I have the same problem and when I installed adobe flash 10 beta, I could use libflashsupport again with adobe flash. There was a problem between adobe flash 9 and libflashsupport before. So my firefox3 often crashed. But now it doesn't crash anymore with adobe flash 10 beta.

But now my FF3 is back to FF3.05b and I can't use some new plugins.

Is there any way to make libflashsupport and adobe flash 9 working together? 

Thanks lots

Peter

libflashsupport does fixes the flash sound issue for some firefox user's but not all, and with a drawback, firefox crashes, flash 10 is the solution for everyone that have a firefox sound problem with flash 9, and no need to install libflashsupport.
FF3 or FF3.05b use the same plugins but maybe in different plugins folders, just check where those plugins are installed, if you can install flash 10 in /usr/lib/mozilla/plugins folder then this plugin can be used by every browser installed, including opera.

---

### Post by FGazerro on 2008-06-26
> **gandaran said:**
> you have swfdec flash installed, just remove it so adobe flash can take over, and don't install libflash or anything else to do with flash, just adobe flash.
if you happen to have any firefox flash sound problems with adobe flash 9, don't install libflashsupport, just remove all flash installed flashplugin-nonfree or the adobe tarball you installed, and install adobe flash 10 beta.


Worked like a charm. I uninstalled swfdec, installed flash 9, and everything works great. Thank you.

Frank

---

