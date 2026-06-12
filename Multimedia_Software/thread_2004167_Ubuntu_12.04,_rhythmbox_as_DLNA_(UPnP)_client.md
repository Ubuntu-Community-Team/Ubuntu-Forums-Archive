---
title: "Ubuntu 12.04, rhythmbox as DLNA (UPnP) client"
date: 2012-06-15
forum: Multimedia Software
---

### Post by Newbunto on 2012-06-15
I've just upgraded to Ubuntu 12.04 from 11.10 and one of the things that I noticed is that it appeared to change the default media player from Banshee to rhythmbox - hence my interest in rhythmbox.

Is there a plugin for rhythmbox so that it can access music via DLNA, and current instructions for how to make that happen?

I have a DLNA server on a different computer and a TV that is a DLNA client - and that all works well. (Video recorder is also a DLNA server.) So it would make sense for my Ubuntu PC to be able to be a DLNA client.

There seem to be mentions that this *was* possible.

Looking at the help for rhythmbox it appears to support something called DAAP but reading the Wikipedia article on DAAP suggests that it is the opposite of what Linux is about and should be avoided if possible !

---

### Post by druellan on 2012-06-17
Hi Newbunto.

Rhythmbox used to work fine on DLNA networks using Coherence Server as a plugin ([http://coherence.beebits.net/](http://coherence.beebits.net/)) but on 12.04 is no longer on repositories and I can asume is not compatible with this version of Rhythmbox.

Currently, the idea seems to use Grilo ([https://live.gnome.org/Grilo](https://live.gnome.org/Grilo)). Grilo-plugins-0.1 is on the main ppa, but so far I was no able to get DLNA support with it, and seems I'm not the only one: ([http://askubuntu.com/questions/103022/how-to-enable-grilo-upnp-plugin-in-rhythmbox](http://askubuntu.com/questions/103022/how-to-enable-grilo-upnp-plugin-in-rhythmbox)).

I'll post back if I'm able to find a solution.

---

### Post by Mac9 on 2012-07-15
If you install Rygel you'll be able to push content to Rhythmbox (or Banshee). 

The solution I'm running with is to [install XBMC]("http://wiki.xbmc.org/index.php?title=HOW-TO:Install_XBMC_on_Ubuntu/HOW-TO_1")

---

### Post by druellan on 2012-07-15
Hi Mac9.
Yes, I've installed Rygel, and works fine, but its a SERVER. What we want to acocmplish here is to use Rythmbox as a media CLIENT. On previous versions that was done using a Coherence plugin. Current version is supposed to work using Grilo, but on Ubuntu I did not found a way to Rhythmbox to use Grilo for DLNA my local server.

---

### Post by damnsavage on 2012-11-10
Check out these instructions here to install the grilo rhythmbox plugin on ubuntu 12.04
[http://bernaerts.dyndns.org/linux/240-ubuntu-precise-upnp-dlna-client](http://bernaerts.dyndns.org/linux/240-ubuntu-precise-upnp-dlna-client)

Its straightforward and worked for me :)

---

### Post by druellan on 2013-04-01
If you're using Rygel, there is a plugin you can install on Rhythmbox for better integration on the UI. Check it out: [http://code.google.com/p/rhythmpnp/](http://code.google.com/p/rhythmpnp/)

---

