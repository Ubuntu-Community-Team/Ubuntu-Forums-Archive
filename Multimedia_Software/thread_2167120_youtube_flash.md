---
title: "youtube flash"
date: 2013-08-12
forum: Multimedia Software
---

### Post by d.khatri on 2013-08-12
i am unabel to view videos on youtube and in ubuntu youtube flash player seems kinda different type apart from window that i used to. i have uploaded a pic of that ! please help what am i suppose to do?

---

### Post by GwL3eNC on 2013-08-12
Hi,

i would first try a reinstallation of flash plugin. You can download a debian file here [http://get.adobe.com/de/flashplayer/](http://get.adobe.com/de/flashplayer/)
With sudo dpkg -i DOWNLOADFILENAME.DEB you can install the file. 

Or you can try 

sudo apt-get update
sudo apt-get install --reinstall flashplugin-installer 

for the multiverse package or

sudo apt-get update
sudo apt-get install --reinstall adobe-flashplugin

for the canonical package.

I hope this solves your problem.

---

### Post by Gilad_Pellaeon on 2013-08-12
Also if that doesn't work you can install Google Chrome which has it's own pepperflash support built in and has working hardware acceleration especially on older computers like mine where the Adobe flash plugin falls flat on it's face so to speak trying to play flash games and video sometimes.

---

