---
title: "Shoutcast Explorer _ Listen and record shoutcast radios stations"
date: 2013-10-13
forum: Multimedia Software
---

### Post by 3nitysoftwares on 2013-10-13
[FONT=arial][SIZE=2]hi 

i'm here to present Shoutcast Explorer in 2nd version 

[COLOR=#555555]Shoutcast Explorer is a small Open Source browser and player  for shoutcast radios stations.[/COLOR]

[COLOR=#555555]it find radios stations by genre , download radios stations playlists (.PLS Files Extensions) and open the default associated program for .Pls files types to start the listening.
[/COLOR]
added in version 2:

[COLOR=#555555]was added :[/COLOR]
[/SIZE][/FONT][COLOR=#555555][FONT=Helvetica Neue][FONT=arial][SIZE=2]*embedded media player
*record function ( using streamripper )
*save and load playlists
*streams vu meters
*the program shows the playing stream title[/SIZE][/FONT]

[/FONT][/COLOR]
[CENTER][COLOR=#555555][FONT=Helvetica Neue][IMG]http://3nitysoftware.com/images/shoutcast.jpg[/IMG]
[/FONT][/COLOR][COLOR=#555555][FONT=Helvetica Neue][http://sourceforge.net/projects/shoutcastexplor/](http://sourceforge.net/projects/shoutcastexplor/)
[http://3nitysoftware.com/shoutcastexplorer.html](http://3nitysoftware.com/shoutcastexplorer.html)[/FONT][/COLOR][/CENTER]
[COLOR=#555555][FONT=Helvetica Neue]

[/FONT][/COLOR]
**How to install Shoutcast Explorer version 2 on Ubuntu/Xubuntu/Lubuntu (Amd64 version (64bits))
***********************************************************************


open a terminal (or bash) :


```
wget --output-document=shoutcastexplorer.deb http://sourceforge.net/projects/shoutcastexplor/files/Shoutcast%20Explorer%20v2/shoutcastexplorer_2.0.1.39_amd64.deb/download && sudo dpkg -i shoutcastexplorer.deb && sudo apt-get -f install

```



**How to install Shoutcast Explorer version 2 on Ubuntu/Xubuntu/Lubuntu (i386 version (32bits))
***********************************************************************




```
wget --output-document=shoutcastexplorer.deb http://sourceforge.net/projects/shoutcastexplor/files/Shoutcast%20Explorer%20v2/shoutcastexplorer_2.0.1.39_i386.deb/download && sudo dpkg -i shoutcastexplorer.deb && sudo apt-get -f install

```



**To Remove the program:
************************


```
sudo dpkg -r shoutcastexplorer

```



**Notes : to record stations , the program uses streamripper : 
**************************************************************


to install streamripper you need the universe repository activated


and enter in a bash :


```
sudo apt-get install streamripper

```

[COLOR=#555555][FONT=Helvetica Neue]
[/FONT][/COLOR]

---

