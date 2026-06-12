---
title: "A player that handles WMA in Ubuntu 7.04?  XMMS Questions.. Amarok help.."
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by Elotero on 2007-06-20
The default player ( i dont know what it is) played all my collection fine.. i loaded over a hundred songs.. but when the player got to a song that was WMA it stopped stating that it wasnt compatible with WMA songs.. thats cool.. is there a player that can handle it?? I use my laptop for music mainly... im big on Soulseek so of course i got Nicotine Plus working quickstyle.. But any help as far as a good steady media player would help.. 

 I tried XMMS because somwhere someone mentioned its alot like Winamp (which was my player of choice in Windows) but when i try to load my collection i cant find it.. My collection is in a removeable hard drive on my desktop.. in the add music feature of XMMS i cant find my USB.. cant find my music.. can anyone help out?? 

In Amarok i found my removable storage and tried to load a gig or so of music.. the system froze on me.. Amarok was just loading for about 15 minutes.. finally i said forget it and cold booted my laptop... i heard alot of good things about Amarok.. but that kind of killed it.. did i load too much at one time?? Winamp used to be able to handle that with no problems.. Windows Media Player too... 

You guys are probably the best community out there.. thanks for all your help..

---

### Post by boldexplorer on 2007-06-20
HI there,
I had the same problem until I tried playing a WMA video file in Movie  Player (Ubuntu Feisty standard). Although the format was not recognised the play searched for the codecs to run WMA files. 
Now Amarok and Movie Player both handle WMA audio well but occasionally not video. 
I hope that this helps!
Cheers

---

### Post by Elotero on 2007-06-20
> **boldexplorer said:**
> HI there,
I had the same problem until I tried playing a WMA video file in Movie  Player (Ubuntu Feisty standard). Although the format was not recognised the play searched for the codecs to run WMA files. 
Now Amarok and Movie Player both handle WMA audio well but occasionally not video. 
I hope that this helps!
Cheers

Not bad.. i have some WMV videos. i will try running them later and let you know how it goes.. thank you for the tip!!!

---

### Post by Tautoa on 2007-06-22
Don't know if it will apply to your problem (Amarok crash), but when it was running slowly for me, I found that getting it to use MySQL sped things up a lot, havn't had a crash since.

Instructions for using Amarok with MySQL at the URL below

[http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

---

### Post by peetbull on 2007-10-03
I personally prefer XMMS because it's the player I met first in my Linux (relatively short) experience.

So, this very morning I wanted to play some WMA songs a friend gave me and XMMS didn't support it by default.

So the solution for this issue was a 2-step process, given that I already had XMMS installed.

_Step 1:_ installation via apt-get

- Open a terminal (gnome-terminal or something).

- Type: ```
sudo apt-get install xmms-wma
``` press "enter" and give the super user password

_Step 2:_ locate and play my WMA file

- Find the file your interested in listening to

- Open XMMS

- Simply, drag and drop your file from the file browser in XMMS.

- Press "play" button


Enjoy!

---

