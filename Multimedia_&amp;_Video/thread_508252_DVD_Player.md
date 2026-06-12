---
title: "DVD Player"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by Matthew Wiebelhaus on 2007-07-24
What is the best dvd player for Ubuntu and what codecs do i need to install for it?

---

### Post by Matthew Wiebelhaus on 2007-07-24
Ive got my codecs i just want a good player please help me

---

### Post by RomeReactor on 2007-07-24
Hi. I would say Totem is very good at handling DVDs when correctly set up; another one would be VLC. Totem's got my vote, though.

---

### Post by Gremlinzzz on 2007-07-24
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
:guitar:

---

### Post by Gremlinzzz on 2007-07-24
> **Gremlinzzz said:**
> What i have too do to setup mplayer first i uninstall totem and its plugin.
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
:guitar:

oh yeah change your video in the smplayer too x11 if you use beryl it wont black out

---

### Post by misfitpierce on 2007-07-24
Totem standard movie player is prob the best. Automatix can install the codecs for you if you need them. VLC is also great and has most codecs inside it and is lightweight on resources.

---

### Post by Matthew Wiebelhaus on 2007-07-24
Thanks guys i think i like vlc the best

---

