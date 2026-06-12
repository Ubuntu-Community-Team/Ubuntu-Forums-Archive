---
title: "returning unmount, fixing open w/ other"
date: 2010-10-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mc4man on 2010-10-10
With some recent talk about the removed unmount option and the obvious defect in the open with other app menu...
I happen to find the unmount useful so have returned here and find the open w/ other changing the default folder handler annoying so have also 'negated'

For those interested am attaching 2 patches that ATM will apply cleanly to current nautilus source in maverick. (2.32.0-0ubuntu1

 Future updates to nautilus will most likely break the line numbering, the code within should remain viable for some time so can be used as a guide to create new patch(s) or manually apply.

Presumes some know-how to building, though would help if needed. 
(any corrections are certainly welcome

Basically to do
apt-get the source and build deps of nautilus

Extract the attached folder, take the 2 patches inside  and place in the /nautilus-2.32.0/debian/patches folder.

Also included is a series file - [COLOR="Blue"]EDIT[/COLOR] - (the latest nautilus in maverick - ..0ubuntu1.1, has a new patch - # 96 so just edit in the new ones using the included series file as a guide)( the patches are still good))   -  it lists the patches to be applied - if the open with isn't desired just comment out the line in the series file - the number's used for the patches are just what I felt like using

As far as versioning
you could leave the /debian/changelog alone, the new packages would install as a re-install, then you'd need to pin - not advised though ok (if unhappy then the easiest to revert, just allow nautilus to update back to unpatched version

Up the version by 1 -  (1:2.32.0-0ubuntu[COLOR="Blue"]2[/COLOR]) will not be updated until nautilus updates - you will be notified first by update manager ect.

I use this - a new entry

> nautilus (1:2.32.0-0ubuntu1+nmu1) maverick; urgency=low

  * restore unmount option
  * make inactive the Remember option on open with other application
    context menu

 -- Doug Mc <mc4man@nowhere.com> Sun, 10 Oct 2010 01:18:38 +0200

nautilus (1:2.32.0-0ubuntu1) maverick; urgency=low

  * New upstream release:
    - Fix places sidebar sometimes not changing location when clicking on a
      place (LP: #625938)
    - Fix various crashers (LP: #630884)
    - Translation updates

 -- Didier Roche <didrocks@ubuntu.com>  Tue, 28 Sep 2010 01:18:38 +0200


Build with whatever package build command you wish, I use debuild -us -uc though this will suffice

```
dpkg-buildpackage -rfakeroot -D -us -uc
```

After build just install the whole group with sudo dpkg -i *.deb
( i usually create a folder named "in" in source dir. and move what I want installed in  - the -dev and dbg may not be needed by most,

I use nautilus elementary now - patches avail. upon request, can no longer attach to this post

=======================================================================

Regards to natty - both patches are still good, the offset for the 1st. 2 in the unmount has been increased by 15, the patch should still apply or edit the line #'s by + 15 for 1st two like - 
```
--- nautilus-2.31.90.orig/src/nautilus-places-sidebar.c
+++ nautilus-2.31.90/src/nautilus-places-sidebar.c
@@ -13[COLOR="Blue"]51[/COLOR],7 +13[COLOR="Blue"]51[/COLOR],7 @@
 	}
 	if (mount != NULL) {
 		*show_eject |= g_mount_can_eject (mount);
-		*show_unmount = g_mount_can_unmount (mount) && !*show_eject;
+		*show_unmount = g_mount_can_unmount (mount);
 	}
 }
 
@@ -13[COLOR="Blue"]84[/COLOR],8 +13[COLOR="Blue"]84[/COLOR],6 @@
 		*show_start = g_drive_can_start (drive) || g_drive_can_start_degraded (drive);
 		*show_stop  = g_drive_can_stop (drive);
 
-		if (*show_stop)
-			*show_unmount = FALSE;
 	}
 
 	if (volume != NULL) {
```

---

