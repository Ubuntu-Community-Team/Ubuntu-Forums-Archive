---
title: "Music library db idea... Is it any good?"
date: 2010-10-23
forum: Multimedia Software
---

### Post by adamwong246 on 2010-10-23
First post ever! Woot!

So I had an idea which I conceived while looking for a good media player. I tried out a lot of different players (songbird, amarok, banshee, mp3blaster and too many more to mention), which were all ok. But there seemed to be a problem: If a change was made to the file structure of my Music folder, calamities abounded, especially when switching players. Add that to the long rescan time for each player... For my modest size collection, it was intolerable. So heres the idea: 

Aggregate all the metadata for music files under a single database, which is available to all players and via a set of scripts, changes to the file structure and file metadata are easily made. A small script offers a standard interface to the db.

Obviously, players that exist already will need to be modified but if the code is stubbed well, it shouldn't be a huge deal. (maybe, I don't really know) Maybe the best solution is to allow the user to check an option that would enable my solution, as opposed to each applications default behavior?

The database would have a table to track file locations and metadata for each file like rating, play count etc so that each player would show synchronized, identical info. Other tables could hold a list of id's and would be comparable to playlists. Another table could hold a list of sql select statements- this would be a list of 'smart' playlists.
The script would update the db with all new files each time the a player was opened and maybe do other stuff, like using MusicBrainz to correct metadata and rename files and folders with a nice convention.

thought?

ps, I have a very unfinished ruby script, which in retrospect seems like a poor language choice for a finished product and which I doubt anybody will want to see.

---

