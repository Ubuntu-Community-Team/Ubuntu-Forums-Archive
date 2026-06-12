---
title: "Anyone know their way around id3ren?"
date: 2010-09-10
forum: Multimedia Software
---

### Post by man-man on 2010-09-10
First post in a while (tried Linux ages back, retreated, eventually came back around to the idea) so apologies if I'm in the wrong place or anything embarrassingly noobish like that.

Anyway, I just downloaded id3ren; id3-based file renamer, and whilst it works perfectly when pointed at a single folder I was hoping it would be able to go down though a folder structure to find files to rename. For example pointing it at an artist folder, and it finding the mp3s within all the album folders.

Current progress: ```
id3ren -template '%n - %s.mp3' home/user/Music/*.mp3
``` The above will rename anything in the folder specified. Just looking for that extra little addition to specify "and subfolders too"... something like the -r in the infamous rm -rf 

That, or if anyone knows of an alternative thing that would work in much the same way but work with subfolders... or if it came to it I assume it could be done with some scripting (not that I'd know *how* just yet, learn2script is still on the todo list).

---

### Post by v1ad on 2010-09-10
have you tried -r?

man id3ren

it should explain everything. i would check myself but i don't have it installed.

---

### Post by v1ad on 2010-09-10
hmm does not seem that it has that feature, maybe create a script that will send it into ascending folders.

---

### Post by man-man on 2010-09-10
Poked around a little further, I'm thinking ls -R would produce a list containing every subfolder (seems to include every file, looking at it)

But feeding that, one item at a time, and filtering for only the mp3 files, into the last argument of id3ren, that's a bit beyond my current knowledge.

Feels like it ought to be doable in one command by piping the output of ls somewhere clever, but it might be easier as a script (since I'll probably be saving it to a script file, even if it can be done in one line)

Edit in case anyone comes across this while looking for a solution: I didn't find one. It can probably be done without all too much effort but [ReNamer]("http://www.snapfiles.com/get/denrenamer.html") works pretty damn well under WINE and will rename files (including subdirectories) based on ID3 tags or any other rule you dream up, all from the comfort of a shiny GUI.

---

