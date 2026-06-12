---
title: "TuxGuitar Crashes When Closing Dialogs (64-bit, 13.10)"
date: 2013-11-07
forum: Multimedia Software
---

### Post by floborg on 2013-11-07
TuxGuitar is crashing when various dialogs are closed via an OK or close button.  As long as you avoid these settings dialogs, the app runs fine.

This is on a 64-bit Kubuntu 13.10 installation.  It was installed straight out of the repos.  The sound engine doesn't seem to matter as I've tried the jsa addon and timidity.

I ran the Excelsior JET version on a 32-bit install for years with no major problems.

Has anyone else seen this problem?

---

### Post by agustisenseh on 2013-11-17
Solution:
[http://www.alessandrosenese.eu/pillole/ubuntu/kubuntu-13-10-e-crash-applicazioni-java](http://www.alessandrosenese.eu/pillole/ubuntu/kubuntu-13-10-e-crash-applicazioni-java)

---

### Post by floborg on 2013-11-23
To save others from translating Italian, the workaround under KDE is to change the GTK2 theme to something other than oxygen-gtk.

Someone reported the Eclipse problem:
[Bug 324438]("https://bugs.kde.org/show_bug.cgi?id=324438")

It doesn't look like a fix is coming soon.

PS: Thanks.  I rarely get any responses.

---

