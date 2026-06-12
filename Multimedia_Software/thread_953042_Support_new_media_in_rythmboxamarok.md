---
title: "Support new media in rythmbox/amarok"
date: 2008-10-19
forum: Multimedia Software
---

### Post by newgalois on 2008-10-19
So, I have a new Rizr phone, which have a decent music player. My hope is to be able to sync my music to this phone.

The Rizr music player have a relatively simple structure, with playlists stored in m3u file. So, I can half-manually sync my songs to the phone by:
- export by rythmbox playlists to m3u file
- write a (python) script to process the playlists, extract the song names, sync these songs to the phone (i.e. remove the songs that I don't need from the phone and add the new songs there).

It shouldn't be a hard task to make everything automatic. When I plug my phone in, rythmbox should recognize it. Then I should be above to mark some of the playlists. Rythmbox can then write the m3u files to the phone and run my script.

The thing is that I don't know how to write a rythmbox plug-in that recognizes my phone. The section "supporting new removable media" in their API seems to be left "TO DO" forever. (Again, this is the one thing I HATE about open source software: people don't bother complete their products before releasing them.)

Anyone has an idea? Someone has developed an iPod sync plugin. Thus, it must be possible to do this.

---

### Post by kostkon on 2008-10-19
> **newgalois said:**
> So, I have a new Rizr phone, which have a decent music player. My hope is to be able to sync my music to this phone.

The Rizr music player have a relatively simple structure, with playlists stored in m3u file. So, I can half-manually sync my songs to the phone by:
- export by rythmbox playlists to m3u file
- write a (python) script to process the playlists, extract the song names, sync these songs to the phone (i.e. remove the songs that I don't need from the phone and add the new songs there).

It shouldn't be a hard task to make everything automatic. When I plug my phone in, rythmbox should recognize it. Then I should be above to mark some of the playlists. Rythmbox can then write the m3u files to the phone and run my script.

The thing is that I don't know how to write a rythmbox plug-in that recognizes my phone. The section "supporting new removable media" in their API seems to be left "TO DO" forever. (Again, this is the one thing I HATE about open source software: people don't bother complete their products before releasing them.)

Anyone has an idea? Someone has developed an iPod sync plugin. Thus, it must be possible to do this.
If your phone is a MTP-based player, then try to enable the *MTP* plugin from *Rhythmbox*'s preferences.

If it is recognised as a *USB mass storage device* by the system, then try to create an empty file called *.is_audio_player* (with the dot in front) in the root folder of your phone (by going in the root folder and the right-clicking and selecting *Create a document-> empty file*). This will help *Rhythmbox* to see your phone as a media player device.

---

### Post by newgalois on 2008-10-21
What is MTP-based player?

Rhythmbox does recognize my phone, it's even "recognizes" (a bit wrongly) that it is "Motorola Razr". However, it cannot load the playlist in my phone. The way the playlist work is kind of ad-hoc, with m3u files as I described.

---

