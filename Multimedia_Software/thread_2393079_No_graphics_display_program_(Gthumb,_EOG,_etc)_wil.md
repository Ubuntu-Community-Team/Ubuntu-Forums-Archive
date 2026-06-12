---
title: "No graphics display program (Gthumb, EOG, etc) will show MPG, MPEG, AVI, etc.)"
date: 2018-05-29
forum: Multimedia Software
---

### Post by RogerDavis on 2018-05-29
Title pretty much says it all - No graphics display program (Gthumb, EOG, etc) will show MPG, MPEG, AVI, etc.)

These have always worked in gthumb before, so I tried several now, the only one that works is VLC, and it's way too clunky trying to move from one video to the next.  

Gthumb will only show snippits of very few of them, but none successfully.  JPG works fine.

How can I make Gthumb work again?  I did nothing to change it, just normal updates called for by the system.

Thanks!

---

### Post by Perfect Storm on 2018-05-29
Thread moved to Multimedia forum.

---

### Post by mc4man on 2018-05-30
Run gthumb from the terminal, if you see this then a flaw in gthumb/gstreamer/libva (16.04, may be fixed in 18.04
[xcb] Unknown request in queue while dequeuing
[xcb] Most likely this is a multi-threaded client and XInitThreads has not been called
[xcb] Aborting, sorry about that.
gthumb: ../../src/xcb_io.c:179: dequeue_pending_request: Assertion `!xcb_xlib_unknown_req_in_deq' failed.
Aborted (core dumped)

Could be inconsistent as in a vid may work one moment, not the next.

If seeing above or similar then  remove gstreamer1.0-vaapi (if installed

---

### Post by RogerDavis on 2018-06-02
I ran gthumb from terminal, got this before any attempt to load a picture, though one thumbnail spot was highlighted.

```
(gthumb:12522): Gtk-WARNING **: Theme parsing error: gtk.css:27:35: Junk at end of value

(gthumb:12522): Gtk-WARNING **: Theme parsing error: gtk.css:40:48: Junk at end of value

(gthumb:12522): Gtk-WARNING **: Theme parsing error: gtk.css:48:46: Junk at end of value

(gthumb:12522): Gtk-WARNING **: Theme parsing error: gtk.css:59:58: Junk at end of value

(gthumb:12522): Gtk-WARNING **: Theme parsing error: gtk.css:70:46: Junk at end of value

(gthumb:12522): Gtk-WARNING **: Theme parsing error: gtk.css:81:58: Junk at end of value
```

No change after trying to manually show a video - no success.

gstreamer1.0-vaapi is not installed.

I have discovered that VLC, MPV, work, but are clunky.

"Videos"  not only won't work, but crashes every time.

EOG won't work.

gwenview won't work.

Thanks!

---

### Post by mc4man on 2018-06-04
Tried in both 16.04 & 18.04, in both cases gthumb works. The only difference is in 16.04 the vid will play in gthumb's window, in 18.04 it open a 2nd window for playback.
(- though the controls remain in main gthumb window.. screen shows 18.04 

As it uses gstreamer you have to be able to play these vids in a gstreamer player like totem.
Are all the the gstreamer media plugins installed?

gstreamer1.0-libav gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly

---

### Post by RogerDavis on 2018-06-16
All the codecs for gthumb got trashed.  I reinstalled, and now it works... but HOW did VLC work and Gthumb NOT work before on these same files ???

So not really solved...

---

### Post by Holger_Gehrke on 2018-06-16
Check the output of 'dpkg -s vlc'. vlc has it's own codecs and does not use gstreamer. So it's actually the opposite of a surprise that vlc wasn't bothered in the least.

Holger

---

### Post by RogerDavis on 2018-06-17
That helps.  

VLC might be better overall, but there is NO way I can find to advance or go back in file sequence without using the mouse.  Space forward, backspace back is good...  Do you know if this can be done?

---

### Post by Holger_Gehrke on 2018-06-17
If you've opened a playlist or a directory, then the next track / previous track media keys (if you have those) work. Alternatively 'n' for next and 'p' for previous. These are of course redefinable with Tools->Preferences->Hotkeys.

Holger

---

### Post by RogerDavis on 2018-06-18
OK, that helps.  Last point - is it possible to set it up so clicking a file in a file manager like XFE will automatically open VLC and then have the N and P keys work like gthumb does?
Thanks!!!

---

### Post by viktorbetter on 2018-06-18
I had the same problem, fixed after reinstalling

---

