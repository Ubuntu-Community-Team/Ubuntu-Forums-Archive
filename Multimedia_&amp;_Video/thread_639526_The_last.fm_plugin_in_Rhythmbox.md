---
title: "The last.fm plugin in Rhythmbox"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by rljacobson on 2007-12-13
I would like to use the last.fm plugin in Rhythmbox. I have enabled the plugin, but I cannot listen to any stream. When I try to play a 'station' I get the following error message:
[INDENT]Couldn't start playback

Problem occured without error being set. This is a bug in Rhythmbox of GStreamer.[/INDENT]

I have the ubuntu-restricted-extras package installed. Am I missing some codec?

---

### Post by macabro22 on 2008-03-15
bump!

---

### Post by tenach on 2008-03-23
What gstreamer packages do you have?  To check open Synaptics and search for "gstreamer".  I have the good, bad and ugly gstremer packages, and it works fine.  I am not sure which one it is depending on however.

---

### Post by macabro22 on 2008-03-24
I also own the good, the bad and the ugly. Hilarious =]

---

### Post by SQuark on 2008-03-31
Same problem here. I've also got the base, good and ugly plugins and their multiverse variants.

The error header is always the same ("Couldn't start playback"), but the body switches between "Could not determine type of stream.", "(null)" and "Problem occured without error being set. This is a bug in Rhythmbox of GStreamer.".

---

### Post by SQuark on 2008-04-01
It started working now for me.

Try this:
[LIST]
[*]Close Rhythmbox.
[*]Open ~/.gnome2/rhythmbox/rhythmdb.xml (with gedit, Mousepad, Geany, ...)
[*]Delete every lastfm-station entry. (That is, everything from [FONT="Monospace;Courier New"]<entry type="lastfm-station">[/FONT] up to and including the next [FONT="Monospace;Courier New"]</entry>[/FONT])
[*]Open Rhythmbox and try again.
[/LIST]

---

### Post by el-mar01 on 2008-04-01
You have to give your Username/Password in the plug in properties.

---

### Post by tenach on 2008-04-01
> **el-mar01 said:**
> You have to give your Username/Password in the plug in properties.

Thanks, but that is not the issue.  The issue is that once logged in and status "OK", Rhythmbox's last.fm plugin does not submit scrobbles.

@ SQuark:  I have no such file.

---

### Post by SQuark on 2008-04-03
> **tenach said:**
> Thanks, but that is not the issue.  The issue is that once logged in and status "OK", Rhythmbox's last.fm plugin does not submit scrobbles.
That's not the issue either (at least not for me or the OP). Scrobbling worked fine. What didn't work was playing neighbourhood/artist/tagged streams from Last.fm.

> @ SQuark:  I have no such file.

Sorry, 't was a typo. The file should be: ~/.gnome2/rhythmbox/rhythmdb.xml.

---

### Post by tenach on 2008-04-03
Ah, okay.   I have that file.  Thanks.

---

