---
title: "Mythmusic: how to delete music ?"
date: 2008-11-12
forum: Mythbuntu
---

### Post by laffinet on 2008-11-12
How do I delete music from the database in mythmusic ?

I know how to get it off the active playing queue, but say I want to permanently delete a file from my /var/lib/mythtv/music folder and then have it removed from the database too, how do I do that ?

Or is it enough to just delete the file ? Will it produce errors if the song is still in the database but the file is gone ?

---

### Post by hoffman462 on 2009-05-24
If a music collection is moved (migrated) to another machine, is it possible to remove the /var/lib/mythtv/music collection without causing errors?

I don't know.  I see this question posted alot on forums but I don't see any answers, I also don't see a 'how to remove' local file cache / db cache guide.

curious if there is answer.

---

### Post by crez79 on 2009-05-24
Under Utilities->Music Tools->Scan for new music  will scan the music folders and update the database with the music it does or doesn't find. You can add or remove music from the watched folders and it will fix the database. You can remove music from the playlist, but I don't know of any way to remove music from the database from the frontend, but why would you want to do that?

---

### Post by NautiusMaximus on 2009-07-18
I can think of one reason why you'd want to do it: the details of the music are recorded incorrectly in the database, and you want to delete it from the database so that you can import it again with the correct details.

Unless there's a way to edit the details of music once it's imported. I haven't been able to find a way: does anyone else know of one?

---

### Post by Milan Knizek on 2011-09-11
I know it's an old thread, however, since I have been struggling with the topic recently (mythtv 0.24.1 fixes), the information might be useful for some.

In my case, I renamed the directories, file names and changed metadata of the songs (by purpose: cleaning the house a bit). Mythmusic was not able to open some files (it remembered old directory name) and it did not help to "scan for new songs" after pointing to an empty directory. A rather messy situation.

Finally I simply installed phpmyadmin, logged into mysql with the same login as mythtv and deleted all entries in music* databases (albums, artists, directories, songs, etc.). I do not use any playlists, so it caused no harm.

I guess that there might be some script within mythtv, though this direct method worked well, too.

---

