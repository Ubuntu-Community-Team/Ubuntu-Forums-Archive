---
title: "Kaffeine won't play DVDs, VLC Media Player will"
date: 2010-01-03
forum: Multimedia Software
---

### Post by Objekt on 2010-01-03
Kaffeine (version 1.0-pre2) refuses to play DVDs.  I already installed both the Ubuntu Restricted Extras package and all the packages listed at Medibuntu.org.  In a previous Kubuntu 9.04 install, this was enough for Kaffeine to play either a DVD, or an *.iso image of that DVD.

I did a little detective work by running Kaffeine from the command line.  When I tried to load a DVD .iso, the following messages appeared in the console:

```
objekt910@objekt910-desktop:~$ libdvdnav: Using dvdnav version 1.1.16.3 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: BOMBERS_B_52
libdvdnav: DVD Serial Number: 39645168
libdvdnav: DVD Title (Alternative): BOMBERS_B_52
libdvdnav: Unable to find map file '/home/objekt910/.dvdnav/BOMBERS_B_52.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
```

I also got an error dialog in the Kaffeine window, which stated:
```
Could not start process Unable to create io-slave:
klauncher said: Unknown protocol 'dvd'.
```

Meanwhile, VLC Media Player has no problem playing either *.iso images of DVDs, or actual DVDs.  Clearly, the relevant packages are present to allow playing DVDs so why won't Kaffeine do it?

Yes, I could just use VLC to watch DVDs, but it bothers me when stuff is broken for no reason.  Also I like some of the features and general layout of Kaffeine better than VLC Media Player, probably because I am so used to Kaffeine from running Kubuntu.

Anyone know how to fix this?  The Kaffeine forums aren't too active, so I'm hoping someone here has a solution.

update:
I am also unable to rip DVDs in Kaffeine.  It works fine in Brasero, which tells me that the underlying packages are in place to allow working with DVDs.  For some reason Kaffeine just refuses to use them.

---

