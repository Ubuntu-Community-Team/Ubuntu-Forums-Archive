---
title: "Mobility Radeon 9100IGP not work with any linux distro"
date: 2006-08-01
forum: Multimedia &amp; Video
---

### Post by jadm55 on 2006-08-01
Hi from Mexico

I enter the world of linux with a laptop HP Pavilion ZV5007LA and is great, except for the fact than after 3 distros installed (Suse 10.1, fedora core 5 and now Ubuntu Dapper) the 3D card isnt work, the guides in ubuntu forums ([http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)) are very clear but the results after follow all the steps without errors on screen is no 3D. The only reason i found is the drivers from ATI not support my video card. This is curious because a year ago I bought this middle/use lap and with SUSE 10 the 3D works very well with games and all.
anyone have a clue about this?

Thanks for your comments

PD: Sorry for my not practiced english

---

### Post by mpvano on 2006-08-02
It's confusing and true, and very annoying that both ATI and Ubuntu documentation do NOT make clear which cards work and which don't.

In fact the drivers simply DO NOT WORK with many (perhaps most?) popular  notebook  computers, but instead of honestly admitting this fact, ATI seems to be trying to hide the problem behind page long error messages listing the cards they support in a form that cannot be translated into actual hardware!

I've personally wasted days on this subject only to discover that there's no general way to describe your card's hardware. It seems that the model number reported by lspci does NOT guarantee the ATI driver will work because the real hardware is described by mysterious undocumented names that are never referred to by vendors.

It would be GREAT if someone at ATI would either provide an accurate (not forum rumors) description of how to tell if your card will work before you spend days trying to manually recompile broken drivers and add them to your system in ways you cannot easily undo.

Hey ATI (or Canonical) How about shipping a utility that UNAMBIGUOUSLY tests the proprietary secrets of your card's version info and just displays it in a manner compatible with the driver's version download info so we can tell if it is worth trying or not before we trash our systems?

One person's opinion....

Mario

---

### Post by jadm55 on 2006-08-02
Thanks for answer, its true, my search for a effective method for install this particular ATI is frustrating. But, as i say, I'm do not how this guy, (the first owner of the lap) install sucessfully the 3D in SUSE 10, in SUSE 10.1 i dont discover how, the truth is if I bught this lap for a free software installation, i think I made a wrong buy. is not the only than dont work, the card reader and the wifi are the same. Probably i need of more expertise.

Thanks again

---

