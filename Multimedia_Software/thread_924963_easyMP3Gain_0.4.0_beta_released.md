---
title: "easyMP3Gain 0.4.0 beta released"
date: 2008-09-20
forum: Multimedia Software
---

### Post by Giantics on 2008-09-20
Yesterday easyMP3Gain 0.4.0 beta was released:D 
[http://sourceforge.net/project/showfiles.php?group_id=207001&package_id=247705&release_id=627331]("http://sourceforge.net/project/showfiles.php?group_id=207001&package_id=247705&release_id=627331")

Changelog:
 - AAC support (for ".mp4" and ".m4a" files, not raw ".aac")
 - Ogg-Vorbis support (".ogg" and ".oga")
 - GUI saves settings (target volume, etc..)
 - Recursive adding of files now works on NTFS-drives
 - New process-module (internally)
 - Console Output can be viewed
 - Localization-system changed to GNU gettext
 - Automatic album detection (by directory)
 - Accepts files as argument
 - Several other improvements

known bugs:
 - Drag & Drop does not work in the QT4-Version!
 - MultiSelect does not work in the QT4-Version!

There are also 64bit-packages. They have been created by the openSuSE BuildService (rpm). They are not tested yet.

I hope, that in the next version the QT4-MultiSelect problem is fixed. However it depends on Lazarus and the QT4-Bindings for the Pascal language. Then I will also create QT4-packages.

If someone wants to translate the GUI, just have a look at the po-files in "/usr/share/easymp3gain/lang/". Modify them, test them and mail them to me!

Have fun with easyMP3Gain 0.4.0

---

### Post by bttb on 2008-09-20
Hi there,

thanks for the pointer, I've subconsciously been looking for a tool like this. Until now I've used foobar2000 in Wine for "replaygaining" my mp3 files. Looks like I don't have to anymore.

A few things here and there. Are you sure this is a beta? On source forge it doesn't look like a beta, it looks like a release.

There's a little issue with the easyMP3Gain icon. It's shown in Gnome's menu but when easyMP3Gain is running the icon isn't shown in the top left of the window nor in Gnome's window panel.

I also get some warnings in ~.xsession-errors:
```

 Gtk2_ItemSelectionChanged  ItemCache=nil lvFiles
 Gtk2_ItemSelectionChanged  ItemCache=nil lvFiles
 Gtk2_ItemSelectionChanged  ItemCache=nil lvFiles
 Gtk2_ItemSelectionChanged  ItemCache=nil lvFiles
 Gtk2_ItemSelectionChanged  ItemCache=nil lvFiles
 Gtk2_Fenstermanager-Warnung: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1c00040 (easyMP3Gai)
Fenstermanager-Warnung: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
```

But it seems to run fine nevertheless. I'll give it a shot, thanks!

Regards

---

### Post by Giantics on 2008-09-20
> **bttb said:**
> Are you sure this is a beta? On source forge it doesn't look like a beta, it looks like a release.

Yes, it's still called beta (look at the main-window caption ;-)).
If you all find it stable enough, the next version won't be beta anymore.

> **bttb said:**
> There's a little issue with the easyMP3Gain icon. It's shown in Gnome's menu but when easyMP3Gain is running the icon isn't shown in the top left of the window nor in Gnome's window panel.

Are there black boxes instead? I'm using KDE 3.5 and 4. There it looked correct.
It's possible to be a problem with the programming IDE Lazarus, this is also still beta and some things don't work correctly yet.


> **bttb said:**
> ```

 Gtk2_Fenstermanager-Warnung: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1c00040 (easyMP3Gai)
Fenstermanager-Warnung: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
```

This seems to be a problem when using compiz.
[http://ubuntuforums.org/archive/index.php/t-609433.html](http://ubuntuforums.org/archive/index.php/t-609433.html)
[http://forum.ubuntuusers.de/topic/ati-radeon-7000/](http://forum.ubuntuusers.de/topic/ati-radeon-7000/)

---

### Post by redzheb on 2008-09-20
Great App by the way, i havent used the last beta tho.
but the previous beta saved my day :). I was using the one for windoze before. I guess the next one will be even better (and not beta ;) ). Keep on good work.

---

### Post by Joe on 2008-10-06
Giantics, just wanted to say thanks for putting in the work on this.  Can't wait for the QT4 version as well.

---

### Post by budigos on 2010-04-18
EasyMP3gain is really good for me... The GUI is almost the same as the Win version...

Easy mp3 has a new version already EasyMp3Gain 0.5.0
[http://sourceforge.net/projects/easymp3gain/](http://sourceforge.net/projects/easymp3gain/)

[IMG]http://3.bp.blogspot.com/_nGbTnWE9K7U/S8tFErxPsgI/AAAAAAAAAPw/ueBm3S7JgGo/s1600/Screenshot-easyMP3Gain+0.5.0.png[/IMG]

---

