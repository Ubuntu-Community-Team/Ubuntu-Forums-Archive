---
title: "media player classic"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by buccaneere on 2007-12-15
Edited: VLC player installed; see below please...

---

### Post by buccaneere on 2007-12-16
Well, I've loaded VLC, and it ain't properly playin' some .tsp's.

It zips through the whole file without audio or video, in about a minute.

What am I doin' wrong? 

Thanks.........

---

### Post by buccaneere on 2008-01-05
> **buccaneere said:**
> Well, I've loaded VLC, and it ain't properly playin' some .tsp's.

It zips through the whole file without audio or video, in about a minute.

What am I doin' wrong? 

Thanks.........

bumpintodatop.........

---

### Post by BreathEasy on 2008-01-06
I have no idea what .tsp's are, but ods are VLC hasn't got the right codecs for it and so it basically just seeks extremely quickly through the file until it ends.

My recommendation would be to open a terminal, type in **vlc** and try to load your file again. You can then observe the messages VLC prints in the terminal, which will hopefully include the failure.

---

### Post by buccaneere on 2008-01-06
> **BreathEasy said:**
> I have no idea what .tsp's are, but ods are VLC hasn't got the right codecs for it and so it basically just seeks extremely quickly through the file until it ends.

My recommendation would be to open a terminal, type in **vlc** and try to load your file again. You can then observe the messages VLC prints in the terminal, which will hopefully include the failure.

Hi breath...

.tsp is the format from which MPEG2 's offload (rip) from sattelite DVR HD's.

Terminal returned [HTML]VLC media player 0.8.6 Janus[/HTML].

Then another VLC interface popped up on my screen, waiting to play a file.

EDIT:
I quit the player to free the terminal : Cntrl C.

It gave me:
[HTML]signal 2 received, terminating VLC - do it again in case it gets stuck.[/HTML]

I entered 'exit', and nothing.

Cntrl C again...return:
[HTML]user insisted too much, dying badly
aborted (core dumped)[/HTML]

Help?

---

### Post by BreathEasy on 2008-01-06
OK, try a different player. In a terminal:

sudo apt-get install gmplayer
gmplayer

Run those two commands, and in gmplayer load up the file. Gmplayer (which uses mplayer as its engine) generally has a lot more success at file formats.

---

### Post by buccaneere on 2008-01-06
Thanks again there Breatheasy...

return:
[HTML]chuckacer@chuckb-laptop:~$ sudo apt-get install gmplayer
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gmplayer[/HTML]

---

### Post by buccaneere on 2008-01-06
Thanks again there Breatheasy...

return:
[HTML]chuckacer@chuckb-laptop:~$ sudo apt-get install gmplayer
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gmplayer[/HTML]

I have all software sources 'enabled'...

EDIT:
Oops - A couple of 3rd party sources are not checked, and a couple of update sources aren't checked...
Does that matter?

---

### Post by benerivo on 2008-01-06
Change it to```
sudo apt-get install mplayer
```According to last message on [this thread]("http://forums.afterdawn.com/thread_view.cfm/211001"), mplayer will play at least one type of .tsp file.

---

### Post by buccaneere on 2008-01-06
> **benerivo said:**
> Change it to```
sudo apt-get install mplayer
```According to last message on [this thread]("http://forums.afterdawn.com/thread_view.cfm/211001"), mplayer will play at least one type of .tsp file.

Downloaded, and working. Thanks benerivo...

Do you use this player? Is there a way to play in the FULL screen? I got it maximized, but the top and bottom taskbars are still at the borders, even with both on autohide for both.

Thanks again ...

EDIT: Does it have any controls at all? Pause, etc., ?

---

### Post by benerivo on 2008-01-06
I use vlc. It's been a long time since i used mplayer, but it's very popular so i'm sure someone will help you with this problem. It shouldn't behave the way you describe. Just to clarify - you selected the full screen option from within mplayer but it didn't cover the top and bottom gnome panels?

---

### Post by benerivo on 2008-01-06
> **buccaneere said:**
> EDIT: Does it have any controls at all? Pause, etc., ?Yes!! As far as i can remember mplayer should open from the main menu as two windows. One is the video window, and  the other is a controls panel, as here...

[IMG]http://www.debianadmin.com/images/mplayer.png[/IMG].

Right clicking in the video screen should give you a full screen option.

---

### Post by buccaneere on 2008-01-06
> **benerivo said:**
> Yes!! As far as i can remember mplayer should open from the main menu as two windows. One is the video window, and  the other is a controls panel, as here...

[IMG]http://www.debianadmin.com/images/mplayer.png[/IMG].

Right clicking in the video screen should give you a full screen option.

I closed the control panel window when the first started the file.

How do you open the control panel back up?

Rt click in the screen gives nothing........

---

### Post by buccaneere on 2008-01-06
Got the control panel back. Had to exit out of the CLI.

Thanks again...

---

### Post by BreathEasy on 2008-01-06
<disregard.>

---

