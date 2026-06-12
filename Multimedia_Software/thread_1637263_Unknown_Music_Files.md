---
title: "Unknown Music Files"
date: 2010-12-04
forum: Multimedia Software
---

### Post by vanoccupanther on 2010-12-04
Hello,

Have recently switched to Ubuntu 10.10 from Win Vista, due to the crappiness of vista a lot of my music was catalogued in multiple unknown folders with a few songs from each album in there. 

Is there a program/add-on I can get to identify these songs so I can put them in the correct folders before I import into Rhythmbox?

Also whats a good alternative to Rhythmbox? I recently read somewhere its not being supported anymore.

Thanks!

---

### Post by BcRich on 2010-12-04
hi vanoccupanther
I'm not sure if i understand your question correctly but if you are asking about how to organise your music collection most music players on Ubuntu read ID3 tags so the location of your files should not really make much of a difference to how your music is organized in your music player as long as your music files have the correct information in their ID3 tags. If on the other hand you need something to edit ID3 tags automatically you could use Entagged or Cowbell both of which search the internet to match ID3 tags to your untagged mp3's, ogg's etc.
regarding music players better than Rhythmbox, I'd recommend, Banshee if you are using Gnome and Amarok if you are using KDE. Of those two I prefer Amarok even though I use Gnome, which some people seem to think is sacrilegious :)

---

### Post by vanoccupanther on 2010-12-04
Hi BcRich,

Sorry if my question was not completely clear but you have answered it exactly. I'll get Banshee and an ID3 (something I never knew about, I'm computer simple) tag reader and post back to let you know how I get on.

Cheers

---

### Post by BcRich on 2010-12-05
Hi vanoccupanther
no problems glad I could help :)  
if you are using Banshee you might not actually need an ID3 tag editor.. if your music is all in subfolders of a main folder (called "music" for example) you can set Banshee to use that folder as it's "source" (in Banshee 1.6.0 Edit>Preferences>Source Specific). Banshee will scan this folder and all its subfolders, for music files and organize any music files it finds by ID3 tag information (including album name, artists name etc). Also if your music was organized by similar categories in your previous system, there's a good chance that your music already has iD3 tags, so you might not need an ID3 tag editor after all.
It might also be worth pointing out that once your music is identified by Banshee, and you don't like the way Banshee has organized it you can rearrange your music using Smart Playlists (in Banshee 1.6.0 Media>New Smart Playlist). These playlists allow you to list your music by filtering content such as names or how many times a track has been played amongst many other options. Finally you can also edit ID3 tags directly from Banshee 1.6.0 by right clicking on a track or a multiple selection of tracks and choosing "Edit track information". Newer versions of Banshee might have the same features in different locations.
Have fun, in my humble opinion Banshee is totally awesome!

---

