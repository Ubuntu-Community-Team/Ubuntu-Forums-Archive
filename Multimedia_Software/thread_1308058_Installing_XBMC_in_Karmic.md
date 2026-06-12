---
title: "Installing XBMC in Karmic"
date: 2009-10-31
forum: Multimedia Software
---

### Post by pstefanini on 2009-10-31
I just installed 9.10 Karmic and wanted XBMC first thing.  I probably went through the install instructions too quickly.  XBMC isn't fully recognized in synaptic and I'm getting an update error message when I refresh the repositories:

*W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY <I left the key # out here>*
  
Does anyone know what this means?  Thank you!

---

### Post by doppis on 2009-11-01
Well...you need to add the ppa key to get rid of that error but I don't think the standalone in synaptic is going to pop up after you fix that...it's not showing up for me either for some reason.

Here is the link to help you fix that error.

[http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide](http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide)

---

### Post by doppis on 2009-11-01
Actually I just got it to show up.  Go into system> administration> software sources and remove your original ppa for xbmc. Refresh the list and then add this

deb [http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu) karmic main

make sure you refresh your synaptic after

---

### Post by pstefanini on 2009-11-01
Thank you... I'm close but hesitating... I have the two XBMC files showing up in my Synaptic Package Manager but when I tick them off, a number of dependencies show up... I'm hesitating...

Is this because of the repository and the files are Jaunty and trying to do this in Karmic?  Would I be better off to wait until Karmic download is available? 

Any thoughts or has anyone tried XBMC in Karmic using the Jaunty files?

---

### Post by doppis on 2009-11-01
check my second post

---

### Post by pstefanini on 2009-11-01
Ok Doppis... I followed your second post and it's downloading ... I'll let you know!!!  Thank you!

---

### Post by pstefanini on 2009-11-01
Doppis:  It worked like a charm... Case closed!  I'm listening to the blues right now!!!

Thank you again!  Phil

---

### Post by doppis on 2009-11-01
great :)

---

### Post by rburkartjo on 2009-11-06
dop tks you also

---

