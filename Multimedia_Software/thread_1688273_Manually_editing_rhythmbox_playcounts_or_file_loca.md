---
title: "Manually editing rhythmbox playcounts or file locations?"
date: 2011-02-15
forum: Multimedia Software
---

### Post by db579 on 2011-02-15
I have several albums in my Rhythmbox library that I originally ripped in 128kbps and have listened to many times. I'd quite like to reimport the songs in higher quality now but don't want to lose the playcounts associated with them.

Is there any way to transfer the playcount over to the new file as it were, or to manually edit the playcount or file location?

---

### Post by jerrrys on 2011-02-16
i always though that 128 kb was high quality.

---

### Post by Hawkoon on 2011-02-16
> **jerrrys said:**
> i always though that 128 kb was high quality.

Very much depends on your hearing abilities, and the kind of music and how much acoustic detail you care for.

But back on topic, I would simply overwrite the original files with the new ones - no import necessary. This works only if the new files have the exact same name as the old ones. Play counts will be maintained, tag information will be updated next time you turn on "monitor library for changes".

---

### Post by db579 on 2011-02-17
Thanks problem is I want to import them in flac now so they'll have a different file extension. I'm guessing that means your suggestio won't work?

---

### Post by db579 on 2011-02-17
Is there any way of getting rhythmbox to upload all your past playcounts to Last.FM like iTunes does?

---

### Post by Hawkoon on 2011-02-17
> **db579 said:**
> Thanks problem is I want to import them in flac now so they'll have a different file extension. I'm guessing that means your suggestio won't work?

In that case, you will have to edit the files' locations in rhythmbox's database manually.

    1) shutdown rhythmbox

   2) make a backup of the database file, in 10.04 it is in ~/.local/share/rhythmbox/rhythmdb.xml

   3) if the only difference is the file extension, replace the file extensions of the relevant files, or otherwise modify the location strings so they point at the new files

Hope you dont have too many albums to update, will be lot of work.

Why is the play count important anyway? If it is just for keeping track of your favourite albums/songs you could do this:

   1) create an automatic playlist based on play count value. That playlist will have only the albums/songs you want to reimport as flac.

2) export the playlist to a file, say fav_albums.m3u

3) replace the old .mp3s with the new .flacs. Don't change the directories.

4) edit fav_albums.m3u and replace all occurrences of .mp3 with .flac

5) import fav_albums.m3u into rhythmbox.  It is now a static playlist, and you can add songs/albums to it if you have new favourite albums.

6) you can delete the automatic playlist

Alternatively, write a script that checks if files specified in the location strings exist, and if not replace .mp3 to .flac.


As for your question on uploading play counts, no idea. Open a new thread on that, you are likely to get more help then.

---

### Post by db579 on 2011-02-18
Thanks very much exactly what I wanted, although having thought about how much effort this would involve (many albums) I decided to scrap the playcounts.

Cheers though!

---

