---
title: "VLC problems (lots of them)"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by kung fu buntu on 2007-06-26
I downloaded a couple of skins (.vlt files) and put them in ~/.vlc/skins/

1) When I open a file VLC starts with its default (wx11?) fugly skin. Even though I have the line:
skins2-last=/home/kaizoku/.vlc/skins2/DefaultRemix.vlt
in my vlcrc config file.

2) Trying to switch between skins is a nighmare because CTRL+S only works when he wants to... I have to press about 10 times before the menu pops up ](*,)

3) When I'm finally able to switch to another skin the video window detaches itself from the controls window ](*,)

Any help on this? [-o<

BTW: VLC 0.8.6

---

### Post by kung fu buntu on 2007-06-27
> **kung fu buntu said:**
> I downloaded a couple of skins (.vlt files) and put them in ~/.vlc/skins/

1) When I open a file VLC starts with its default (wx11?) fugly skin. Even though I have the line:
skins2-last=/home/kaizoku/.vlc/skins2/DefaultRemix.vlt
in my vlcrc config file.
As a user I used kcontrol to override my file association settings for video files regarding VLC. This created the file **~/.local/share/applications/vlc.desktop**. I edited this file to have **wxvlc -I skins2** instead of wxvlc.

> **kung fu buntu said:**
> 2) Trying to switch between skins is a nighmare because CTRL+S only works when he wants to... I have to press about 10 times before the menu pops up ](*,)
Still trying to figure this bug out...

> **kung fu buntu said:**
> 3) When I'm finally able to switch to another skin the video window detaches itself from the controls window ](*,)
It's in a so-called full screen mode, which isn't really full screen because I can see the window's border :(
Pressing "f" attaches the video window back.
I wonder if there is really a way to set a real fullscreen...

---

