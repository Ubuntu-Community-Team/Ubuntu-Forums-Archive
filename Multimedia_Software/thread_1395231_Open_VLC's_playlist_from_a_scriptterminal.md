---
title: "Open VLC's playlist from a script/terminal?"
date: 2010-01-31
forum: Multimedia Software
---

### Post by dillandriskell on 2010-01-31
Hi!

I'm trying to write a script that opens up vlc, opens up the playlist, and then opens up my music folder.  So thus it looks like this so far;

```
#!/bin/bash

vlc &
# command to open up vlc playlist
gnome-open /media/files/multimedia/music
```However, I seem to have no clue as to how to open vlc's playlist from a command.  I know the hotkey for opening the playlist is "ctrl + L" but I don't know if this is useful at all.

Any help would be very much appreciated.

---

### Post by dillandriskell on 2010-01-31
bump :(

---

### Post by sports.car.guy on 2010-01-31
It is easy. Create the playlist, then when you start up VLC pass it too it like if you were telling it to play a song of video file.

Like this:

vlc file://(the path to and name of your playlist)

It is like calling vlc from the command line with any other circumstances. Like if it was the alternate player in MythTV.

To double check if you used file. I did a vlc --help.

If you had done vlc --help or googled vlc terminal commands Linux you would have probably found this out on your own. Not trying to be a jerk here. I swear, but I think that is honestly why no one had taken the time to respond.

---

### Post by mc4man on 2010-01-31
> to how to open vlc's playlist from a command
I don't believe there is one, vlc remembers it's last state.
So close vlc with the playlist open and it will then open with the playlist visible

Based on ~/.config/vlc/vlc-qt-interface.conf < playlist-visible=1 >

---

### Post by dillandriskell on 2010-02-01
> **mc4man said:**
> vlc remembers it's last state.

I see, that worked just fine.  That'll definitely help me cut corners and save some time now when I want to put together a playlist.  Thank you!

And thank you sports.car.guy, that actually gave me a couple of new ideas I've tried out successfully.  Now if I want to listen to say my trance music I just type "trance" into the terminal and boom, it opens that playlist for me.

---

### Post by sports.car.guy on 2010-02-01
> **dillandriskell said:**
> I see, that worked just fine.  That'll definitely help me cut corners and save some time now when I want to put together a playlist.  Thank you!

And thank you sports.car.guy, that actually gave me a couple of new ideas I've tried out successfully.  Now if I want to listen to say my trance music I just type "trance" into the terminal and boom, it opens that playlist for me.


I am glad my post helped you.

---

