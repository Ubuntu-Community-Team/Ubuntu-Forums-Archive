---
title: "Terminal only music player, does it exist?"
date: 2008-12-17
forum: Multimedia Software
---

### Post by Nico-dk on 2008-12-17
Just did a google for this, but with no luck (otherwise I probably wouldn't be in here ;) )

As the title suggest, I'm looking for a music player that I can run from Terminal. Only requiremtns are these:
> Must have volume control/mute
> Repeat song
> Play audio files through a parameter
```
eg: musicplayer -musicfile.mp3 -vol10 -repeat
```

Does one exist, or is there already such functionality in Ubuntu? (yes, I'm a newbie)

Thanks for your time :)

---

### Post by hectorh30 on 2009-05-28
cplay is a nice option, another is mplayer but I haven't use it

About cplay, you install it with

sudo apt-get install cplay

and you have also to install mpg123, well thats what I did in order to use cplay. 

Finally, you run it with

cplay -r file/to/the/music

and then you control the volume with 1,2,3...0
the option -r repeats the playlist.

More info with the command 
man cplay

or pressing 'h' once you run the program

---

### Post by m_duck on 2009-05-28
Or moc (music on console) for a pretty full featured one.```
sudo apt-get install moc
```Run it with```
mocp /path/to/music/directory
```This will show a sort of file browser type thing of all of your music. Arrow keys and enter to play. Also nice as it keeps playing even after X crashes. If you quit with 'q' it also keeps playing and frees the terminal window. Quit with 'Q' to quit and stop playback.

There are loads of other hotkeys, themes etc. It's all in the man page:```
man moc
```

Failing that and you have some time to spare, there is always mpd and one of the many cli frontends like mpc or ncmpc(pp).

---

### Post by mcduck on 2009-05-28
many other media players can be used from command-line as well. Mplayer is very popular choice, and VLC has quite a lot CLI power as well.

Personally, I prefer database-based music players and therefore use MPD together with some ncmpc as client.

---

### Post by andrew.46 on 2009-05-29
Hi Mico,

> **Nico-dk said:**
> 
```
eg: musicplayer -musicfile.mp3 -vol10 -repeat
```


The commandline you mentioned can be reproduced with MPlayer:

```

mplayer -af volume=5 -loop 2 test.wma 

```

All the best,

Andrew

---

### Post by tali713 on 2009-07-07
I like cmus quite a bit.  It is ncurses based though, so maybe not what you are looking for.  It's terminal only, but not strictly speaking CLI.  Though it does have an internal CLI.

---

### Post by preschian on 2010-09-06
> **m_duck said:**
> Or moc (music on console) for a pretty full featured one.```
sudo apt-get install moc
```Run it with```
mocp /path/to/music/directory
```This will show a sort of file browser type thing of all of your music. Arrow keys and enter to play. Also nice as it keeps playing even after X crashes. If you quit with 'q' it also keeps playing and frees the terminal window. Quit with 'Q' to quit and stop playback.

There are loads of other hotkeys, themes etc. It's all in the man page:```
man moc
```Failing that and you have some time to spare, there is always mpd and one of the many cli frontends like mpc or ncmpc(pp).

Nice... :popcorn:

---

### Post by Turgon_Noldor on 2011-07-11
ncmpcpp

---

