---
title: "iPod / m4a issue"
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by palintheus on 2006-07-20
I was using this thread: 

[http://ubuntuforums.org/showthread.php?t=103071](http://ubuntuforums.org/showthread.php?t=103071)

to get my iPod working on my desktop. I used my iPod to move my music folder from my windows laptop to the ubuntu desktop. Put the folder into my home folder. Then following the instructions I selected the 'Local' play list and did file>Add Directory, and chose the file with all my music. Every song produced an error:

Import of '/home/trey/Music/3 Doors Down/Away From The Sun/Away From The Sun.m4a' failed: m4a/m4p/m4b not supported without the mp4v2 library. You must compile the gtkpod source together with the mp4v2 library.

I have no idea how to do this.....any help would be greatly appreciated!

---

### Post by Dubbayoo on 2006-07-20
Let me guess - you installed gtkpod instead of gtkpod-aac

---

### Post by palintheus on 2006-07-20
EDIT : Thanks, problem solved.

Did 
```
sudo aptitude update && sudo aptitude install gtkpod-aac
```

It removed gtkpod automatically.

---

### Post by Dubbayoo on 2006-07-21
I think you need both.

---

### Post by growingneeds on 2007-12-02
The command
"sudo aptitude update && sudo aptitude install gtkpod-aac"
does not solve the issue of mp4 incompatibility. Please refer to this thread instead:
[http://ubuntuforums.org/showthread.php?t=601429](http://ubuntuforums.org/showthread.php?t=601429)

---

