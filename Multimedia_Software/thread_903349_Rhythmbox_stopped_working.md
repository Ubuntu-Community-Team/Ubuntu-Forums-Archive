---
title: "Rhythmbox stopped working?"
date: 2008-08-28
forum: Multimedia Software
---

### Post by tipii on 2008-08-28
I use rhythmbox everyday and have done for a couple of years. Three days ago it simply stopped working and I have no idea why. It opens up fine, reads my library and still watches my music folder for new entries but as soon as you try to play music, whether off the HDD or through the lastFM plugin, the screen fades to grey and it hangs. I have re-installed but the problem remains.

I can still play music through other media players like vlc and lastFM.

Has anyone come across this and solved the problem?

---

### Post by tdrusk on 2008-08-28
> **tipii said:**
> I use rhythmbox everyday and have done for a couple of years. Three days ago it simply stopped working and I have no idea why. It opens up fine, reads my library and still watches my music folder for new entries but as soon as you try to play music, whether off the HDD or through the lastFM plugin, the screen fades to grey and it hangs. I have re-installed but the problem remains.

I can still play music through other media players like vlc and lastFM.

Has anyone come across this and solved the problem?
Try turning off desktop effects, since that is what makes windows turn gray.

---

### Post by tipii on 2008-08-28
Thanks, I turned it off but now rather than turn grey, Rhythmbox just hangs.

---

### Post by tdrusk on 2008-08-28
> **tipii said:**
> Thanks, I turned it off but now rather than turn grey, Rhythmbox just hangs.
Okay. Try running it in the terminal and see what output is shown. Maybe it's segfaulting.

---

### Post by tipii on 2008-08-30
Ok, today it doesn't just hang, bonus! Instead it tries to play a track, fails and then skips through all the tracks in the library, failing to play any of them. I didn't receive any errors in the terminal until I managed to catch it, pausing it before it skipped to the next track. This is what I got:

```
tom@home:/media/hda5/My Music/Fairmont/Coloured In Memory$ rhythmbox 01-fairmont-fade_and_saturate.mp3 

** (rhythmbox:10702): WARNING **: Invalid borders specified for theme pixmap:
        /home/tom/.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Frame-Gap/frame1.png,
borders don't fit within the image

** (rhythmbox:10702): WARNING **: Invalid borders specified for theme pixmap:
        /home/tom/.themes/Mac4Lin_GTK_Aqua_v0.3/gtk-2.0/Range/null.png,
borders don't fit within the image

(rhythmbox:10702): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed

(rhythmbox:10702): RhythmDB-CRITICAL **: rhythmdb_entry_ref: assertion `entry != NULL' failed

(rhythmbox:10702): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed

(rhythmbox:10702): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed

(rhythmbox:10702): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed

(rhythmbox:10702): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed

(rhythmbox:10702): RhythmDB-CRITICAL **: rhythmdb_entry_get_ulong: assertion `entry != NULL' failed

(rhythmbox:10702): RhythmDB-CRITICAL **: rhythmdb_entry_get_string: assertion `entry != NULL' failed

```

The first two errors there are to do with my emerald theme, I get them with everything but they're just warnings so i can live with them. The third worries me a little as I have no idea what it means, I think it may have something to do with my buuf pixmaps (icons). And the rest... again, no idea! I thought perhaps the hard-drive containing my music was too full so I cleared a few gigs but it didn't fix it.

---

### Post by tipii on 2008-08-30
I installed "esound" and "esound-clients" after stumbling across  Luke Robinson's post :

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg546536.html]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg546536.html")

and Rhythmbox works again!

Thankyou TDRusk for your time.

How do I mark a topic as solved please?

---

