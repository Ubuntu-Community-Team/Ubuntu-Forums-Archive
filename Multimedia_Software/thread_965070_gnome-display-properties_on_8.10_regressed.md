---
title: "gnome-display-properties on 8.10 regressed"
date: 2008-10-31
forum: Multimedia Software
---

### Post by secdroid on 2008-10-31
I'm seeing the same problems with gnome-display-properties on the final shipped version that I saw on the release candidate (but _not on the beta_) -- [http://ubuntuforums.org/showpost.php?p=6030826&postcount=1]("http://ubuntuforums.org/showpost.php?p=6030826&postcount=1")

Desktop is larger than physical screen and the panels are not visible.  Monitor is overscanned and there is a whine from the flyback.  Display is distorted.

From Live CD, ALT-F2, gksudo **gnome-display-properties** applet is invoked, settings are changed from (automatic) 1152x864 (4:3) 75KHz to (manual) 1024x768.  Click "apply" and "done" and _resolution is unchanged_.

Display and monitor specs -- [http://ubuntuforums.org/showpost.php?p=6033060&postcount=5]("http://ubuntuforums.org/showpost.php?p=6033060&postcount=5")

8.04.1 works perfectly on the same hardware.

Update: Just learned two things about this problem:

-- There is a difference between System->Preferences->Screen Resolution menu choice and ALT-F2 gksudo gnome-display-properties.  The ALT-F2 does not work for me, but the System menu option does work.  This makes no sense.  (I "felt" around with the mouse on the invisible off-screen portion of the desktop for the menu.) 

-- I misunderstood the wiki & forum comments about xorg.conf.  While the 8.04 displayconfig-gtk could "clobber" xorg.conf, the 8.10 gnome-display-properties is said to leave it alone.  While one should not need to manually update xorg.conf in 8.10, I believe that it is allowed.  I'll try that next.

So, I'm posting from the 8.10 i386 Live CD.  The network problem I reported in the Beta appears to be resolved.

---

