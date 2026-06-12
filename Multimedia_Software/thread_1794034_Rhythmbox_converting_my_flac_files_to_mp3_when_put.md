---
title: "Rhythmbox converting my flac files to mp3 when put to portable player, how to stop"
date: 2011-06-30
forum: Multimedia Software
---

### Post by MechaMechanism on 2011-06-30
I don't want Rhythmbox to convert my flac files to mp3.  My portable player plays flac files just fine.

How to tell Rhythmbox to transfer flac files and not re-encode.

---

### Post by Chronon on 2011-07-02
I think it will behave how you want if you specify the correct output_formats in a .is_audio_player file:
[http://live.gnome.org/Rhythmbox/FAQ](http://live.gnome.org/Rhythmbox/FAQ)

I believe that audio/flac is the correct mime type.
[http://wiki.xiph.org/MIME_Types_and_File_Extensions#.flac_-_audio.2Fflac](http://wiki.xiph.org/MIME_Types_and_File_Extensions#.flac_-_audio.2Fflac)

---

### Post by SeijiSensei on 2011-07-02
Can you mount the player via USB?  My COWON appears as a USB mass-storage device if I connect it to Linux via the USB cable.  Then I can just copy files onto it directly without using any sort of player software.

My daughter's Sansa Clip works the same way.

---

### Post by MechaMechanism on 2011-07-02
> **SeijiSensei said:**
> Can you mount the player via USB?  My COWON appears as a USB mass-storage device if I connect it to Linux via the USB cable.  Then I can just copy files onto it directly without using any sort of player software.

My daughter's Sansa Clip works the same way.
I found I could use the .is_audio_player method espoused by Chronon to keep the flac files.  But I decided to use your method as it gives me more control ultimately.

---

### Post by Chronon on 2011-07-04
Ah.  I also just drag-and-drop to add music to my audio players.  I thought you actually *wanted* to use Rhythmbox for this purpose.

---

### Post by MechaMechanism on 2011-07-04
> **Chronon said:**
> Ah.  I also just drag-and-drop to add music to my audio players.  I thought you actually *wanted* to use Rhythmbox for this purpose.
I did but then I decided that it wasn't worth the hassle and just went to a manual method.  The .is_audio_player did work well though.

---

