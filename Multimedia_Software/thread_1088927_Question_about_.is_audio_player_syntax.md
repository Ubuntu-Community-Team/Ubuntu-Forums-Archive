---
title: "Question about .is_audio_player syntax"
date: 2009-03-06
forum: Multimedia Software
---

### Post by Charlotte18 on 2009-03-06
I'm trying to build the .is_audio_player file on an mp3 player. So far I seem to have gotten the audio_folders and, maybe, the folder_depth entries correct. I'm having trouble with playlist_format and playlist_path. It seems the Rhythymbox is writing playlists to the correct path, but these playlists do not seem to contain the correct file paths. "Not found" errors occur when I try to play the playlists.

Does anyone know more information on what options are available in the .is_audio_player file, or about the usefulness of these options in Rhythmbox and Banshee?

---

### Post by Charlotte18 on 2009-08-18
Here are the contents of the file I am using:

```
audio_folders=MUSIC/
output_formats=audio/mpeg
playlist_path=PLAYLIST/%File
playlist_format=audio/mpeg-url
```

The problems I have are these:

1. Rhythmbox writes playlists correctly to the PLAYLIST folder on the device. However, instead of heeding the "playlist_format" line, Rhythmbox puts the lists in .pls format.

2. Banshee writes playlists to a folder called PLAYLIST that Banshee  creates within the MUSIC folder on the device. Banshee seems to ignore the "playlist_path" line.  Banshee puts the playlists in m3u format though.

---

### Post by Charlotte18 on 2009-08-22
bump

---

### Post by linusr on 2010-05-13
> **Charlotte18 said:**
> bump

any success?

---

### Post by dartmusic on 2010-05-13
> **linusr said:**
> any success?

I've been after this same info for about 18 months.  It seems simple enough, but somehow one bit is not communicating correctly with other bits, be it the .is_audio_player file, the device, the program (Banshee, Rhythmbox, etc.).  

I would love to see this clarified once and for all.  

Sorry to make this a "me too" but I want to keep an eye on this.

---

### Post by r2d2rogers on 2011-01-07
I'm working on a .is_audio_player file for my Captivate.

I noticed your m3u mime type didn't match to what I found,  I see:

audio/x-mpegurl

This is also a useful reference [http://cgit.freedesktop.org/media-player-info/tree/media-players/samsung_galaxy.mpi](http://cgit.freedesktop.org/media-player-info/tree/media-players/samsung_galaxy.mpi)

If anyone is still looking at this, I'll post my file when I get it working.

---

### Post by josh23920 on 2013-02-01
The .is_audio_player file AND setting my device to MSC transfer mode (saw that in another post someplace) seems to have done the trick!

My setup is an Ubuntu 12.04.1 LTS 64-bit Athlon x2/nVIDIA laptop... and a lowly lil ole Philips GoGear Vibe (4GB) MP3 player.

Worked like a champ in Windoze, took SOME fiddling with in Ubuntu; but, thanks to smart people on the forums its working again!!!

Thanks to all of you who work, play, and break (then fix) stuff and are willing to share with us newbies!

---

