---
title: "A couple of Sansa Fuze questions"
date: 2009-08-07
forum: Multimedia Software
---

### Post by Bartender on 2009-08-07
Just plugged a Sandisk 8GB microSD card into a 2GB Fuze.  The microSD shows up as a second device, with one folder - "Music".
I figured the Fuze would take advantage of the extra storage automagically but it didn't.  When I tried to load another audiobook into the original "audiobooks" folder I got an error message - not enuf room.

Anyone come up with a way to make the Fuze take advantage of the extra storage seamlessly?  It can't be as easy as creating another "Audiobooks" folder on the second device.  Can it?

I've been using ```
cat *.mp3 > *[COLOR="Blue"]file name[/COLOR]*.mp3
``` to merge dozens of .mp3's into one .mp3 file.    Does that same command work for .ogg files?  ```
cat *.ogg > *[COLOR="Blue"]filename[/COLOR]*.ogg
```

---

### Post by Bartender on 2009-08-08
OK, nobody responded, so here I go talkin' to myself again.

Here's what I found about accessing the microSD card.  The Fuze is plugged in to the Ubuntu PC, and I get two file browsers, one representing the Fuze and the other representing the microSD card.  When looking at the microSD card, all I saw was a MUSIC folder.  But if you double-click on it, the MUSIC folder shows two more folders within - Audiobooks and Podcast.  This is on a genuine Sandisk 8GB microSD card.  I don't know if the card was blank when purchased and the Fuze added these folders when the card was first installed?  Anyway, screenshot of both devices on the desktop - Fuze on left and microSD card on right - are attached.

Getting to the microSD card via the Fuze takes a couple of extra steps that I stumbled onto this morning.  Start up the Fuze, go to Home, scroll to Music, right-click wheel, scroll down to Folders, right-click the wheel again, and you'll see two entries - Internal Memory" & "External uSD Card".  Right-click on "External", go thru "Music" to find "Audiobooks".  The audiobook I dropped into the microSD card via Ubuntu was there and it played.  Yeah!!

The command line function does work when merging ogg files just like it does when merging mp3, but in this case it didn't do me any good.  Audio CD Extractor rips the CD as .oga.  I replaced ".mp3" with ".oga" and Ubuntu successfully merged the .oga files into one continuous file.  But the Fuze doesn't recognize .oga, at least not when generated from Sound Juicer.  

The Fuze's firmware was updated a couple of hours ago, so it's the latest.

The next thing to figure out is proper labeling so the Fuze doesn't just say "Unknown" or "Track 1" or etc.

---

### Post by Bartender on 2009-08-10
EasyTag seems to work pretty well.  I installed the one in repos.

Using EasyTag I was labeling the audiobooks in the "Title" line and leaving "Album" and "Artist" blank.  By mistake I tagged one of the CD's in the "Album" line and that seems to work better once it's loaded to the Fuze.  Instead of "Unknown", then having to right-click again, the tag comes up immediately with the Sansa "book" icon.

---

