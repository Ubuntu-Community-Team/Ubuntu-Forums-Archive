---
title: "Rhythmbox. All it seems to do is crash on me these days"
date: 2008-06-03
forum: Multimedia Software
---

### Post by Sweet Spot on 2008-06-03
I don't know what has changed but, up until about a month and a half ago, things seemed fine. Now, I'll just be sitting and listening to music and after a song is finished, RB just crashes. No error message, nothing. Has been going on for weeks now, and it's damned annoying to say the least. All I had running aside from it, was Gaim, and I wasn't even in an conversation. It was just opened, minimized. 

Has anything been going on w/it lately which might be causing this ? 

doug

---

### Post by WeEatVista on 2008-06-03
I haven't heard of any Rhythmbox crashes like what your specifying with no error messages or anything. Have you tried un-installing Rhythmbox and installing it again? Maybe it just installed wrong. If Rhythmbox still isn't working out for you, I use songbird (mozilla) for my music. It looks sort of like iTunes, and works pretty well with Ubuntu.

Sorry I wasn't much help, but thought I might as well post my suggestions.

-We Eat Vista

---

### Post by Sweet Spot on 2008-06-04
Thanks anyway. I've had RB installed and been using it since day one, (couple years now) and this is the first time it's acted flaky. Songbird is nice, but has a long way to go. It's way too bloated for my liking right now. 

Doug

---

### Post by kostkon on 2008-06-04
Do you remember if you have changed something that may cause these crashes? A good way to find out the problem is to run *Rhythmbox* from the terminal. Just open a terminal and call *Rhythmbox* like this
```
rhythmbox
```
and when it crashes there are many chances that you'll see some output. Although, it is better to run *Rhythmbox* in *debug mode*; a lot of output will be created, so be ready for this
```
rhythmbox -d
```
You can pipe the output to a text file, if I'm right, like this
```
rhythmbox -d > ~/rb_output.txt
```

---

