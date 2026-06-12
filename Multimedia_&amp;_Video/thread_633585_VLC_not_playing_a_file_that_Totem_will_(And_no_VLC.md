---
title: "VLC not playing a file that Totem will? (And no VLC update"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by theShaggy on 2007-12-06
So here's something bizarre:

I've been slowly downloading a large torrent containing video files - getting chunks, burning them to DVD, getting more (It's Dr. Who... far too big for my harddisk).  Up until this point, I've never had a problem.

The weird part is just now, after I'd updated Deluge, the only remaining video files from the previous download batch play fine in VLC, but any of the new ones that are completed won't.  They open, run for two seconds and stop.  No video, no sound, nothing.  There isn't even a length in VLC of any sort.

However, it will run fine in Totem player, which is strange since I've always known VLC to play ABSOLUTELY EVERYTHING while Totem wouldn't.

Is this something I'd go to VLC about, or does anyone have any idea what's up?

Secondly, there was a new release of VLC the other day, with some security fixes and such.  I have been trying to update, but none of Gutsy's package managers seem to list the new version, they're keeping the old one.  Will we be able to find a deb somewhere?

---

### Post by bsmith1051 on 2007-12-07
I'm looking for the update, too.  It's hit-or-miss whether or not these 'secondary' apps get updated in the repositories (and auto-distribute to everyone).

---

### Post by wolfen69 on 2007-12-07
For Ubuntu Gutsy I386 add the following line to your sources.list:
deb [http://nightlies.videolan.org/build/gutsy-i386/arch](http://nightlies.videolan.org/build/gutsy-i386/arch) ./

then do-  sudo apt-get update

it should show up as an update, or just download from synaptic.

---

