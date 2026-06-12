---
title: "Problem with Mplayer and Full Screen"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by phoenix7 on 2007-06-23
I use a wide screen lcd panel. I've installed mplayer and gmplayer 
(using apt-get from standard ubuntu repositories)
When I press F key to change the program to full screen it changes to full screen but
It does not change the movie show size, just adds big black margins to the movie!
How can I fix it?

Thanks,

---

### Post by taurus on 2007-06-23
Edit ~/.mplayer/config

Applications -> Accessories -> Terminal
```
gedit ~/.mplayer/config
```
and add this line to the end of it.

```
zoom=yes
```
Save it and run MPlayer again and see if the fullscreen works now.

---

### Post by jerrykun on 2007-06-26
hey man i have the save problem this post fixes my full screen but i still cant use non of my other video players. i ran vlc thru the terminal and i get this:

VLC media player 0.8.6 Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  87
  Current serial number in output stream:  88


if you have a fix help me out here please many thanks

---

### Post by phoenix7 on 2007-06-27
Thanks taurus, 

that fixed the problem!

---

