---
title: "Video and slight sound problem"
date: 2005-10-14
forum: Multimedia &amp; Video
---

### Post by Kimm on 2005-10-14
OK, after upgrading to hoary I got some trubble with graphics, its an Onboard Intel graphics card, dont know the model, but it uses the i810 driver. It worked fine in Hoary where I could run games in cedega and wine without any real trubble, but now the games lagg something terrible. Starcraft and Stratagus/Invasion works though, but I supose thats since they need less graphics.

The slight sound problem isnt that big, but its rather anoying. If I kill the x-server and restart it, sound stops working and esd refuses to start, complaining about alsa, I'll give you more details when It happens again.

can anyone help?

---

### Post by mlomker on 2005-10-14
Have you tried **sudo dpkg-reconfigure xserver-xorg** to walk through the video driver selection again?

---

### Post by Kimm on 2005-10-15
didnt realy make much of a differance :(

---

