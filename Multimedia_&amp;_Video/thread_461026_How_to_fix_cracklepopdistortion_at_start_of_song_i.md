---
title: "How to fix crackle/pop/distortion at start of song in Amarok"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by geoff123 on 2007-06-01
When manually changing songs in Amarok I was getting an annoying crackle/pop/distortion sound in the first microsecond of starting a song in gnome. This is what fixed it for me - I hope it helps others. 

Assuming you are running gnome desktop:

-Set Amarok engine settings to 'xine Engine' and Output plugin to 'esd'. 
-Make sure you have the libxine1-gnome package installed
-In the gnome desktop make sure ESD is running: System > Preferences > Sound >Sound needs to have "Enable software sound mixing (ESD)". 
-Try it to make sure it works, then re-start amarok.

[I'm assuming if you use kubuntu you will set output plugin to 'arts' and make sure arts is running].  

I'm guessing that this is related to re-initializing the output to alsa (original output plugin) at each song since the sound was not present when it automatically changed tracks.  Might this be an Amarok or Xine or Alsa bug?

Note that this is for Feisty.

---

### Post by chefboyjames on 2008-01-01
wow,wow,wow,wow,so simple to fix but for a newb like me I've dealing with that crackle for weeks, thanks soooooooooooo much man

---

