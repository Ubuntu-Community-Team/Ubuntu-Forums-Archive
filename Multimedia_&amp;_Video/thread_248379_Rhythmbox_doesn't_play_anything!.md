---
title: "Rhythmbox doesn't play anything!"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by max_croft on 2006-09-01
I've taken care of all the restricted formats. Everything plays fine in Totem, but whenever I try to open up even a single file in Rhythmbox, nothing happens. It looks like it was preparing to play but nothing gets added, no files in the library or the queue despite all attempts at trying to import files or folders.

I'm not getting any errors or crashes either. It just doesn't play. What's going on?

---

### Post by encompass on 2006-09-01
Did you get any information when running rhythmbox from the console?

---

### Post by max_croft on 2006-09-01
If I type this at the console:

rhythmbox overkill.mp3

It returns:

Failed to load file://home/max/Desktop/overkill.mp3: No reply within specified time

---

### Post by max_croft on 2006-09-01
This is different. If I type

sudo rhythmbox overkill.mp3

I get:

(rhythmbox:8953): Rhythmbox-WARNING **: couldn't connect to session bus: No reply within specified time

(rhythmbox:8953): Rhythmbox-WARNING **: Unable to start mDNS browsing

Don't know what those errors mean, but once they went past, rhythmbox actually started and the file played!

So what does this mean and how do I go about fixing it?

---

### Post by encompass on 2006-09-01
weird... but you don't have rights to do something with rythmbox.  Sheck your rights in the user and group settings under the administrations menu.
And those errors are no big deal.  As long as it plays.

---

### Post by max_croft on 2006-09-01
I'm part of the admin, lpadm and max groups.

I tried it again, this time if I right-click and choose to open the mp3 with Rhythmbox, it runs the program as if trying to load the file and then quits.

This thing seriously has me confused.

---

### Post by faledrol on 2006-09-08
I have this problem too:
with ubuntu 6.06 just installed, and after, uploaded with all the gstreamer packet, when i first start Rhythmbox from menu i see only the first wizard page, then the page it's blocked (no response).

When I load from console nothing return and nothing is show.
When I load with sudo, i get this message (and first blocked page):

(rhythmbox:12380): Rhythmbox-WARNING **: couldn't connect to session bus: No reply within specified time

(rhythmbox:8953): Rhythmbox-WARNING **: Unable to start mDNS browsing

I have try to remove, it has been removed, it has written that he couldn't find:
/usr/share/scrollkeeper/Templates/null/scrollkeeper_cl.xml
When I had reinstalled, in sudo mode show me:

(rhythmbox:12380): Rhythmbox-WARNING **: couldn't connect to session bus: No reply within specified time

(rhythmbox:12380): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

(rhythmbox:12380): Rhythmbox-WARNING **: Unable to load icon media-eject

---

