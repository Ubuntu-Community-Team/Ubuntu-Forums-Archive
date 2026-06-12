---
title: "Amarok commands in terminal"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by FaceorKneecaps on 2007-01-30
Solved...




I run Edgy and do love to do my things in terminal (reminds me of the Dos days, and it  is fast as f***)
So is there a way to control my Gui players in the terminal? 

If I want to see a movie I need to pause my amarok to run my vlc. When done I want to run my amarok after shutting down vlc. 

My biggest issue adding/showing/removing songs in amarok while in terminal......
Is this possible? or do I need a new player? I do want the same player for both moods.

---

### Post by kebes on 2007-01-30
In KDE there is something called [DCOP]("http://en.wikipedia.org/wiki/DCOP"), which allows you to pass messages/commands to applications. There is a commandline tool of the same name: "dcop". So in bash scripts and in python code you can write things like:

dcop applicationname dothis

Of course the syntax for "dothis" is going to depend on the application. Amarok should support that kind of inter-process communication.


Hope that helps...

---

### Post by FaceorKneecaps on 2007-02-01
Thank you Kebes...

I run Gnome but googled for DCOP gnome and found bonobo.... 

To the reading and learning!

---

### Post by Jojo12a on 2007-02-01
Well, dcop is available as soon as amarok and its dependencies (namely kdelibs4c2a) are installed. Bonobo is afaik not at all compatible to DCOP ;)

for examples, see [http://amarok.kde.org/wiki/DCOP_Functions](http://amarok.kde.org/wiki/DCOP_Functions)

---

