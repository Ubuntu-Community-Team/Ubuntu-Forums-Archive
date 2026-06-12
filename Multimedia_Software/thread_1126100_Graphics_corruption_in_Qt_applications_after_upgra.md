---
title: "Graphics corruption in Qt applications after upgrade to Jaunty"
date: 2009-04-15
forum: Multimedia Software
---

### Post by vlovich on 2009-04-15
After upgrading to Jaunty (which comes w/ Qt 4.5), I got the same problem as [http://ubuntuforums.org/showthread.php?p=7069715]("http://ubuntuforums.org/showthread.php?p=7069715").  Would just like to say that the proposed fix does indeed work (disabling vertical sub-pixel rendering).

If you have ssh access into the foo-barred box, do the following:

ssh bad-machine -X
export `dbus-launch`
systemsettings

1.  Go into Appearance -> Fonts.
2. Change Use Anti-aliasing to false or
  (i) Force it to enabled
  (ii) Disable sub-pixel rendering or set it to RGB or BGR (not vertical)
3.  Hit appy & restart your apps.

Or for the command-line inclined:
Make sure you have the following set
XftAntialias=true
XftHintStyle=hintfull
XftSubPixel=rgb

in the [Global] section of $HOME/.kde/share/config/kdeglobals (mainly just make sure XftSubPixel is not set to vrgb or vbgr).

This should probably be made a sticky as the Jaunty release date approaches unless the bug gets fixed (I couldn't actually find it on Trolltech's or KDE's bug trackers).  Would've saved me tons of time & hassle (I thought it was the proprietary ATI drivers causing the issue).

---

