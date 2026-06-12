---
title: "radeon driver in Edgy Eft"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by Joe_CoT on 2006-10-30
I'm trying to use the open-source radeon driver provided by xserver-xorg-driver-ati, as I am trying to use AIGLX, which is not supported by fglrx. When using the radeon driver, Xorg fails with the following error:

```
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 4.0.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(EE) module ABI major version (0) doesn't match the server's version (1)
(II) UnloadModule: "radeon"
(II) Unloading /usr/lib/xorg/modules/drivers/radeon_drv.so
(EE) Failed to load module "radeon" (module requirement mismatch, 0)
```

[This thread](http://ubuntuforums.org/showthread.php?t=280084) suggests that the reason is that I'm using an old version of xserver-xorg-driver-ati (he claims to have 1:6.6.2-0ubuntu4, I have 6.5.7.3-0ubuntu7). However, my version appears to be the newest; I'm using the us.archive.ubuntu.com repository, and I even checked the pool to see I'm indeed using the latest one in the repo (though it was last modified 01-May-2006). However, it very much looks to be compiled off the wrong version of xorg. Is there something I'm missing here?

---

### Post by CarpKing on 2006-10-30
I take it you upgraded from Dapper?  The ati driver is now called "xserver-xorg-video-ati."  There is a metapackage to install this and the other new drivers called "xserver-xorg-video-all."

---

### Post by sciurus on 2006-10-30
I had the same problem. CarpKing's suggestion will fix it. This among other things made for a pretty unsettling upgrade.

---

### Post by Joe_CoT on 2006-10-31
CarpKing's solution worked; thanks for the help. I'm now successfully running the radeon driver instead of fglrx. Unfortunately, the purpose of using the radeon driver was so I could use both DRI and the composite extension; I get a cheerful message in my xorg log telling me that DRI doesn't work on the 200m. Guess I get to wait for ATI to get off their butts and do something. ](*,)

---

### Post by warjowuch on 2006-11-05
WHat the heck, this metapackage installs all drivers for whatever kind of videocard you're using...
I suggest installing the suitable driver for one's card ought to be enough?? Why should this work better?

---

