---
title: "DAAP music sharing in Rhythmbox?"
date: 2010-07-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by uBeer on 2010-07-04
Has anyone else noticed that the plugin is not there anymore? (Or are my eyes deceiving me...)
And if so: is there a way to reinstall the plugin?

---

### Post by zekopeko on 2010-07-05
> **uBeer said:**
> Has anyone else noticed that the plugin is not there anymore? (Or are my eyes deceiving me...)
And if so: is there a way to reinstall the plugin?

Either look for RB plugins in the repos or install tangerine from the repos. It's a simple standalone DAAP server.

---

### Post by uBeer on 2010-07-05
The package in the repo still states that the daap plugin is included, but it doesn't show up. Later today I'll file a bug.

I did install tangerine (used it before, didn't like it too much) but it won't start up (gives some exception) so I'll have to make a bug report for that as well...

---

### Post by moviemaniac on 2010-07-05
I don't know what a DAAP server is but I sure am missing my DLNA/UPnP media server in Rhythmbox.

---

### Post by seeker5528 on 2010-07-07
> **moviemaniac said:**
> I don't know what a DAAP server is but I sure am missing my DLNA/UPnP media server in Rhythmbox.

Apple uses DAAP for sharing/consuming locally shared media on your network, in the beginning it was more mature and functional than media sharing with UPnP.

UPnP was the MS/Intel alternative, I think there were multiple issues that caused it to be slow to take off in the beginning, but it's pretty well standard now. 

DLNA builds on top of UPnP and was the result of a bunch of companies that create media type networked devices getting together and creating a specification they could build against that would allow their various devices to work together.

Don't know what the support for DLNA is like on the Apple side of things, seems unlikely that they would move away from DAAP as the default, whether they support DLNA or not.

Going forward DLNA seems like the preferred way to go, in the short term it may depend on the devices and/or software you have and how you try to use the stuff.

Going from MythTV on Linux to XBMC on Windows seems to work reasonably well, within the limitations of the way MythTV presents the stuff on the network. 

For a more general DLNA solution rygel kinda seems to be leading the pack, as far as servers go.

Don't know what the current and future status of DAAP is on Linux, with DLNA support gaining in traction, it may be reaching the tipping point where developers feel it's no longer worth the effort to maintain support for something that is closed and has to be reverse engineered when there is a functional open alternative available.

Later, Seeker

---

### Post by kyleabaker on 2010-07-07
> **uBeer said:**
> The package in the repo still states that the daap plugin is included, but it doesn't show up. Later today I'll file a bug.

I did install tangerine (used it before, didn't like it too much) but it won't start up (gives some exception) so I'll have to make a bug report for that as well...

Confirmed. I hope its just "missing" cause that was a really handy plugin!

EDIT:
I just downloaded the source for Rhythmbox 0.13.0 and the "daap" plugin is still in the plugins folder. Maybe its just disabled atm. A bug report would be good still.
[http://projects.gnome.org/rhythmbox/](http://projects.gnome.org/rhythmbox/)

If you look at the news/changelog, you'll find this..
> 566852 - Move DAAP code to use common libdmapsharing

---

### Post by alexmurray on 2010-07-07
kyleabaker is on the right track: "*Important: because the DAAP plugin now uses libdmapsharing which is not available in the Ubuntu and Debian repositories, the plugin does not work for now, but libdmapsharing will probably be available soon!"

[http://www.webupd8.org/2010/07/install-rhythmbox-0130-in-ubuntu.html](http://www.webupd8.org/2010/07/install-rhythmbox-0130-in-ubuntu.html)

---

