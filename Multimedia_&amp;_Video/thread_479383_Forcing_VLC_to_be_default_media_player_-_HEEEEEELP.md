---
title: "Forcing VLC to be default media player - HEEEEEELP!!!!!"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by bagrol1 on 2007-06-20
I've been struggling with this seemingly simple thing, but cannot find a solution.

**Problem**
I have a paid video subscription over the net which broadcasts file as streaming wmv files. I found that these files can be viewed by vlc player, but not by the default Totem player.  When I click the link to a wvm file, Totem is automatically launched but is not able to play the file. To see the file I need to manually copy the file path from Totem and paste it into vlc.

**Solution Trials**
1. Tried clicking on a local wmv file and changing it properties to be open by vlc player.  It does not work for streaming files.  Totem still is the default.
2. Installed some extension plugin into Firefox for windows media in which all the media files can be linked to specific player. It does NOT work as I think at the site with links to wmv files Firefox does not recognize them or something and Totem still launches.
3. Tried to get rid of Totem, but got warning that removing it would also remove gstreamer codecs.
4. WHAT ELSE CAN I TRY????? Is there registry in Linux or some configuration text file where I could make Ubuntu forget that Totem even exists????
5. Or maybe there is a way of making Totem work with wmv files???

Please help!!!

---

### Post by RomeReactor on 2007-06-20
Hi. You need to install the **w32codecs** to enable Totem to play .wmv videos, if you haven't already. If you have the [Medibuntu]("https://help.ubuntu.com/community/RestrictedFormats#head-17f9569280643c3d657d7df670f44c448c95c4fb") repositories, you'll find the codecs through Synaptic; or, from the terminal:
```
sudo apt-get install w32codecs
```

---

### Post by Gremlinzzz on 2007-06-20
What i have too do to setup mplayer first i uninstall totem and its plugin.
then i get the deb package for smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/) plays my dvd movies.
Then i install mplayer plugin using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/Re...t=%28codecs%29](https://help.ubuntu.com/community/Re...t=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
last but not least i test mplayer plugin at [http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
if its gray i config the settings by right clicking the video window and choose X11 video &ALSA audio
Thats it and it works great i can watch dvd movie cds and divxs movies and streaming video.
these are the setup tweaks i learned for mplayer i could not find tweaks that match em for totem.

---

### Post by Gremlinzzz on 2007-06-20
You should remove VLC if you try mplayer cause they most likely would bump heads.

---

### Post by bagrol1 on 2007-06-20
It works!!!!!!!!!!!!!!!!!!!!!!!!  I installed Totem-xine and it works!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

