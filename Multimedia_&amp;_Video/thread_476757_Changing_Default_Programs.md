---
title: "Changing Default Programs"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by sondo2121 on 2007-06-17
How can you set the default appllication for listening to MP3's?

I am looking for the equivalent to "Open With" and then selecting the "Always" option in Windows.

Right not when I open an MP3 file, Totem movie player starts, I would like Rythmbox to start up and play that file.

---

### Post by zvacet on 2007-06-17
right click on file<properties>open with

---

### Post by sondo2121 on 2007-06-18
this did not work.  I followed your instructions, and then tried to open an MP3, and Totem still tried to play it, this was after a restart as well.

---

### Post by sondo2121 on 2007-07-20
Is there another way to change the default programs?

---

### Post by abrichr on 2007-07-30
bump

this really shouldn't be so difficult.

---

### Post by capink on 2007-07-31
I think the file that control the default program is "defaults.list". There should be one copy of the this file in each user home directory. If not present you can then edit the system wide file.

the location of the per user file is:

```
~/.local/share/applications/defaults.list
```

the location of the system wide file is:

```
/usr/share/applications/defaults.list
```


open the file with your favorite text editor "you should open the local file first if present" and replace the following:

```
audio/mp3=totem.desktop
```

with

```
audio/mp3=rhythmbox.desktop
```

---

