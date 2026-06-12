---
title: "How to know which mplayer is which mplayer in the file system"
date: 2009-03-02
forum: Multimedia Software
---

### Post by sofasurfer on 2009-03-02
There are 4 movie players on my system. 
1) Totem... I can tell by the name at the top of the open player window
2) Gnome MPlayer... I can tell by the same method
3) Movie Player (Gstreamer)... 
4) MPlayer Movie Player... Its my favorite because it has an equalizer

Question...
Are all of these a differant player?

There is a .mplayer file in /user directory and a mplayer directory in /etc. The one in /user is for the one that displays my DVB because it has the channels.conf.atsc file. But I don't know which player it is. The one in /etc I have no idea.

Basically, how do I differentiate them in the file system? Why are there so many with the same name but no clue as to how to tell them apart?

---

### Post by andrew.46 on 2009-03-02
Hi sofasurfer,

> **sofasurfer said:**
> 
1) Totem... I can tell by the name at the top of the open player window
2) Gnome MPlayer... I can tell by the same method
3) Movie Player (Gstreamer)... 
4) MPlayer Movie Player... Its my favorite because it has an equalizer


1) Totem is the official movie player of the GNOME desktop environment. Details can be [seen here]("http://projects.gnome.org/totem/"). 

2) Gnome MPlayer is a front-end for MPlayer. Details can be [seen here]("http://kdekorte.googlepages.com/gnomemplayer"). 

3) 'Movie Player (Gstreamer)' I suspect is the same as the 1st on your list?

4) MPlayer is the media player that is behind the Gnome MPlayer frontend. Details can be [seen here]("http://www.mplayerhq.hu/design7/news.html"). To see an equalizer you must be using a gui with it possibly gmplayer?

I agree, too many programs trying to use the same name can only create confusion. Mind you there are other media players. You have left out vlc for example which is a very capable player and well worth a try.

Andrew

---

