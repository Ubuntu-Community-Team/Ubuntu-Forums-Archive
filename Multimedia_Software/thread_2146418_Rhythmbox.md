---
title: "Rhythmbox"
date: 2013-05-18
forum: Multimedia Software
---

### Post by zxbcrhj on 2013-05-18
Just upgraded to Ubuntu 13.04 with Rhythmbox 2.98 and all my audio CD's are showing Unknown title and Unknown Artist.  With Ubuntu 12.10 and Rhythmbox 2.97 my audio CD's ahowd title and artist properly.  Any idea's

Thanks

---

### Post by mc4man on 2013-05-18
I filed a bug on this in Jan., no action,  RB is pretty much worthless for audio cd's
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1095105](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/1095105)

Edit: if I put up a RB-2.99.1 install then it works ok, so will likely be fixed in 13.10, never in 13.04
(maybe you can find a ppa for 2.99 for 13.04

---

### Post by mc4man on 2013-05-18
The gnome3 ppa has rb 2.99 packages for raring, they can be installed **without** needing to upgrade any add. non Rb packages from the ppa.
(upgrading completely using that ppa will currently cause issue with a unity session in 13.04

If inclined I do as such - 
```
sudo add-apt-repository ppa:gnome3-team/gnome3 && sudo apt-get update
```
```
sudo apt-get install --only-upgrade rhythmbox
```
```
sudo add-apt-repository -r ppa:gnome3-team/gnome3 && sudo apt-get update
```

---

### Post by zxbcrhj on 2013-05-19
I'll give it a try.     Thanks

---

### Post by dgundling on 2013-05-20
Tried your suggestion in 12.04. No luck. I have been trying to get Rhythmbox to play a music CD all the way through for over 3 months now. My first efforts yielded a freeze on the first song. Later I got it to play the first song but then it froze during the second. After doing as you suggested it got throught the first and second songs but froze on the third. The CD will play through easily on a WIN XP machine. I have the same problem with both of my Ubuntu machines. One is on an Intel processor. The other is AMD. Tried VLC and Banshee and neither of them work either. Has anyone been able to get RB to work? Thanks.

DAve

---

