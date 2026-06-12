---
title: "installed mplayer, plugins, codecs and remove totem still can't see anything"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by parvez on 2007-07-13
hi
I have installed mplayer, plugins, codecs and remove totem still can't see anything. Its showing me black screen and no video on firefox. I have installed fresh ubuntu 7.04. Can anybody help me PLEASE!!!!!!. thanks

---

### Post by Waappu on 2007-07-13
Hi

See if this helps
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_do_I_fix_black_windows_during_video_playback](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_do_I_fix_black_windows_during_video_playback)

You can found other useful tips to install codecs and media players from same page

---

### Post by Gremlinzzz on 2007-07-13
What i have too do to setup mplayer first i uninstall totem and its plugin.
then i get the deb package for smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/) plays my dvd movies.
Then i install mplayer plugin using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
last but not least i test mplayer plugin at [http://www.hogsbreath.com/hogcam/](http://www.hogsbreath.com/hogcam/)
if its gray i config the settings by right clicking the video window and choose X11 video &ALSA audio
Thats it and it works great i can watch dvd movie cds and divxs movies and streaming video.
these are the setup tweaks i learned for mplayer i could not find tweaks that match em for totem.

---

### Post by trak87 on 2007-07-13
> **parvez said:**
> hi
I have installed mplayer, plugins, codecs and remove totem still can't see anything. Its showing me black screen and no video on firefox. I have installed fresh ubuntu 7.04. Can anybody help me PLEASE!!!!!!. thanks

Are you running it from the command line? Run this:

```
mplayer -vo help
```

You'll get a bunch of video options. Then, for example, pick one of the video options (like vesa,xv,x11,gl2) and try to play a video file with it:

```
mplayer -vo vesa filename.avi
mplayer -vo xv filename.avi
mplayer -vo x11 filename.avi
mplayer -vo gl2 filename.avi
etc.

```

Does anything work?

---

### Post by BobLand on 2007-07-13
I've had similar problems and was ready to give it up.  Then I found a post about SMPlayer.  Installed it.  It did all the work with codecs and plugins.  The short story is it worked the first time for everything.  No more totem.

If you want to default files to smplayer open /etc/gnome/defaults.list.  FInd the video files you want to default to and change them to smplayer.

Removes all of the headaches.

bobland

---

