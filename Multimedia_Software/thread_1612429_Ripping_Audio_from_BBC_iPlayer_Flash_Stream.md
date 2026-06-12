---
title: "Ripping Audio from BBC iPlayer Flash Stream"
date: 2010-11-03
forum: Multimedia Software
---

### Post by zengyro on 2010-11-03
Hello all, 

So I am looking at ripping the audio from a [very old episode]("http://www.bbc.co.uk/programmes/p004y23x") of 'In Our Time'. The episode is so old that it predates the podcast (which of course, would solve all my problems). 

I would like to use something like icecream or VLC to rip the audio from the '[Listen Now]("http://www.bbc.co.uk/iplayer/console/p004y23x")' link on this page. Unfortunately I am having a hard time finding the actual URL. The player itself is a Flash widget, so it is something more complicated than looking for OGG, mp3 or RAM file extensions in the page source. 

Any ideas how i might track it down? Any general tips? 

If there are some nifty command flags I should add when invoking icecream on the command line, I am all ears.

---

### Post by ron999 on 2010-11-03
Hi
Look in Synaptic Package Manager.
Install the program named '**get-iplayer**'.

To download the episode use this command:-
```
get-iplayer --get --type=radio --pid=p004y23x
```

---

### Post by zengyro on 2010-11-03
Yeah I just found it. What an ace little program. 

Worked a treat! Thanks for your help

---

