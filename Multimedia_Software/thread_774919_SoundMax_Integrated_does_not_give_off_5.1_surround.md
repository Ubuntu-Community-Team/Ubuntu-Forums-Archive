---
title: "SoundMax Integrated does not give off 5.1 surround."
date: 2008-04-29
forum: Multimedia Software
---

### Post by pogoyoyo on 2008-04-29
Hey, i have an intel motherboard with a soundmax integrated sound card on my desktop pc. it has an orange, green and blue input sound jacks ( on windows, the orange is for center / sub, blue for rear speakers, and green for front ). my logitech z 5300's work fine on windows, but i cant get them running. i use amarok and ive tried almost everything. i hope someone has a solution for me :)

---

### Post by pogoyoyo on 2008-04-29
help please

---

### Post by dublued on 2008-05-02
I was having the same problem with my Asus M2NPV-VM board.  Stumbled across this and 5.1 surround works like a charm.

here is the post:  [http://ubuntuforums.org/showthread.php?t=515003&highlight=soundmax+surround](http://ubuntuforums.org/showthread.php?t=515003&highlight=soundmax+surround)

and here are the instructions if you don't want to click

from user:  mgmiller

> To turn on surround sound:
1) Open the volume control by double clicking the speaker icon in the top panel.
2) Click on edit preferences.
3) Put check marks in both the surround and channel mode boxes.
(you will have to scroll down the list to find channel mode)
4) Make sure the slider for surround is turned up and not muted.
5) On the Options tab, select 4ch, 6ch or 8ch as appropriate. 


To test the speaker set up with a spoken voice for each speaker,
copy the following commands to a terminal.

7.1 channel surround:
speaker-test -Dplug:surround71 -c8 -l1 -twav 

5.1 channel surround:
speaker-test -Dplug:surround51 -c6 -l1 -twav

4 channel surround:
speaker-test -Dplug:surround40 -c4 -l1 -twav

2 channel:
speaker-test -Dplug:front -c2 - l1 -twav

the -l1 makes it play the voice 1 time, change the number to anything reasonable. If you leave this out it repeats till you close the terminal..

for more info man speaker-test

Note:
Sometimes you may have to move the actual speaker jacks around while the voice is describing which channel is which to get everything right.

EDIT:  Although the speaker test works just fine, playing mp3 or videos (encoded with surround) do not utilize all of the speakers.  only the front 2 are used.  is this a problem with the player itself?  i've tried VLC, Mplayer, Movie Player and Audacious... all with the same results

any help is appreciated

---

### Post by dublued on 2008-05-11
bump... please help

---

