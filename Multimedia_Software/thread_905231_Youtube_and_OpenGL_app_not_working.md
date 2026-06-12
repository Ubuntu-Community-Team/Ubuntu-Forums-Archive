---
title: "Youtube and OpenGL app not working"
date: 2008-08-30
forum: Multimedia Software
---

### Post by Bucky Ball on 2008-08-30
Hi all.

I originally installed flashplayer 10 using this code:

```
cd /tmp
wget [http://download.macromedia.com/pub/l..._070208.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz")
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer
```All was working fine (for about 3 months). Boot up this morning, go to youtube to check out something for uni, but get the old grey box where the vid should be and no response. Odd. I have tweaked nothing to make this happen and in fact was working fine last night.

Wondering if this is a flash problem or something else as I did notice something odd was happening last night, but not with youtube. Thought I might have a break from study and have a game of foobilliards. Haven't played that in awhile and was working fine last time I did play. Nothing. Desktop flickers when I boot it up but nothing. Downloaded Cannon smash (ping pong simulation) to see if that worked and same. No screen, but with this, I could hear the ping pong ball getting hit! The plot thickens.

Foobilliards uses OpenGL. I am wondering if it has anything to do with this (and not flashplayer). Is this one issue or two that have coincidentally occured at the same time? Again, haven't tweaked anything that I imagine would effect this but will keep looking. Any ideas?

*** UPDATE!!!

Changed a few things in my software sources, reopened youtube and back to normal! Okay, that makes some sense. What doesn't is that did a little research, go to synaptics package manager and 'python-opengl' not installed, along with every other package relating to opengl!?! Not sure how this happened. Can anyone enlighten me on this??? IE what do I need to reinstall, just 'open-gl'? Really don't know how it is uninstalled as must have been happening for Foobilliards to work, yea? :)

---

