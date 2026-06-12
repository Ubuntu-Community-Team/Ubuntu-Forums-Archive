---
title: "Video Playback - Black Screen"
date: 2011-08-19
forum: Multimedia Software
---

### Post by vivekratnavel on 2011-08-19
I upgraded from 10.10 to 11.04 three months back. Suddenly I am not able to view any video files in any of my players. I tried VLC, M player, Kaffeine and Movie Player, but every player behaves the same. I see a black screen with only audio. Any help is appreciated. Thanks.

---

### Post by axredneck on 2011-09-15
When i installed Kaffeine i also had only audio without video... but after just Reboot all became working...

---

### Post by gawryl77 on 2011-09-27
have you solved your problem?

if no, try to start mplayer (in terminal) with a parameter:    -vo x11   (or -vo vdpau, if you have installed vdpau drivers; or other video output drivers, try one of those listed in output of mplayer -vo help).

---

### Post by vivekratnavel on 2011-09-30
I still get the black screen when playing videos. I figured out that am able to play videos smoothly when I login to Unity but when I login to Gnome, I get this black screen. So, it is clearly a problem with gnome. Mine is version 2.32.1

---

### Post by vivekratnavel on 2011-09-30
I tried to start mplayer with parameters from the terminal and the video played, but the size was small and not resizeable. I was not able to control any aspect of the video. But, the video played :)

---

