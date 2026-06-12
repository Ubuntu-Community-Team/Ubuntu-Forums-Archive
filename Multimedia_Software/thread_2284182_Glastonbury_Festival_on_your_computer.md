---
title: "Glastonbury Festival on your computer"
date: 2015-06-27
forum: Multimedia Software
---

### Post by shantiq on 2015-06-27
Your computer needs to be in the UK

then

```
get_iplayer --stream --type=livetv "BBC One" --player="mplayer -cache 512 -"
get_iplayer --stream --type=livetv "BBC Two" --player="mplayer -cache 512 -"
get_iplayer --stream --type=livetv "BBC Three" --player="mplayer -cache 512 -"
get_iplayer --stream --type=livetv "BBC Four" --player="mplayer -cache 512 -"
```

or place this in your .bashrc

```
alias BBC1='get_iplayer --stream --type=livetv "BBC One" --player="mplayer -cache 512 -"'
alias BBC2='get_iplayer --stream --type=livetv "BBC Two" --player="mplayer -cache 512 -"'
alias BBC3='get_iplayer --stream --type=livetv "BBC Three" --player="mplayer -cache 512 -"'
alias BBC4='get_iplayer --stream --type=livetv "BBC Four" --player="mplayer -cache 512 -"'
```

then ```
. ~/.bashrc
```   use mpv if you have

then call from terminal


BBC1 , BBC2 etc

---

### Post by coldraven on 2015-06-28
Thanks, that is neat. Ooops! I don't have a TV license :( <goes back to viewing pre-recorded shows>

---

### Post by shantiq on 2015-06-28
... of which there are [so many]("http://www.bbc.co.uk/iplayer/episodes/b007r6vx")  Cold One 
The Waterboys were outofthisworld!!
ps    and yes a licence

---

### Post by coldraven on 2015-06-28
Ah! Waterboys! I used to have one of their albums on vinyl (In about 1987) I must check out the iPlayer later. I'm having a "Life without Adobe Flash" discussion on another thread in the Cafe at the moment, it might be installed again by this evening. :)

---

