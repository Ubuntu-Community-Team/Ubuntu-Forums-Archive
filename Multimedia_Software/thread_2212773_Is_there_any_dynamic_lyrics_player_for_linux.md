---
title: "Is there any dynamic lyrics player for linux?"
date: 2014-03-23
forum: Multimedia Software
---

### Post by mynonrealemail on 2014-03-23
I know there is software called [OsdLyrics]("http://code.google.com/p/osd-lyrics/"), but it's not developing. It does not work on 13.10. Its latest update is for quantal :(
Is there any else software that resembles closely to Minilyrics (=lyric finder and viewer for windows)?

---

### Post by shantiq on 2014-03-23
```
sudo apt-get install libmpd1 ; wget https://osd-lyrics.googlecode.com/files/osdlyrics_0.4.3-1~precise1_amd64.deb  &&  sudo dpkg -i osdlyrics_0.4.3-1~precise1_amd64.deb
```


Hi [COLOR=#000000][mynonrealemail]("http://ubuntuforums.org/member.php?u=1881425") [/COLOR]this will install it on Saucy just copy line in terminal and enter password   and thnx never heard of it before really nice :]

---

### Post by mynonrealemail on 2014-03-23
@[[IMG]http://ubuntuforums.org/customavatars/avatar870500_30.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=870500") 				 				 					 						 	[**[COLOR=#000000]shantiq[/COLOR]**]("http://ubuntuforums.org/member.php?u=870500"),

It is installed, but Unfortunately it does not work on Sausy while it worked on Quantal. It can not fetch lyrics on Sausy and its "osd" mode does not work.

Any else software?

---

### Post by shantiq on 2014-03-23
-----------------------

---

### Post by shantiq on 2014-03-23
[ATTACH=CONFIG]251393[/ATTACH]


got it going .... had to start Audacious first here then allow some of the plugins [not sure if needed]

then start osdlyrics in that order ... maybe try that

---

### Post by mynonrealemail on 2014-03-24
@shantiq
1. OsdLyrics does not work on 13.10 anyway, at least it does not work here. In fact, as I said, it runs but can't fetch anything. :(
2. In your attached picture -> left-top side -> what is it: ***Osdlyrics*** or ***Aaudacious feature***?

---

### Post by shantiq on 2014-03-24
[I]Osdlyrics   of course    otherwise why would i bother to put it up :]

av you tried to run Audacious with [/I]*Osdlyrics the way i explained...    all i can say is that it is running here on 13.10; so it can be done clearly  ....    anyway best of luck*

---

### Post by mynonrealemail on 2014-03-24
Oops. It seems there is a problem on OsdLyrics trunks for me. look at the attached picture. Audacious could fetch the lyric for  **Janitor of Lunacy - Nico, **but OsdLyrics couldn't find it in its repositories (ttplayer & Xiami).

---

### Post by shantiq on 2014-03-24
osdlyrics found it here there must be something not installed yet on your system   ...    finding out what it is is the question here   ...    sadly i do not know what it might be  ...   someone else might
    
best of luck

---

