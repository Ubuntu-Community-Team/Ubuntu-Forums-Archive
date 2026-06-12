---
title: "Is there anyway to import my iTunes library into Banshee?"
date: 2009-04-01
forum: Multimedia Software
---

### Post by villainy on 2009-04-01
I've looked everywhere and can't find a solution for the latest version of Banshee, 1.4.3.

I've read before, there was a plugin that imported the .xml file from iTunes, but is no longer available since it's built into newer versions of Banshee.

How can I do this with 1.4.3?

---

### Post by lindsay7 on 2009-04-01
Banshee is in my Synaptic and add/remove list. I just copied the whole itunes folder to Ubuntu and put it in a music folder. If Banshee does not find it by itself, you can import the folder and it will pick up everything.

---

### Post by Backharlow on 2009-04-01
Bare in mind, even if you couldn't get Banshee to use the actual xml lib from itunes just pointing it dumbly at the main music directory will pull in almost all of the meta data you were seeing in itunes, i.e. album, artist, etc. because that data is embedded in the id3 tags within the audio files themselves and is thus software player gnostic.
If you don't do an import.. I just use Firefly on Mac/Win to stream itunes over a network to Ubuntu on demand. Works great in Banshee.

---

### Post by narmoture on 2009-04-15
in Banshee, go to Media in the menu, select Import media (or press ctrl+I), select Local Folder and navigate to your iTunes Folder. click it once and the click open. Tadaa!

Now, to figure out how you import playlists....

---

### Post by nortexoid on 2009-04-25
> **narmoture said:**
> in Banshee, go to Media in the menu, select Import media (or press ctrl+I), select Local Folder and navigate to your iTunes Folder. click it once and the click open. Tadaa!

Now, to figure out how you import playlists....

Suppose none of your music is contained in your iTunes folder. Then does what you suggest work? Or is what you suggest just importing the music without ratings, etc?

---

### Post by Backharlow on 2009-05-05
In itunes... use the Consolidate Library feature. This will migrate (make a copy of) all of the audio files that your itunes library is using, and merge those copied files into the main itunes music library folder. That way you then have all of your actual sound files in one central folder and not strewn all over. You can prevent this from happening in the first place by setting the preferences to make a copy in the library at import.
but if you're just ditching itunes, do the consolidate library function, then verify that that main itunes folder now has those aggregated copies of everything. then go to banshee and point it at that folder.

---

