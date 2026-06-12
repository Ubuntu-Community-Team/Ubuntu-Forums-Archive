---
title: "Firefox Flash Performance Fixed (How I did it)"
date: 2011-01-01
forum: Multimedia Software
---

### Post by JosephPaul on 2011-01-01
Hello all!

I posted a few weeks ago about Flash performance in Firefox vs. Google Chrome.  Thanks to all those who responded.  I finally figured out the problem in Firefox, it was Compiz desktop effects.  With effects off, flash in Firefox is just as fast as Google Chrome.  I am not sure why Compiz only affects Firefox Flash, but apparently Chrome is not affected.  I know there are a lot of posts about this topic, so before driving yourself nuts installing FlashAid, and running terminal commands, try disabling desktop effects first.

Take care!

Joseph

---

### Post by lovinglinux on 2011-01-02
Compiz does not play well with flash. That is a known issue.

BTW, I just released version 2.0 of Flash-Aid, with tons of improvements, including performance tweaks, beta updates, plugin automatic detection and more.

[http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid)

---

### Post by JosephPaul on 2011-01-03
> **lovinglinux said:**
> Compiz does not play well with flash. That is a known issue.

BTW, I just released version 2.0 of Flash-Aid, with tons of improvements, including performance tweaks, beta updates, plugin automatic detection and more.

[http://www.webgapps.org/addons/flash-aid](http://www.webgapps.org/addons/flash-aid)
Hello,

Thanks for posting about the update to Flash-Aid.  No trashing of Flash-Aid was intended in my post as I still use it for FF.  I did not know this was a known issue.  All the google results and Forum posts directed me to either Flash-Aid, editing Flash config. files, or claimed it was a kernel issue.  I will check my Firefox plug-ins for updates asap.

---

### Post by lovinglinux on 2011-01-03
> **JosephPaul said:**
> Hello,

Thanks for posting about the update to Flash-Aid.  No trashing of Flash-Aid was intended in my post as I still use it for FF.  I did not know this was a known issue.  All the google results and Forum posts directed me to either Flash-Aid, editing Flash config. files, or claimed it was a kernel issue.  I will check my Firefox plug-ins for updates asap.

BTW, the reason for the difference between Firefox and Chrome, is that Chrome has an "optimized" flash plugin bundled with it. That doesn't mean it is always better. There are users that experience issues with Chrome plugin and not with Firefox. Depends on Chrome updates and which plugin you are using with Firefox. If you want to turn the Chrome plugin off and use the same flash version as Firefox (installed with Flash-Aid for example), then type **about[noparse]:[/noparse]plugins** in Chrome address bar, then click the "Details" on the top right, then scroll to *Shockwave Flash* section and disable the one that has **/opt/google/chrome/libgcflashplayer.so** as *Location*.

---

