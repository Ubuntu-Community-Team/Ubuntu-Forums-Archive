---
title: "White Video appears Gray in gutsy on Intel Graphics"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by mridkash on 2007-11-02
Recently I stumbled upon a strange problem, white colored videos appear gray when played. 

Screenshot:
[IMG]http://home.mridul.googlepages.com/image.jpg[/IMG]

I came to know of it when using Blender to edit videos. While rendering it showed white background and when played, gray. Then I confirmed this issue by making a white colored clip in Kdenlive which when played in totem or any other player showed up as gray. You can see it in the screenshot.

I'm using Ubuntu Gutsy on laptop with Intel integrated graphics. 

Check if the attached video appears white or gray on your pc. 
[White video link]("http://home.mridul.googlepages.com/untitled.flv")

---

### Post by FrederikNS on 2007-11-28
Exactly the same here, but also almost all color has gone

ain't much fun watching everything in almost grayscale.

EDIT: Seems i fixed it... but only for vlc player.
The problem seems to be that the "XVideo extension video output" outputs grey video, if I go into vlc->edit->preferences->video->output modules, tick the advanced options box, and switch the output module to x11, and restart the program, i get the correct colors again.

It also seems as if it's a common error for the "xine" users: [http://www.xinehq.de/index.php/faq#CONTRASTBRIGHTNESSSATURATION](http://www.xinehq.de/index.php/faq#CONTRASTBRIGHTNESSSATURATION)

---

### Post by Rumo on 2007-11-28
This is probably related to [ this ]("https://bugs.launchpad.net/bugs/32963") bug (it's not restricted to totem player).

---

