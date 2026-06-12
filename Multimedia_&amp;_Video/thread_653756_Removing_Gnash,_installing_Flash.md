---
title: "Removing Gnash, installing Flash"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by Hex_Mandos on 2007-12-30
I've been having a problem with Flash. When I installed Gutsy a week ago, I installed Gnash as I'd read somewhere that it was ready. It isn't, many flash animations aren't displayed correctly. So I removed gnash and I'm trying to install flashplugin-nonfree, both via apt and automatically on Firefox, but I always get a "The Flash plugin is NOT installed." on the console as it finishes downloading.

Any ideas?

(BTW, I appreciate the work the Gnash people are doing, but I hate it when people announce stuff that's simply not true. I'll use Gnash as soon as it works correctly, but right now it can't replace Flash)

---

### Post by PmDematagoda on 2007-12-30
Did you remove Gnash before installing Flash?

---

### Post by Hex_Mandos on 2007-12-30
Yes.

---

### Post by ions on 2007-12-30
I'm getting the very same error on a brand new install.

The Flash plugin is NOT installed. after running sudo apt-get install flashplugin-nonfree

---

### Post by bliffle on 2008-01-01
That's odd: gnash is working fine for me on youtube and the few flash sites I encounter. I decided to NOT install Flash when I upgraded from Feisty to Gutsy because the Flash plugin had locked up gnome DTE and I had to RESTART. That happened a half dozen times. Also, someone reported an odd attempt by Flash plugin to access the internet. I'm not fond of closed software, having had so many problems and not really trusting their access to my data.

I DID have trouble with "Video DownloadHelper", which greyed out the browser (Firefox 2.0.0.11) screen and then locked up the whole ubuntu. So I removed gnash and Video downloadHELPER and re-installed gnash and it seems fine.

---

### Post by yaknowwat on 2008-01-01
yes this is a well known glitch.
Its due supposedly to a md5sum mismatch you have to install flash manually.

here's the thread for it [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

It would be nice if this was sticked until the problem was fully solved IMO.

---

