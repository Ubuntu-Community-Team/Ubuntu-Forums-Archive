---
title: "Missing needed files to burn a DVD disc"
date: 2017-01-05
forum: Multimedia Software
---

### Post by javierdl on 2017-01-05
[COLOR=#2E3436][FONT=&amp][Kdenlive]("https://kdenlive.org/") is only giving me a .vob file.[/FONT][/COLOR]
[COLOR=#2E3436][FONT=&amp]When I choose a DVD project with [/FONT][/COLOR][K3b]("https://apps.ubuntu.com/cat/applications/k3b/")[COLOR=#2E3436][FONT=&amp], and just before burning the disc, K3b tells me there are missing needed files to burn a DVD disc.[/FONT][/COLOR]
[COLOR=#2E3436][FONT=&amp]How to ensure Kdenlive will produce such files?

[/FONT][/COLOR][COLOR=#2E3436][FONT=&amp]I did try the DVD Wizard, but it freezes every time [/FONT][/COLOR][IMG]https://forum.kde.org/images/smilies/sad.gif[/IMG]
[COLOR=#2E3436][FONT=&amp]I was advised to get [DVDauthor]("http://dvdauthor.sourceforge.net/").

Unfortunately familiarity with programming is assumed. The 1st thing to do is to compile this, but the instructions are not exactly obvious: 

[/FONT][/COLOR]```
To compile, type
    ./configure
    make


Then to install, type
    make install



```

[COLOR=#2E3436][FONT=&amp]Like I suggested, I am not a programmer, so this is what I tried:

```


```[/FONT][/COLOR]```
javier@javier-Predator-G3-710:~/Downloads/dvdauthor$ ./cofigure
bash: ./cofigure: No such file or directory
javier@javier-Predator-G3-710:~/Downloads/dvdauthor$ ./cofigure make
bash: ./cofigure: No such file or directory
javier@javier-Predator-G3-710:~/Downloads/dvdauthor$ 

```

[COLOR=#2E3436][FONT=&amp]Most times I find it fun to tweak and learn stuff, but right now I just want to get this DVD done.
This being said, do you know another software to do this (getting the missing files) ?

Would [DVDstyler]("https://alternativeto.net/software/dvdstyler/") do it?

Thanks guys,

JDL[/FONT][/COLOR]

---

### Post by ajgreeny on 2017-01-05
In have only ever used **devede** which is in the repos and has always worked when I needed it, though that is not very often.  It will make a DVD from any video file that can be played by mplayer.

---

### Post by Autodave on 2017-01-05
*Brasero *is another good option. Also in the repos.

---

