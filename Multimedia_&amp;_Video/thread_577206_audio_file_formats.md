---
title: "audio file formats"
date: 2007-10-15
forum: Multimedia &amp; Video
---

### Post by doKtor_hallam on 2007-10-15
ok, i have a secondary hard drive shared by kubuntu and win200 with approx 10,000 music files on it (my entire cd collection, and yes, they are all legally mine)
about 70% are .wma
the rest are mp3
i can :

1)convert all wma to mp3, then find/install an mp3 player into kubuntu, thus leaving all files avail in both os's.

-or-

2)convert both wma and mp3 to another format more suited to kubuntu, leaving them potentially unaccessable in win2000 (which would be an inconvenience for now, but not in the long run as i look to drop windows when i am knowledgable and able enough to replace all win2000 activities in kubuntu)

any suggestions?  also does anyone know any good freeware file format converters that can do an entire directory in a single command? (as i am NOT wanting to do this 1 file at a time)

many thanks for any suggestions
chris

---

### Post by doKtor_hallam on 2007-10-16
does anybody have any suggestions here?

---

### Post by Samhain13 on 2007-10-16
You can try using ffmpeg. It's a command line tool for converting between formats. Example code would be (in the directory where a music file is):

```

ffmpeg -i song.wma song.mp3

```

But it has lots of other settings that you might want to explore. It can also convert video files. I'm just not sure how to use it for bulk conversion.

There's also mencoder. Both are available in the repositories,

---

### Post by doKtor_hallam on 2007-10-16
thank you, i will look into them both. i appreciate the help.

and i am not becoming a fan of amarok, it seems rather buggy.  just in playing around with it and experimenting and learning, i have had it crash several times. and i havent changed any settings or anything, just in browsing its tabs and menus it freezes on me regularly. could this be a hardware issue? or is amarok known for bugginess?

can anybody tell me a good file format that has a nice coexistence of quality/small size/and is supported by a good player/library in kubuntu?

thanks all..

---

### Post by Samhain13 on 2007-10-17
Ogg Vorbis. :D

---

### Post by Druke on 2007-10-17
OGG Vorbis > than all

(my opinion)

---

### Post by FredB on 2007-10-17
> **Druke said:**
> OGG Vorbis > than all

(my opinion)

My opinion too ! Ogg is really a great format for music.

---

