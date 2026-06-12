---
title: "Totem crashes when playing DVD"
date: 2009-08-26
forum: Multimedia Software
---

### Post by Donnw on 2009-08-26
When I try to play DVDs with Totem the program instantly shuts down.  Other applications such as Mplayer and Kaffeine play DVDs without a problem. I  have had this problem since upgrading to Jaunty.

The output from the terminal after Totem crashes is:

/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
** Message: no file info
Device is now /dev/sr0
libdvdnav: Using dvdnav version 4.1.3
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 2D557427
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/kevin/.dvdnav/DVD_VIDEO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions:2 4
libdvdnav: Cell is in block but did not enter at first cell!
VTS change
totem: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:863: vm_get_video_aspect: Assertion `aspect == 0 || aspect == 3' failed.
Aborted

Can anyone help?

---

### Post by ajgreeny on 2009-08-26
If you are using totem-gstreamer, I suggest you uninstall it and use totem-xine instead, it is much better at DVD playback than the gstreamer default version.  However, I don't see why the gstreamer version would just crash as it does; you obviously have all the codecs etc that are needed, or mplayer and kafeine would not work.

If that is no good, it is perhaps worth purging all the totem apps then reinstalling them.  Perhaps totem is corrupt in some way and a reinstall would help.

---

### Post by Donnw on 2009-08-27
I uninstalled Totem and then installed the xine version. Th DVD playback now works.


Thanks!

---

