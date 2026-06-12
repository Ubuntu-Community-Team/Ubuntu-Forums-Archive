---
title: "gxine 10.04 Lucid gnome desktop crash on load"
date: 2010-05-20
forum: Multimedia Software
---

### Post by skippuff54 on 2010-05-20
After upgrade to 10.04 Lucid Lynx :

gxine crashes the whole GNOME 2.30 desktop when it loads.

Occurs when I load it stand-alone or Firefox loads the plugin.

Previous searches for help have turned up threads and bugs on instances of gxine crash, but my entire desktop goes down.

No way to pull up a terminal or safely reboot either - forced to do a hard shutdown by holding the power key.

On a Toshiba Satellite with stock Intel 855 card.

Edit: The bug reported here describes basically what I experience: [https://bugs.launchpad.net/ubuntu/+source/gxine/+bug/416403]("https://bugs.launchpad.net/ubuntu/+source/gxine/+bug/416403")

Who has my answer today??? Who shares my frustration?

---

### Post by skippuff54 on 2010-05-21
[SIZE="6"]**Solution**[/SIZE]

Background: FAQs on the xine-project.org site made me inquire about the XShm (vs. Xv) video extension. Those references are at: [http://www.xine-project.org/faq#xfreecrash]("http://www.xine-project.org/faq#xfreecrash") and [http://www.xine-project.org/faq#xvextension]("http://www.xine-project.org/faq#xvextension")

Looks like a driver issue. Maybe the devs left the Xv extension out of 10.04 (or the latest Linux kernel)?

Followed the steps below (from the compiz.org wiki - [http://wiki.compiz.org/VideoPlayback]("http://wiki.compiz.org/VideoPlayback")) to change the driver in gxine: 

**[SIZE="5"]Note: [/SIZE]** [SIZE="4"]FIRST[/SIZE] - Start gxine from terminal, rather than launcher, and force it to start with XShm:


```
gxine -V XShm
```

[SIZE="4"]**NEXT:**[/SIZE]

```

1. Launch Xine [edit: you just did this with the above terminal command].

2. Go to File &#8211;> Configure &#8211;> Preferences.

3. For experience_level, select Master Of The Known Universe so that all the settings become visible.

4. Go to the Video tab.

5. For the driver, select xshm.

6. Restart Xine. 
```

According to the compiz wiki, this fix should work for any front-end GUI that uses the xine engine (e.g., kaffeine, totem).

Awesome, now I can watch Atlantis (STS-132) land next week!

---

### Post by wwwookie on 2010-09-15
Hi, Thanks for the guide, and the useful links to how you got to your solution - it always helps to know what's going on. I ran into the same problem with metacity crashing, and needing to use ALT-F2, metacity --replace - but the problem seems to be connected with gxine itself. When I tried xine-ui there was no difficulty in playing DVDs with the xv driver, which is faster, and (i think) uses the video card's memory rather than system RAM.
Incidentally when I selected the xv video driver in the preferences menu of xine-ui, my sound disappeared. this was easily fixed by manually setting the audio to driver to ALSA. I presume pulse would work too but haven't tried it.

I still get the odd segmentation fault that others have described with both frontends, but at least this way my desktop doesn't get killed. 

Peace

1.6 GHz P4 512MB RAM
Ubuntu 10.4
Geforce 6200 (driver built from Nvidia website)

---

