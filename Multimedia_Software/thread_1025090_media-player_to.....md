---
title: "media-player to...."
date: 2008-12-29
forum: Multimedia Software
---

### Post by davidtuti on 2008-12-29
Hi,

I have Kubuntu 8.10 and I would like a program to see videos (like kaffeine, vlc, mediaplayer ....) that I could execute the video from command line and if it's possible to control when the video ended to can execute a post-script.
I've saw the dcop possibility but I'm newbie with media players for Linux and I dont know what it's the best to my requirements

Any help?
Many thanks and sorry for my english!!

---

### Post by 2hot6ft2 on 2008-12-29
Type mplayer in a terminal and it will give you a list of options

---

### Post by andrew.46 on 2008-12-29
Hi davidtuti,

> **davidtuti said:**
> I have Kubuntu 8.10 and I would like a program to see videos (like kaffeine, vlc, mediaplayer ....) that I could execute the video from command line and if it's possible to control when the video ended to can execute a post-script.

If you use MPlayer from the commandline the option you are after is '-endpos' which you can set for a time interval. An example taken from the MPlayer man pages is:
> 
-endpos 01:10:00
Stop at 1 hour 10 minutes.

Hope this is what you are after?

 Andrew

---

### Post by davidtuti on 2008-12-30
Many thanks!

I try with mplayer but I dont understand this media player. Where are a button to stop de movie, to play, pause, etc. I can't find them.

Many thanks!

---

### Post by andrew.46 on 2008-12-30
Hi davidtuti,

> **davidtuti said:**
> I try with mplayer but I dont understand this media player. Where are a button to stop de movie, to play, pause, etc. I can't find them.

I have perhaps misunderstood your question, my apologies :(. This is the commandline face of MPlayer and the functions you speak of are by default a set of keys:

```
Basic keys: (complete list in the man page, also check input.conf)
 <-  or  ->       seek backward/forward 10 seconds
 down or up       seek backward/forward  1 minute
 pgdown or pgup   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 x or z           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand

```

There is a nice frontend for MPlayer called smplayer but this of course a gui, were you not after something to start a movie from the commandline?

All the best,

 Andrew

---

### Post by davidtuti on 2008-12-30
Well the problem that I have is that I don't have keyboard because I see the movie in the tv on my living-room and I have only a mouse cordless , so I would like to stop,pause, etc the movie from the frontend.

---

