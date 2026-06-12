---
title: "icecast2 and ices setup"
date: 2017-07-10
forum: Multimedia Software
---

### Post by bill-lancaster on 2017-07-10
Have installed icecast2 OK (I think).  I can access Icecast2 Admin through the browser.
Installed ices2 and set up a play list for 3 .ogg files without success
Looking at the ices.log I see this error:-
```
playlist-builtin/playlist_read Error opening file " /home/bill/Music/Library/001462.ogg": No such file or directory
```
The path is correct so where have I gone wrong?
Any help would be appreciated

---

### Post by bill-lancaster on 2017-07-10
OK, file not found error caused by a space character in front of the path string!
Fixed that, now :-$ sudo ices2 /home/bill/Music/ices-playlist.xml produces this line in ices.log
```
[WARN playlist-builtin/playlist_read Corrupt or missing data in file (/home/bill/Music/Misc/stan1.ogg)
```
and this error shows in terminal ```
Segmentation fault (core dumped)
```

Most of my .ogg files are the product of my own editing, perhaps they are corrupt in some way although mplayer plays them without comment.

---

