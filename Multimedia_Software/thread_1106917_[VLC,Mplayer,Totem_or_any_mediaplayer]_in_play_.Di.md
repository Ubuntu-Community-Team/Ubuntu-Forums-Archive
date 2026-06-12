---
title: "[VLC,Mplayer,Totem or any mediaplayer] in play .DivX files&gt; can't show with Subtitle"
date: 2009-03-26
forum: Multimedia Software
---

### Post by Vahids on 2009-03-26
i try to play DivX movies (.divx) but, when i try to set subtitle of the movie in mpayer when right click >> Video >> Track >> track 2 ::> i have this Error:
Code:

Cannot find codec matching selected -vo and video format 0x42535844.

and in VLC i have this Error:
Code:

main decoder error: no suitable decoder module for fourcc `DXSB'.
VLC probably does not support this sound or video format.

in smplayer when i set track 2 of video just play audio without video

*** My .divx movies had a hard subtitle in .dix file ! noting srt OR idx or any subtitle file exist,
just a .divx file, this file can had more than 1 subtitle whit herself!!!

[CENTER]-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=[/CENTER]
Come on MAN, help me! Please. it's just my problem in linux! i didn't have like this problem in WINDOW$ please help me!

---

### Post by aeiah on 2009-03-26
im not really familair with .divx. its not used very often from my experience. you might find it easier to extract the subtitles out of the divx container

---

### Post by mortasa on 2009-03-26
Setting srt subtitle file in out side of the .divx file with same name of video file is working for me well. MPlayers' subtitle font is coming very large. But it is working well with vlc player. You better try this way.
:guitar:

---

### Post by Vahids on 2009-03-26
i need a way to see subtitle of .divx move not any other subtitle! no way ?!!!! :(
i love ubuntu, but this problem F#CKED ME!!!!!!!!!! :((

---

### Post by hatalar205 on 2009-04-25
First follow the steps in following link and install necessary codecs.
**[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)**

Next, **install "smplayer"**
and (as the smplayer version in repos are really old) follow the steps in this link
**[https://launchpad.net/~rvm/+archive](https://launchpad.net/~rvm/+archive)**

**Update your system.**

When I had 8.10 Intrepid Ibex, I could watch any kind of films in different formats with subtitles.

---

