---
title: "Problem with Rhythmbox database"
date: 2012-03-22
forum: Multimedia Software
---

### Post by Abedi Pele on 2012-03-22
Hi all

Until now I have always find an answer among already posted thread. But this time I could not find.

I am using Rhythmbox and recently, I got big problems with the database. I am often entering information about mp3 files by hand (through the Properties menu.
When Rhythmbox crash or quit, it mixes completely the database (basically, all the file of the same album are going to have the same name).

I have tried to play with the database file (rhythmdb.xml), particularly making saves of it from time to time. But it does not work  (maybe it is due to the fact that I visualize the database with a text editor). I introduce more errors in the database if I correct the mstakes (with my back-up file).

So would you have a solution, first maybe to correct these Rhythmbox mistakes, and if not, to be able to play easily with the database.

Thanks in advance

Abedi

---

### Post by ageofsteam on 2012-04-17
Rhythmbox reads the ID3 song info from the files themselves.  When you use Rhythmbox to edit the track info, it is trying to write the information to the files, I think.  So editing the database won't help, since Rhythmbox will "fix" the track info by reading it from the (un-edited) files again.

I've had problems with Rhythmbox crashing when trying to write to files at times, too; I'm not sure what causes it. :(  It doesn't do it *all* the time, though, which makes me think something might be wrong with yours...

My shortcut is to install the Linux version of Mozilla Songbird and use it to edit the song information.  After you load a song into Mozilla Songbird, edit the track info and then save it, Rhythmbox will display the new info for the song when it loads.

I wish I could give a more "techy" solution, but my lazy version works pretty well. ^^;  And it's at least tolerable until something else comes along, ne?

---

### Post by Abedi Pele on 2012-04-23
I have reported a bug to Gnome, and apparently this is a known problem that they will solve in the next Rhythmbox version.
Thanks for your answer

---

