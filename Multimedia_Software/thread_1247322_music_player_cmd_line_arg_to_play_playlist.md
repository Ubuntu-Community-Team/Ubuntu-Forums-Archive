---
title: "music player cmd line arg to play playlist"
date: 2009-08-22
forum: Multimedia Software
---

### Post by zsugiart on 2009-08-22
Hi, 

I'm looking for a music player in Ubuntu (KDE/GNOME) that can do this in the command line: 

musicplayer --playlist "playlist name" 

... to play a playlist with the name "playlist name"

rhythmbox is my preferred music player, but it can only start and stop currently selected playlist. In Winamp, I used to have morning playlist that will play every morning at 7am (to wake me up). 

Scheduling is taken care of with cron, but unfortunately the cmd line arg for rhythmbox doesn't expose this feature, so it's not schedulable. 

question: 
1. is there a music player that can do --playlist "playlist name" ?
2. what music player has the richest command line args / options ?

---

### Post by zsugiart on 2009-08-24
I take it then that this is not possible :(

---

### Post by mcduck on 2009-08-24
mpc, ncmpc, mplayer, vlc, actually pretty much any command line music player I can think of supports loading playlists from CLI.

---

### Post by nikhilbhardwaj on 2009-08-24
mpg321 is what you are looking for
the playlist should be a list of files one per line with the complete path

---

### Post by cherva on 2009-08-24
mocp is a nice console player

---

### Post by andrew.46 on 2009-09-16
Hi zsugiart,

> **zsugiart said:**
> is there a music player that can do --playlist "playlist name" ?

You almost have the MPlayer command there:

```
mplayer -playlist filename.pls
```

From the man pages:
```

 -playlist <filename>
              Play files according to a playlist file (ASX, Winamp,  SMIL,  or
              one-file-per-line format).


```

Is this what you mean?

Andrew

---

