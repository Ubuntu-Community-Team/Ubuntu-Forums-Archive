---
title: "Kaffeine Won't Load in Gnome"
date: 2006-11-30
forum: Multimedia &amp; Video
---

### Post by taddy_porter on 2006-11-30
Using Edgy with latest upgrades.

I was successfully using Kaffeine-Xine. I rebooted and now it refuses to load in Gnome. Works fine in KDE though.

I tried running through the terminal but it does nothing.

taddy@taddy1:~$ kaffeine
taddy@taddy1:~$ 


I tried completely removing and reinstalling but it didn't help. To my knowledge I didn't do any installs since I rebooted (but I don't remember when I rebooted last).

Strangely if I use Konqueror and select "preview in Kaffeine-Xine" it loads just fine.

GXine works fine too.

Got any ideas?

The only other thing I've noticed is that XV is the default video driver, but it gives a black screen with just audio. Switching to opengl gave me a video.

---

### Post by taddy_porter on 2006-12-01
This is surely a Gnome issues. Works fine in E17 and KDE. 

Any help would be appreciated.

---

### Post by taddy_porter on 2006-12-01
I seem to have fixed this.

I needed to remove the dcopserver and run kdeinit.


Thanks for all the help.

---

