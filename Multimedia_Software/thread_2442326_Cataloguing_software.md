---
title: "Cataloguing software"
date: 2020-05-02
forum: Multimedia Software
---

### Post by mentalminion on 2020-05-02
Hello Ubuntu people.  Because of whats going on in the world, and Mr Gates Agenda in particular. Ive decided microsoft can do one.

However before i make the switch, i need to know if there are any such disk cataloguing tools such as VVV or wincatalog available.

I have 60Tb connected to this PC, i need to be able to keep tabs of where things are, and be able to keyword search for things quickly

TIA

---

### Post by TheFu on 2020-05-03
No clue what those tools are, but we have tools that can track PB of data and more, ZB.  **locate**, **recoll** are what i use. Lots of others if you all allow pre-indexing.  if you don't allow pre-indexing, then it won't be instant, but it can be complete. Mate has the mate-search tool.  Of course, you can use recoll and locate  if you prefer.

Recoll is like having google for your files, but you'll need to configure where the index goes.

For searching by filenames alone partial or exact, locate is the fastest.  Locate honors Unix permissions, so if a file in the index wouldn't be seen by the current userid, then the results will not show it.
```
$ locate -i analyst
/d/D1/M/Presidents_Analyst
/d/D1/M/Presidents_Analyst/Presidents_Analyst-dvd.mkv
/d/b-D3/M/Presidents_Analyst
/d/b-D3/M/Presidents_Analyst/Presidents_Analyst-dvd.mkv
```

Recoll has a gui.  There are probably 20 other tools similar to recoll.  i use it mainly without any gui.
if you keep media files in a media server, then that interface will have a search capability.

Recoll is very impressive.  But all of this is nowhere near enough reason to change an OS.

---

