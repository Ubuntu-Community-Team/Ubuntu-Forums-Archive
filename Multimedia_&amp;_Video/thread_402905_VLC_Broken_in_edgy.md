---
title: "VLC Broken in edgy"
date: 2007-04-06
forum: Multimedia &amp; Video
---

### Post by Benjamin2 on 2007-04-06
Hi,

I installed the VLC package from the universe repository, but it is broken.
When I call vlc, it prints the following error:

```
VLC media player 0.8.6 Janus
[00000020] main interface error: no interface module matched "hotkeys,none"
[00000020] main interface error: no suitable interface module
[00000001] main vlc error: interface "hotkeys,none" initialization failed
[00000021] main interface error: no interface module matched "screensaver,none"
[00000021] main interface error: no suitable interface module
[00000001] main vlc error: interface "screensaver,none" initialization failed
[00000022] main interface error: no interface module matched "any"
[00000022] main interface error: no suitable interface module
[00000001] main vlc error: interface "(null)" initialization failed

```

---

### Post by mardson on 2007-04-13
I ran into the same issue this morning. After some apt-get magic, it started working.

I specifically remember doing these moves ...

sudo apt-get remove vlc
sudo apt-get update (twice)
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get install vlc


... i'm sorry for this lame reply, but after all that it magically started working. best of luck! :(

---

