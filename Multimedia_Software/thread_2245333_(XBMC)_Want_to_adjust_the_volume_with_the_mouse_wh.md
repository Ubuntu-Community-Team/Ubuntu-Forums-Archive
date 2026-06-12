---
title: "(XBMC) Want to adjust the volume with the mouse wheel"
date: 2014-09-22
forum: Multimedia Software
---

### Post by linuxyogi on 2014-09-22
I want to use the mouse wheel to adjust volume in XBMC.

I found these 2 solutions but none worked.

[Solution 1]("http://forum.xbmc.org/showthread.php?tid=122795&pid=1017161#pid1017161")

[Solution 2]("http://followthegeeks.com/how-to-change-mouse-wheel-function-in-xbmc/")

```
$ xbmc --version
XBMC Media Center 13.2 Git:0f3db05
Copyright (C) 2005-2013 Team XBMC - http://xbmc.org

```

Is there a way to do this in 13.2 ?

---

### Post by shantiq on 2014-09-23
ok yogi   took a bit of time but got there ....   myself on Ubuntu 14.04

and using xbmc 13.2


first to open:

```
sudo gedit /usr/share/xbmc/system/keymaps/**mouse.xml**
```


and then to replace with:   added lines are in brown



```
<?xml version="1.0" encoding="UTF-8"?><keymap>
  <global>
    <mouse>
      <leftclick>leftclick</leftclick>
      <middleclick>middleclick</middleclick>
      <rightclick>rightclick</rightclick>
      <doubleclick>doubleclick</doubleclick>
      <wheeldown>wheeldown</wheeldown>
      <wheelup>wheelup</wheelup>
      <mousedrag>mousedrag</mousedrag>
      <mousemove>mousemove</mousemove>
    </mouse>
  </global>
[COLOR=#800000]
 <!-- Full Screen Video Controls -->[/COLOR]
[COLOR=#800000]  <FullscreenVideo>[/COLOR]
[COLOR=#800000]    <mouse>[/COLOR]
[COLOR=#800000]      <wheelup>VolumeUp</wheelup>[/COLOR]
[COLOR=#800000]      <wheeldown>VolumeDown</wheeldown>[/COLOR]
[COLOR=#800000]    </mouse>[/COLOR]
[COLOR=#800000]  </FullscreenVideo>[/COLOR]
[COLOR=#800000]  <!-- Video On-Screen-Display Controls -->[/COLOR]
[COLOR=#800000]  <VideoOSD>[/COLOR]
[COLOR=#800000]    <mouse>[/COLOR]
[COLOR=#800000]      <wheelup>VolumeUp</wheelup>[/COLOR]
[COLOR=#800000]      <wheeldown>VolumeDown</wheeldown>[/COLOR]
[COLOR=#800000]    </mouse>[/COLOR]
[COLOR=#800000]  </VideoOSD>[/COLOR]
[COLOR=#800000]  <!-- Music Visualization Controls -->[/COLOR]
[COLOR=#800000]  <Visualisation>[/COLOR]
[COLOR=#800000]    <mouse>[/COLOR]
[COLOR=#800000]      <wheelup>VolumeUp</wheelup>[/COLOR]
[COLOR=#800000]      <wheeldown>VolumeDown</wheeldown>[/COLOR]
[COLOR=#800000]    </mouse>[/COLOR]
[COLOR=#800000]  </Visualisation>
[/COLOR][COLOR=#800000]<!-- Music On-Screen-Display Controls -->[/COLOR]
[COLOR=#800000]  <MusicOSD>[/COLOR]
[COLOR=#800000]    <mouse>[/COLOR]
[COLOR=#800000]      <wheelup>VolumeUp</wheelup>[/COLOR]
[COLOR=#800000]      <wheeldown>VolumeDown</wheeldown>[/COLOR]
[COLOR=#800000]    </mouse>[/COLOR]
[COLOR=#800000]  </MusicOSD>[/COLOR]
[COLOR=#800000]
[/COLOR][COLOR=#800000]<!-- Home On-Screen-Display Controls (Master List for movies/music/etc) -->[/COLOR]
[COLOR=#800000]  <Home>[/COLOR]
[COLOR=#800000]    <mouse>[/COLOR]
[COLOR=#800000]      <wheelup>VolumeUp</wheelup>[/COLOR]
[COLOR=#800000]      <wheeldown>VolumeDown</wheeldown>[/COLOR]
[COLOR=#800000]    </mouse>[/COLOR]
[COLOR=#800000]  </Home>
[/COLOR]
  [COLOR=#800000]<!-- Picture Slideshow Controls -->
  <SlideShow>
    <mouse>
      <leftclick>Pause</leftclick>
      <rightclick>PreviousMenu</rightclick>
      <wheelup>PreviousPicture</wheelup>
      <wheeldown>NextPicture</wheeldown>
    </mouse>
  </SlideShow>[/COLOR]

</keymap>
```


all thanx to info from[ this post]("http://forum.xbmc.org/showthread.php?tid=171647&pid=1487745#pid1487745")


**PS** XBMC   is so good    when videos flicker on VLC or mpv they rmain stable on xbmc ...

---

### Post by linuxyogi on 2014-09-23
Awesome ! It worked. Since you are also using 13.2 I simply deleted whatever was on that file and replaced it with yours.

---

