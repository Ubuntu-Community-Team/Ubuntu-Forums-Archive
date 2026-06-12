---
title: "K3b Missing Lib Files"
date: 2008-04-18
forum: Multimedia &amp; Video
---

### Post by LOBONCA on 2008-04-18
When I open kb3 I am told there are missing Libs files

yet I cannot find these files with the package manager.

Mp3 Audio Decoder plugin not found.


"K3b could not load or find the Mp3 decoder plugin. This means that you will not be able to create Audio CDs from Mp3 files. Many Linux distributions do not include Mp3 support for legal reasons.

Solution: To enable Mp3 support, please install the MAD Mp3 decoding library as well as the K3b MAD Mp3 decoder plugin (the latter may already be installed but not functional due to the missing libmad). Some distributions allow installation of Mp3 support via an online update tool (i.e. SuSE's YOU)."

Can anyone help?

---

### Post by Kevbert on 2008-04-18
Hi. I've installed K3b and it seems to work fine.  It may mean that you need to load additional codecs.  I installed mine by using Quickstart.  It can be found here: [http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart](http://ubuntuforums.org/showthread.php?t=613462&highlight=quickstart)
Hopefully this will help.

---

### Post by xc3RnbFO8P on 2008-04-18
I install this in Synaptic Package Manager:
libmad0
libmad0-dev
python-pymad

k3b
k3b-i18n
libk3b2
libk3b2-extracodecs
libk3b2-mp3
libk3b-dev

dvd95
dvdauthor
liba52
liba52 dev
libdvdnav4
mkisofs

---

