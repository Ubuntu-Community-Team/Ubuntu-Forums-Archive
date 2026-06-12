---
title: "flash 10.1 crashes huludesktop and mythbrowser"
date: 2010-06-13
forum: Multimedia Software
---

### Post by samiller25 on 2010-06-13
Sorry for posting *yet another* flash complaint, but my issue seems to be different from the other threads.  I'm running 32-bit Mythbuntu 10.04, and I've installed the latest flashplugin-installer package (10.1.53.64ubuntu0.10.04.1).  Flash works great in Firefox 3.6.3 and Chromium 5.0.375.38.  However, it crashes the latest Hulu Desktop (0.9.7-1) and MythBrowser (0.23.0+fixes25073-0ubuntu0+mythbuntu2).  Hulu Desktop takes over a minute to start up, and at some point will crash with the message[INDENT][FONT=Courier New](huludesktop:2089): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
Segmentation fault[/FONT]
[/INDENT]If I try to load YouTube on MythBrowser, it will cause mythfrontend to crash with the following message:[INDENT][FONT=Courier New](process:2138): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.24.1/gobject/gtype.c:2706: You forgot to call g_type_init()

(process:2138): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:2138): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
Segmentation fault[/FONT]
[/INDENT]By the way, I can view non-flash pages fine in MythBrowser, and I can load YouTube if I rename /usr/lib/flashplugin-installer/libflashplayer.so to something else (though of course I can't view any of the videos).

In case it helps, I have libgtk2.0-0 version 2.20.1-0ubuntu1 and  libglib2.0-0 version 2.24.1-0ubuntu1 installed.

Most of the complaints I see about Flash are about 64-bit or about getting Flash to work at all.  Like I said, I'm running 32-bit and it works fine in Firefox and Chromium.  I suspect this is an OS or configuration issue because two very different applications fail when trying to use flash.

Does anyone else have this problem?  Any suggestions for further troubleshooting?  Any ideas what huludesktop and mythbrowser might have in common that does not affect Firefox or Chromium?

---

### Post by owlhoot on 2010-06-13
I had no problems with flash until this latest version came out. Hulu would not let me run a video until I upgraded my flash, however there is no version out yet which supports my 64 bit architecture. Looks like my hulu days are over until flash catches up to the rest of us. God I hate flash. It has never been good.

---

### Post by samiller25 on 2010-06-13
> **owlhoot said:**
> Hulu would not let me run a video until I upgraded my flash, however there is no version out yet which supports my 64 bit architecture.

Seems like everyone with 64-bit OS is having flash trouble.  But, just to clarify, **I am running 32-bit** and flash is still misbehaving.

---

### Post by rodan99 on 2010-06-14
I am using Arch. Your post helped me think it over. I had new installation of mythbrowser with flashplugin 10.1.53/686i it did the same. After sucessfull downgrade to flash 10.0.45/686i it is working now.

---

### Post by samiller25 on 2010-06-15
Some progress.  I downgraded flash to 10.0.45.2 as you suggested, and YouTube works and mythbrowser does not crash.  However, hulu.com and dailymotion.com now do not work.  That was the reason I upgraded to begin with: without 10.1, those sites simply don't play any video.

With either version of flash, huludesktop still crashes after a prolonged startup as described above.  So I'm beginning to think its problem is unrelated to mythbrowser's problem.

---

### Post by x-wolf on 2010-06-25
I had the same problem on 32bit system. Downgrade to 10.0.45 helped me out, but will be a problem every time i upgrade the system. Does anyone know when an update will fix this problem?

---

### Post by lotharjade on 2010-06-25
Hulu worked yesterday, but not today.  I suspect the 10.0.45.2 is the issue.  Odd that the start ad still plays.  I just wish I had a confrimation of what it is.

---

### Post by samiller25 on 2010-06-27
Well, I don't know what changed, but flash 10.0.45 seems to be more useful than it was.  I can now play videos from hulu and dailymotion with 10.0.45 whereas I couldn't before.  Flash 10.1 still crashes mythbrowser, though.

---

