---
title: "custom srt styles with mplayer"
date: 2008-07-04
forum: Multimedia Software
---

### Post by CraymelCage on 2008-07-04
Hello I'm using mplayer no-gui from the midibuntu repo. I want to customize the font and colour of srt files in mkv's.

When I put something like this in the config file
```
***-border-color=BL
***-color=RR
```

It ends up looking like this:
[IMG]http://i88.photobucket.com/albums/k200/J------n/screenshot3.png[/IMG]
or this:
[IMG]http://i88.photobucket.com/albums/k200/J------n/screenshot2-1.png[/IMG]

I also want to change the thickness of the border and the font as well. It would be nice if your answers could involve the config file because I find it easier to edit from there then from the terminal. You can give terminal command because I can still use them in the config file. Thanks for the help in advanced.

---

### Post by CraymelCage on 2008-07-04
Okay so I figured out how I can change the font for srt subtitles with:
```
a s s-force-style=FontName=<InsertFont>
```
The only problem is that this changes the a s s/ssa subtitle files to the same font as the srt. I'm also still having problems with the colour. I only wan't the srt to be changed with out affecting any other subtitles. Still waiting for some help.

---

