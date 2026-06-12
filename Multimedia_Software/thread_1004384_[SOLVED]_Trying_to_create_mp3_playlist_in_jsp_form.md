---
title: "[SOLVED] Trying to create mp3 playlist in jsp format"
date: 2008-12-07
forum: Multimedia Software
---

### Post by grahams on 2008-12-07
Anyone know a tool/ script to create mp3 playlist in jsp format (needed by networkmediatank)?

---

### Post by grahams on 2008-12-23
Figure it out myself.

This will create a random jsp playlist

find ./Music/ -type f |egrep -i '\.(mp3|wma|flac|ogg|mpc)$' | rl | sed 's#^\(.*\)/\([^/]*\)#\2|0|0|file://\1/\2#; s/$/|/' >playlist.jsp

---

