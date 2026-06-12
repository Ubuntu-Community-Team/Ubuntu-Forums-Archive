---
title: "Changing default DVD player"
date: 2008-07-17
forum: Multimedia Software
---

### Post by tripwire45 on 2008-07-17
I really don't like Totem and would prefer to have Xine launch when I put a DVD in my optical drive. As it is now, I wait until Totem launches, kill it, then launch Xine manually. I've searched (but apparently not well enough) but can't find out how to change the default movie player.

I've gone into System -> Preferences -> Preferred Applications, then selected the Multimedia tab, but the only selections are Rhythmbox Music Player and Totem. I rather expected a list of all media players available on my machine, but alas, they aren't present.

Can anyone clue me in on how I can select Xine as my default movie player? Thanks. :)

-Trip

---

### Post by mc4man on 2008-07-17
run
```
sudo update-alternatives --config totem
``` choose 2 and exit

---

### Post by tripwire45 on 2008-07-17
```
There is only 1 program which provides totem
(/usr/bin/totem-gstreamer). Nothing to configure.
```

---

### Post by mc4man on 2008-07-18
> to have Xine launch For Xine you'd have to try a method similar or the same as is done for vlc. Haven't tried it with Xine, should be no problem to enable and set as a default choice. The only issue would be if Xine's default launch command wasn't suitable. You may need to experiment there.
Here's one way to make vlc default that you could adapt - would need xine.desktop to be where expected.

[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

Thought you wanted to make totem-xine the totem choice for default player. (would have to be installed)

If you install gxine it should be auto added to default choice list. (sometimes a little tricky if it doesn't show up at first)

Edit: a quick looks shows the launch comm. for the xine player would be unsuitable for autoplay, maybe you could adjust, I sorta doubt. Probably better to run/open manually

---

