---
title: "Rhythmbox + Large Library + .txt/.jpg files = FRUSTRATION!"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by raintheory on 2007-07-25
Okay so here's the deal:

 -  Rhythmbox 0.10.0 on feisty
 - Large music library (~150GB) on external firewire drive.

  I have rhythmbox set to watch my folder for new files, as I add new albums fairly regularly.  The problem is, I get numerous import errors and it takes FOREVER to scan for new files (I've let it go for 2 hours before closing it down).  When I rip albums to PC I usually include a txt file with information, as well as a jpeg of the cover art, Windows also throws in it's "thumbs.db" files.  These are the files that get import errors ("The stream is of a different type...", "The MIME type of this file...", etc.).  It would be incredibly time-consuming to sort through all of the folders to remove all of these offending files, and I'd rather not have to do that for other reasons as well.

  Basically Rhythmbox never actually imports any new material because it spends all of it's time scanning these other file types and spitting out errors.

  Is there a way to have Rhythmbox *ignore* specific file types?  

  I have no problems listening to music with the program, and I like the DAAP, so I don't plan to use a different player (unless there is one that has DAAP support...)

  Any help would be greatly appreciated!  :)

---

### Post by booljayj on 2007-07-25
I too have errors when importing some folders into Rhythmbox, but it will still find my music even through all the errors. Since you have such a large collection, it's understandable that it would take a long time to scan. Whenever I get a bunch of errors upon importing, I usually just remove them (right click-remove) without much consideration. They don't really mean anything, and Rhythmbox will still scan and find all the music. After you've scanned through them once, Rhythmbox shouldn't produce the same error for those files again. At least, it doesn't for me.

I would recommend just letting Rhythmbox do it's thing, even it it does take an obscenely long time, and then remove all the error messages that appear. You should then see all your music and not get the errors again.

---

### Post by raintheory on 2007-07-28
Well, I let it run/load overnight.  I then right-clicked on all the errors and chose "remove".

Unfortunately this hasn't solved the problem, the same errors start popping up again the next time the program is launched.

---

### Post by raintheory on 2007-11-02
I've upgraded to Gutsy and the problem persists...

I've been looking around with gconf-editor @ rhythmbox & gstreamer...  

Is there anything I can add in there somewhere to have either/or exclude/ignore specific filetypes?

---

### Post by Tiftof on 2007-11-06
> **raintheory said:**
> I've upgraded to Gutsy and the problem persists...

I've been looking around with gconf-editor @ rhythmbox & gstreamer...  

Is there anything I can add in there somewhere to have either/or exclude/ignore specific filetypes?

I justed started trying out rhythmbox and got the same problem. Any solution for this yet?

---

### Post by moderatelymodest on 2008-02-14
+1 on this.

major annoyance. :mad:

---

### Post by Martindale on 2008-04-27
Another bump, because this is lame. Major annoyance.

---

### Post by DaVince21 on 2008-06-10
+1 here. Rhythmbox adds all MIDIs it can find too, and whenever I try to remove them from the list it just re-adds them next time, so I'd like to have MIDIs (or plain directories) just ignored.

Even better, can't Rhythmbox just get all reported supported file types from GStreamer and only look for these files (plus maybe any manually defined file types)?

---

