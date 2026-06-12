---
title: "Sync or stream media to AppleTV from Ubuntu"
date: 2008-06-15
forum: Multimedia Software
---

### Post by bsharitt on 2008-06-15
I recently got an AppleTV because I like the simplicity of the interface and the option to rent movies from my couch(which, aside from the fact I don't really care for MythTV, is why you shouldn't even bother suggesting "install Linux and run MythTV"), but at the moment, I'm using VMware server to run Windows XP and iTunes to sync with the Apple TV. This is pain in the *** because I have to load up a slow and bulky VM just to synce content, and all of my media won't fit on the AppleTV. So in order to stream all that media, I would have to keep the VM running all the time, killing a large portion of the usefulness of my PC, which is an 2GHz Athlon 64 x2 with 2 GB of RAM, but is quite bogged down as I type this due to the VM in the back ground actively running iTunes.

So far the two failed options I've looked into are Firefly(mt-daap) and iTunes in Wine. 

From what I can tell so far, Firefly can't stream to AppleTV, but I can't be sure because all I can really find so far when searching for mt-daap/appletv and firefly/appletv is how to get Firefly running on AppleTV, which isn't entirely useful for me.

As far as iTunes goes, it seems to run fine on Wine, but I can't see the AppleTV.

Anybody got Linux to sync with the AppleTV(running the AppleTV OS, not Linux)? If so, how'd you do it?

---

### Post by calif99x on 2009-02-04
I have been running iTunes in a VMware Workstation VM on Ubuntu for over a year.  You may need to rebuild the executable as my CPU consumption with a 2.8Ghz Intel processor is about 5%.

Functionally, the iTunes works find access content from a shared folder, but syncing to AppleTV is indeed very slow, which I think is due to iTunes rather than the VM.

---

