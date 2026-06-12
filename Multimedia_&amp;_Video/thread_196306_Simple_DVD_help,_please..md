---
title: "Simple DVD help, please."
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by lagerratrobe on 2006-06-14
Ok, it's after 10:00, and I don't feel like dorking around with this anymore.  I have Dapper installed on my laptop and it seems to be working well.  It comes with 2 applications that appear at first glance to support the playback of DVD's.  I have disk 3 of the Dune SciFi Miniseries in the player, and I get a stupid error in Totem, and nothing in VLC. H

ere's my question:
How do I get the 2 applications that come with Dapper to play my DVD?  I don't want to install a bunch of other crap, and I've just run 
"sudo /usr/share/doc/libdvdread3/examples/./install-css.sh"

Thanks in advance.
--

---

### Post by lagerratrobe on 2006-06-14
Enabling DVD support in Ubuntu 6.06
-----------------------------------
Using [https://wiki.ubuntu.com/RestrictedFormats#alternateplayers](https://wiki.ubuntu.com/RestrictedFormats#alternateplayers)

> sudo apt-get install totem-xine
> sudo apt-get install gxine
> sudo apt-get install libxine-ext

The above listed webpage says to load the 2 packages below as well, but they both fail, and don't seem to be necessary.

NOTE: libxine-extracodecs install failed
NOTE: mplayer install failed

Now I wonder if there is a way to see the chapter titles and navigate through the DVD by clicking on them?
--

---

