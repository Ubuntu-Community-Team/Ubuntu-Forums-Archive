---
title: "mplayer problems"
date: 2007-09-02
forum: Multimedia &amp; Video
---

### Post by n.aggel on 2007-09-02
i want to start using mplayer{for my video needs in ubuntu}, but i havve the following problems::

if i try to view a movie from command line i.e.

```
mplayer mymovie.avi
```

i have no problem viewing it....{resizing or whatever...everything works like it should...}

When i try to do the same from the front end of mplayer i get the message::

```
error opening/initializing the selected video_out (-vo) device
```

So after searching the forum a bit i follow the advise from this thread:: 

[http://ubuntuforums.org/showthread.php?t=459436]("http://ubuntuforums.org/showthread.php?t=459436")

> Right click on the player window and choose 'preferences'. Go into the video tab and choose a different driver .

So if i select xv i get the image distorted...and i can't fix it....
So if i select x11 i get a correct image BUT i can't resize it...if i draw the borders of mplayer screen, the image doesn't scale...also if i left click and select to double the screen size, of half it....the screen  dissapears, i have to flip to another desktop and then back to the previous to get it back{in the low left corner}....

I am using compiz fusion and i was wondering if this affects video....because if i log to a simple session {no xgl or compiz fusion} most problems go away.....

Any ideas?
Settings for video viewing?

PS:: the enable direct rendering option in mplayer what does it do?

PS2:: what is weird is that mpllayer functions correclty from command line, so i am gessing the gui version doesn't work like it should cause of some settings problem...but i don't know why...don't they share the same settings?

---

### Post by jusuchin85 on 2007-09-26
Hi there.

I'm having the same problems as he is. Been around everywhere, and can't find the solution for it.

Running XGL on a Dell Inspiron 1501 with ATi Radeon X1150 Mobility. If I run in either GL2, it becomes distorted like this:

[[IMG]http://img219.imageshack.us/img219/1151/screenshot1dq9.th.png[/IMG]](http://img219.imageshack.us/my.php?image=screenshot1dq9.png)

If I run it under X11 codec, it doesn't go to fullscreen at all!

[[IMG]http://img373.imageshack.us/img373/8161/screenshot2bp6.th.png[/IMG]](http://img373.imageshack.us/my.php?image=screenshot2bp6.png)

It has been bugging me for a long time. I tried using Totem and it worked! But, I want to try in Mplayer. I hope someone out there can help!

Thanks!

UPDATE: It's okay, It can finally work now. I just uninstall the fglrx driver for ATI and it works!

---

### Post by n.aggel on 2007-10-04
>>I just uninstall the fglrx driver for ATI and it works!

yes but isn't this driver necessary for the desktop-effects [ie compiz, etc...}?

---

### Post by Gremlinzzz on 2007-10-04
try smplayer
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
also you have to configure mplayer 
Mplayer-->Right-click on the screen-->Preferences
Video-->Available Drivers: X11 (XImage/Shm)
if you use the mplayer mozilla plugin you have to remove toem and other mozilla plugins to play divx on line add these commands to terminal
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so

---

