---
title: "XBMC Install Question"
date: 2009-07-17
forum: Multimedia Software
---

### Post by BryanA on 2009-07-17
Hey there. I'm having trouble installing XBMC on Ubuntu 9.04.

Here is the source list output:
[http://pastebin.ubuntu.com/220265/](http://pastebin.ubuntu.com/220265/)

Here is the output of an update:
[http://pastebin.ubuntu.com/220267/](http://pastebin.ubuntu.com/220267/)

Here is the output for a search:
 
 ```
mediaserver@MediaServer:~$ sudo apt-cache search xbmc
texlive-latex-extra - TeX Live: LaTeX supplementary packages 
```Any help is much appreciated. 

Thanks

---

### Post by ohzopants on 2009-07-20
Did you do a
```

sudo apt-get update

```

to update the cache?  Did you fetch all the proper keys for the repos?

---

### Post by zetanuxi on 2009-07-21
You have to add the XBMC development site to the list of sources.

Here's the tutorial: [http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step](http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step)

When adding the source and the PPA key, you'll probably get an error about no autentication. Ignore it. Those were popping up for me and XBMC works like a charm. :)

---

### Post by mr_cardholder on 2009-07-27
> **zetanuxi said:**
> You have to add the XBMC development site to the list of sources.

Here's the tutorial: [http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step](http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step)

When adding the source and the PPA key, you'll probably get an error about no autentication. Ignore it. Those were popping up for me and XBMC works like a charm. :)

I followed that tutorial but when I reloaded synaptic package manager, I couldn't find xbmc listed. Any advice?

Thanks

---

### Post by mr_cardholder on 2009-07-27
> **mr_cardholder said:**
> I followed that tutorial but when I reloaded synaptic package manager, I couldn't find xbmc listed. Any advice?

Thanks

Actually just figured it out. For some reason the source was commented out in the sources.list file. Have no idea how that happened but that fixed it.

---

