---
title: "Karmic 9.10 Intel GM965 Performance Issues"
date: 2010-02-07
forum: Multimedia Software
---

### Post by WhiteHorse on 2010-02-07
My Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) has terrible 2D and 3D performance. I first noticed that recent updates have caused my videos to stutter and my desktop interface is very slow to respond to clicks and to display menus.

Everything seemed ok until recently except for games like Nexuiz and Cube 2 - Sauerbraten wouldn't work at all. So... I followed the instructions in the Jaunty Intel Graphics guide but replaced the jaunty apt lines with karmic. All the updates ran and my system is now loading videos and the gui without any hesitation. Honestly, the system is doing much better. 

My system was a totally clean install of 9.10. This is the first time I've modded the graphics and it seems to be much better. I still get only 12fps in Cube2, 15fps in Nexuiz, and 30fps in the penguin racer game. Am I missing something? I thought this was all fixed? Is this the maximum performance I can expect from this video chipset? I seem to remember getting much better performance under windows xp. Any Ideas? Thoughts? I can't find jack in the forums.

---

### Post by SlickRick on 2010-02-11
I've got a GM965 and it's terrible but you can't expect much performance from something like this. Most linux games run OK and I'm happy but you can forget about running any of the latest games. In Vista it does worse since I can't play anything that's more than a couple of years old. Even if the required video ram is enough, most games run really slow for some reason. To be honest that's really weird, like there's something blocking it's full potential. So I don't think there's anything more you can do. It's the chipset at fault and not the drivers.

btw... I've tried that guide with jaunty and it sped things up a bit. I've got karmic now and will be doing it again, since you say all it takes is replacing the apt lines.

---

### Post by WhiteHorse on 2010-02-11
I didn't use the fixmtrr.sh script and I tried the xorg.conf additions. At least now the games do run albeit rather slow.

---

