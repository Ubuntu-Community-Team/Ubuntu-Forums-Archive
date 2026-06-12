---
title: "Trouble with ATi Driver installation"
date: 2007-02-02
forum: Multimedia &amp; Video
---

### Post by redbluemangle on 2007-02-02
I followed this guide for my Radeon 9550 AGP GFX card on Edgy: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2)

and after this command:

```
bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/edgy
```

I get:

```
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.33.6
............................................................................................
............................................................................................
............................................................................................
............................................................................................
............................................................................................
............................................................................................
............................................................................................
............................................................................................
.............................................................Extraction failed.
Signal caught, cleaning up
 
```

I think thats bad no? What's going on here?


EDIT: I just noticed that is leaves a fglrx-install folder on my desktop full of all kinds of .sh files and folders for many different linux distros. There area few readme's but they are very dense and not exactly my vernacular :-/

---

### Post by Paerez on 2007-02-02
Do you have enough free space?

---

### Post by EvilMarshmallow on 2007-02-02
I just installed a 9250 using your instructions.  Everything worked well for me.

I got an error slightly earlier in the process... it actually cleaned up after it errored out.  Mine was because I still had nVidia packages installed for my previous card.

insufficient space is a good possibility... might also be a corrupted download.  I know it verified the integrity of the archive, but who knows?

---

### Post by redbluemangle on 2007-02-04
> **Paerez said:**
> Do you have enough free space?

I have 130 GB of free space :-/ Perhaps someone who has successfully extracted then .deb files could host them on megaupload, sendspace or the like?

---

