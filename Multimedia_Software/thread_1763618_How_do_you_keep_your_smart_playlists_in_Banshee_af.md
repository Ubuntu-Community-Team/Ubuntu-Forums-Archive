---
title: "How do you keep your smart playlists in Banshee after reinstalling?"
date: 2011-05-20
forum: Multimedia Software
---

### Post by johnathanamber on 2011-05-20
Hey everyone,

I have several smart playlists that go by genre in Banshee.

Each time I reinstall my OS, I have to recreate them.

Does anyone know how to save your smart playlists so you can import them each time you reinstall?

BTW, R/C the smart playlist > Export will save an actual playlist, not the smart playlist which is dynamic.

-OR-

Does anyone know where Banshee saves their smart playlists so I can save those files and import them at a later time if needed?

Thank you and God bless,
Johnathan

---

### Post by ajgreeny on 2011-05-20
I don't really know, but it is probably all in either **~/.config/banshee-1** or **~/.gconf/apps/banshee**

---

### Post by b0b138 on 2011-05-20
Right click the playlist and export, save it somewhere.

Then on reinstall, goto media->import playlist

---

### Post by johnathanamber on 2011-05-20
@**b0b138**

Do you know how to save it as a **Smart Playlist** as opposed to a **regular standard playlist**? Exporting the playlist and reimporting it as a standard playlist doesn't help as I would have to recreate the Smart Playlist.

Does that makes sense?

Thank you and God bless,
Johnathan

---

### Post by bertram_wooster on 2011-09-27
@johnathanamber: This is important to me too.

With respect b0b138 does not answer the question asked, and it is a good one. I have a large number of smart playlists, which I build heirachically.

So I have a raw jazz playlist that contains artists I like, and a second one which includes everything in raw jazz and subtracts tracks and albums I don't like (the current banshee smart playlist system seems to require this). I do this for other genres, then compile them into a collected playlist. This way I can sync everything (in theory) to my ear-pod and get all tracks and all playlists on it (important for me).

However, this means I have a complicated set of smart playlists, with lots of requirements - long lists of artists etc. This sort of thing is essential if you are keeping track of 100s of GB of music. So I would like to store all the complicated requirements in my smart playlists, as I suspect does johnathanamber. It would be great to actually store smart playlists in persistent format, so when I stuff up my ubuntu install (as I have just done), I can reimport all the smart playlists.

Maybe I need to speak to the banshee team and help them code it up. Would others like this functionality?

---

### Post by omega_drh on 2012-05-26
This information is stored in ~/.config/banshee-1/banshee.db , which is an SQLite database. This can be read with something like sqlite3 (command line) or sqliteman (gui).

Specifically, the information is in the table 'coresmartplaylists' and the 'Condition' column is the most interesting (though PrimarySourceID and Name are probably useful to back up and insert in a new install as well). If you dump/save these, then you should be able to reinsert them in your new install (with sane values for SmartPlaylistID). You might be able to get away with just dropping the whole banshee.db file into your new system if the path to all your music stays the same (or you fix all those values).

An example of a Condition is:
```
<request><query banshee-version="1"><or><lessThan><field name="playcount" /><int>2</int></lessThan><greaterThan><field name="rating" /><int>3</int></greaterThan></or></query></request>
```

---

