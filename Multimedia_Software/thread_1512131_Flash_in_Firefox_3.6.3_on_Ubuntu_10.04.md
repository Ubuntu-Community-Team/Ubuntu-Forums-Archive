---
title: "Flash in Firefox 3.6.3 on Ubuntu 10.04"
date: 2010-06-17
forum: Multimedia Software
---

### Post by Ctulhu on 2010-06-17
Another post regarding the Firefox/Flash issue on Ubuntu 10.04 ... My main question is that I don't understand why Flash in Firefox (Huffington Post videos of The Daily Show) works differently on two computers that are identically configured (but cf. below):

- both have Firefox 3.6.3;
- within Firefox about:plugins, all plugins with "flash" are the same;
- within Synaptic, all things that have "mozilla", "flash", "adobe" are identically installed on both (that includes Adobe Flash plugin Version 10.1.53.64ubuntu0.10.04.1)

The only difference is that the computer where it works is a 64bit system, the one where it doesn't work is a 32bit system. Can this be true, that this is the thing that makes this huge difference? Any fixes around for that (other than FlashAID)?

---

### Post by lovinglinux on 2010-06-19
Looks like you have multiple plugins installed, which is not good.

What happened when you tried FLASH-AID?

I need more information about both computers:

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by Ctulhu on 2010-06-20
I didn't try FlashAid, but here's the info you asked for, maybe it helps.

    File: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

---

### Post by lovinglinux on 2010-06-21
> **Ctulhu said:**
> I didn't try FlashAid, but here's the info you asked for, maybe it helps.

    File: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

Then try FLASH-AID.

Also could you be more descriptive about the problem? The video doesn't work at all or there is another issue?

---

### Post by Ctulhu on 2010-06-22
The thing that doesn't work is that in place of the flash movie there is what is in the attached screenshot, and when I click OK nothing ever happens ...

---

### Post by lovinglinux on 2010-06-22
> **Ctulhu said:**
> The thing that doesn't work is that in place of the flash movie there is what is in the attached screenshot, and when I click OK nothing ever happens ...

FLASH-AID should fix that.

---

### Post by cjmiller00 on 2010-06-22
> **Ctulhu said:**
> Another post regarding the Firefox/Flash issue on Ubuntu 10.04 ... My main question is that I don't understand why Flash in Firefox (Huffington Post videos of The Daily Show) works differently on two computers that are identically configured (but cf. below):

- both have Firefox 3.6.3;
- within Firefox about:plugins, all plugins with "flash" are the same;
- within Synaptic, all things that have "mozilla", "flash", "adobe" are identically installed on both (that includes Adobe Flash plugin Version 10.1.53.64ubuntu0.10.04.1)

The only difference is that the computer where it works is a 64bit system, the one where it doesn't work is a 32bit system. Can this be true, that this is the thing that makes this huge difference? Any fixes around for that (other than FlashAID)?


i didnt think that ubuntu was able to respond to bad media.  ever think that was the prob.  

seriously i had similar issue till i uninstalled all plugins then got a bunch of java from REPO, and single pluggins for flash and java respectively for browser

---

