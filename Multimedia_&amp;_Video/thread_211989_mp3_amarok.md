---
title: "mp3 amarok"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by 7he on 2006-07-09
Hi everybody!

since the last update of some codecs (about 2 days ago) Amarok can't play mp3 anymore although the default ubuntu multimedia reader can! 
When I open Amarok, I get the following warning:

[FONT="Arial"]
[COLOR="Sienna"]The xine-engine claims it cannot play MP3 files.
You may want to choose a different engine from the Configure Dialog, or examine the installation of the multimedia-framework that the current engine uses. 
You may find useful information in the FAQ section of the amaroK HandBook.[/COLOR][/FONT]

If I understand, Amarok uses xine-engine to play mp3 and xine can't play them . Am I wrong? 
Can someone explain me how to make it possible playing mp3 in Amarok? 

Thank you very much

---

### Post by Rackerz on 2006-07-09
Have you tried going into Synaptic and removing amaroK and the xine packages that it uses and then re-installing them?

---

### Post by tommohawk on 2006-07-09
I would just try and get hold of the new version of Amarok 1.4

Mine worked out of the box with mp3, iPod and all.

---

### Post by gils0040 on 2006-07-09
try
sudo apt-get install libxine-extracodecs

---

### Post by harishg on 2006-07-09
Install the codecs using easyubuntu

---

### Post by wildseven on 2006-07-11
With easyubuntu, after installing and running, I chose what I wanted to be installed and I got a pop warning. Installing unknown files or something about security. Is it ok if i clicked ok?

---

