---
title: "Streaming problem"
date: 2009-01-09
forum: Multimedia Software
---

### Post by hasp on 2009-01-09
[SIZE="4"][FONT="Arial"]Everytime I stream a video online there is audio but no video ( Black screen) Sometimes there is video but if i press pause or fast forward the black screen comes again.
First I used Mplayer plugin then I tried Gecko but neither works. 
Sorry if this is common but ive searched all the forums.
When the video plays I go to preferences and change the video output but this still does nothing. 
Desperate for help!!???

Thanks in advance[/FONT][/SIZE]

---

### Post by tuxxy on 2009-01-09
If its a fresh installation you may want to first install ubuntu-restricted-extras package which provides many codecs and should solve your issue.


Search for  ubuntu-restricted-extras using Synaptic or type in terminal

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by hasp on 2009-01-10
I typed that into terminal and it said I already had the latest version. Thanks for the help. 
Any more suggestions?

---

### Post by AlanR8 on 2009-01-10
I always install the following with the command below:

> sudo apt-get install flashplugin-nonfree mozilla-mplayer vlc


The Mozilla-MPlayer plug-in is all I need on top of Flash to play 99% of all InterWeb media

---

