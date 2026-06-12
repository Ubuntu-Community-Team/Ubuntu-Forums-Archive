---
title: "Installing VLC player 1.1.x on Ubuntu 10.04 Lucid from ppa"
date: 2010-12-11
forum: Multimedia Software
---

### Post by krtica on 2010-12-11
This morning I tried to install newest version of VLC player (at this moment 1.1.5).
I went to [VLC media player for Ubuntu]("http://www.videolan.org/vlc/download-ubuntu.html") and followed instructions I found there.
For Ubuntu Lucid Lynx 10.04 LTS it was:
Command line way
```
sudo add-apt-repository ppa:lucid-bleed/ppa
sudo apt-get update
sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc
```
But! Installation process requires that DeVeDe, Mencoder and some other packages have to be removed. So I decided to choose "**n**" when it asked me about continuing installation. Strange thing was that process continued anyway :shock: and I had new version of VLC installed.
All my dependencies suddenly were broken and I was unable to install DeVeDe oe Mencoder even after I removed VLC and ppa. :confused:

Finally, after googling and searching trough forums, I found the way to fix it and completely remove VLC, DeVeDe and Mencoder.

Than, using a method of tries and errors :D I found the way and order of installing those packages. (At least I hope I have found it, since for now everything works.)

[LIST]
[*]DeVeDe and Mencoder have to be removed prior to installation of newest VLC from ppa.
[*]than I added ppa above and install new VLC
[*]installation of DeVeDe (which installs all dependencies including Mencoder)[/LIST]

I'll appreciate if anyone can tell me more about this issue and process. ;)

*PS: I'm using 64-bit Ubuntu 10.04.*

---

