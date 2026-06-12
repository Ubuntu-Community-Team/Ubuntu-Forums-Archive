---
title: "Timidity server strangeness"
date: 2008-05-29
forum: Multimedia Software
---

### Post by Jefficus on 2008-05-29
I have a midi file that runs perfectly when I run directly, as in
```
timidity myfile.mid
```

However, strange things happen when I play it through timidity in server mode (which I launched using)
```
timidity -iA -B8,2 -Os1l -s 44100
```

In the case of aplaymidi, everything still sounds fine coming through the server (on port 128:0)
```
aplaymidi --port 128:0 myfil.mid
``` 

But if I use pmidi, I only hear the drum channel playing.
```
pmidi -p 128:0 myfile.mid
```

I'm guessing that there's a difference between the way pmidi connects to the timidity port and the way aplaymidi does, but I don't know what that difference is.

The real reason I want to know is because Rosegarden gives me the same drums-only playback, which suggests that it is using the same connection method as pmidi. I don't much care whether I use pmidi or aplaymidi from the command line, but I'd really like to figure out what's wrong with my Rosegarden setup.

I've tried this and had the same results on four different systems:
Ubuntu 7.04, Ubuntu 7.10, Xubuntu 7.10 and Ubuntu 8.04. In each case, I'm using eawpatches instead of freepats, but otherwise, they're all pretty vanilla installations.

Anybody have any idea what's going on? Any hints?

Jefficus

---

### Post by alainhenry on 2009-05-05
I have a very similar problem. Once the timidity server is launched (with the command line shown above), I have no sound from noteedit (even after selecting a correct midi port within noteedit). pmidi and aplaymidi behaves similarly.
Actually, it is quite erratic. sometimes it works fine (usually after several attempts), sometimes sound is very poor, sometimes no sound at all.
This happens with jaunty, but my configuration worked fine with all previous releases up to 8.04 (never used 8.10)
Help ?

---

### Post by alainhenry on 2009-05-07
This thread 
[http://ubuntuforums.org/showthread.php?t=440711]("http://ubuntuforums.org/showthread.php?t=440711") mentions that there could be an interaction with JACK and to use option -Oj instead of -Os when launching the timidity server. 
I will give it a try tonight if possible. Maybe removing JACK could do the trick to, if you don't need it. I think it got installed on my machine when I installed the Ubuntustudio-audio meta-package.
I 'll let you know what happens
Alain

---

### Post by alainhenry on 2009-05-08
Sorry, it didn't work. Jack was nor loaded or installed, as I had actually not installed ubuntustudio-audio.

---

