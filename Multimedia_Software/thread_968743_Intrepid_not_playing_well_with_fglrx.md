---
title: "Intrepid not playing well with fglrx"
date: 2008-11-02
forum: Multimedia Software
---

### Post by WanderingFox on 2008-11-02
So I decided to give upgrading from hardy a shot after hearing that the ubuntu repo of fglrx was fixed to work with the new version of X. Unfortunatly, I cannot seem to get it to recognize my mobility 9600.  I heard of a few people having issues with this, but they all seemed to be resolved with removing fglrx completely and then reinstalling it.

That, however, doesn't seem to fix my issue.

In short, i'm getting a device not found on startup, and being forced into low graphics mode. The card does NOT show up in system>admin>hardware drivers at all, and both fglrxinfo and aticonfig are segfaulting when run.

I've tried installing everything manually, as per the instructions [here](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually), but it tells me I already have the packages in the first step, my xorg.conf is already edited, and the last step involving aticonfig segfaults without doing anything.

Thoughts? I'd rather not have to reinstall back to hardy in order to get my card to run >_<

---

### Post by bjtuna on 2008-11-03
You are not alone.  I experienced this as well, and reported it as a bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/292441](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/292441)

I haven't gotten any response yet, and I'm seeing similar bugs being reported.

---

### Post by WanderingFox on 2008-11-03
At least I know I didn't just botch the install or something XD

Thanks for the confirmation... Hopefully the release ATI drivers function a bit better.

---

