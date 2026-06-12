---
title: "MythMusic Playlists"
date: 2012-01-14
forum: Mythbuntu
---

### Post by Sctmon on 2012-01-14
I think I am having a strange problem with MythMusic but am unsure if it is a bug or not.

When start a frontend, navigate to Music/Select Music/All My Playlists and then select a playlist I can then see what tracks are in that playlist. If I then scan for new music,  just the playlist names are there, I can select them but cannot see the contents. If I exit the frontend and restart it I can then navigate into the playlists and see the contents.

I have also just written a java program that reads an iTunes library, takes the playlists and recreates them in the MythMusic library if it finds matches to the the appropriate files. The problem is that when I create the new playlists in the database they don't show up either without exiting and restarting the front end. Scanning for new music does not update them.

Any ideas if this is how it is meant to function?

---

### Post by Sctmon on 2012-01-27
Bump!

If I create a new playlist  in MythMusic and then query the database for that playlist it returns the playlist successfully but the playlist_songs field remains empty until the frontend is exited and restarted. After a restart playlist_songs has been populated with the correct track IDs.
The playlist and its contents are visible and can be selected in MythMusic though before restarting so is there another temporary table in the database that they are being stored?

---

