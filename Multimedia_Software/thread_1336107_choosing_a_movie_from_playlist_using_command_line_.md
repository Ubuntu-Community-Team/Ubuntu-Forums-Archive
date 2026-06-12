---
title: "choosing a movie from playlist using command line in totem"
date: 2009-11-24
forum: Multimedia Software
---

### Post by faustobm on 2009-11-24
Hi,

I can change playlist, move to next/previous movie using command line.
Can I choose a movie from playlist using command line in totem ?

Thanks

---

### Post by amauk on 2009-11-24
```
man totem
```

>        The following options command an already-running instance of  Totem  to
       do something; they are useful for remote-control scripting. If Totem is
       not already running, these commands will launch a new instance of Totem
       but will not do anything further.

       --play-pause
              Tell an already-running instance of Totem to toggle between play
              and pause.

       --play Tell an already-running instance of Totem to play (has no effect
              if already playing)

       --pause
              Tell  an  already-running  instance  of  Totem  to pause (has no
              effect if already paused)

       --next Tell an already-running instance of Totem to skip  to  the  next
              movie or chapter in the playlist.

       --previous
              Tell  an already-running instance of Totem to return to the pre&#8208;
              vious movie or chapter in the playlist.

       --seek-fwd
              Tell an already-running instance of Totem to  seek  forwards  15
              seconds in the current movie.

       --seek-bwd
              Tell  an  already-running instance of Totem to seek backwards 15
              seconds in the current movie.

       --volume-up
              Tell an already-running instance of Totem to raise the volume by
              8%.

       --volume-down
              Tell an already-running instance of Totem to lower the volume by
              8%.

       --fullscreen
              Tell an already-running instance of Totem to  toggle  fullscreen
              mode.

       --toggle-controls
              Tell  an already-running instance of Totem to toggle showing the
              controls.

       --quit Tell an already-running instance of Totem to quit.

       --enqueue filename|URI
              Tell an already-running instance of Totem to add a new stream to
              the playlist.

       --replace filename|URI
              Tell  an  already-running  instance  of  Totem  to play from the
              playlist.

---

### Post by wojox on 2009-11-24
```
totem --help
```

```
totem --play path/to/movie
```

---

### Post by faustobm on 2009-11-24
Hi,

Thank for answers. 
I already use this commands to remote-control Totem player. 

Can I suggest to Totem Developer Team to add command line to skip directly for a given movie? (Like a mouse click in movie from totem desktop user interface. )

---

