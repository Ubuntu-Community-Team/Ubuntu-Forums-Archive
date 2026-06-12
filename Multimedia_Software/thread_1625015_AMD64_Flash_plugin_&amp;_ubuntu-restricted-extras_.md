---
title: "AMD64 Flash plugin &amp; ubuntu-restricted-extras conflict?"
date: 2010-11-18
forum: Multimedia Software
---

### Post by santosh83 on 2010-11-18
Hi all,

Having installed 10.10 one of the first things I did was to follow the directions given in 
[http://ubuntuforums.org/showpost.php?p=8522076&postcount=1](http://ubuntuforums.org/showpost.php?p=8522076&postcount=1)
post to install Abode Labs's 64-bit Flash plugin.

Now my question is if I can safely install the 'ubuntu-restricted-extras' package without conflicitng with this plugin. My understanding from the above post is that only one of either 64-bit or 32-bit Flash plugin can be used at any one time and parallely installing both seems to cause problems. But the 'ubuntu-restricted-extras' package will cause 'flashplugin-installer' to be installed too right? Which then downloads the 32-bit Flash plugin and nswrapper.

So my question is if there is a way to install 'ubuntu-restricted-extras' and have it NOT conflict with my 64-bit Flash plugin? Any symlink trickery can help?

I can see two ways: 1.) Install 'ubuntu-restricted-extras', uninstall/delete whatever flashplugin-installer installed, then reinstall 64-bit plugin following the mentioned thread. 2.) NOT install 'ubuntu-restricted-extras' at all, but instead each package it depends on individually (finding out the dependencies through Synaptic) and simply omit the flashplugin-installer package.

Can anyone suggest another perhaps better way, or any caveats I should know if I follow 2.) above?

Thanks all.

---

### Post by efflandt on 2010-11-19
I used method 1.  Note that when uninstall flashplugin-installer, the nswrapper related things are still there (but not really in the way).  You can get rid of that with **sudo apt-get autoremove** (which removes things previously added as dependencies when nothing depends on them any more).

---

### Post by santosh83 on 2010-11-19
> **efflandt said:**
> I used method 1.  Note that when uninstall flashplugin-installer, the nswrapper related things are still there (but not really in the way).  You can get rid of that with **sudo apt-get autoremove** (which removes things previously added as dependencies when nothing depends on them any more).

Thanks efflandt! I think I'll go with this method too.

---

