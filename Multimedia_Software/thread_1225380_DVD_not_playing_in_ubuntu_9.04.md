---
title: "DVD not playing in ubuntu 9.04"
date: 2009-07-28
forum: Multimedia Software
---

### Post by davy jones on 2009-07-28
**i just installed ubuntu 9.04 on my laptop. when i inserted an original dvd which i had rented it did not play in any player (movie player and vlc) saying 'you do not have the permissions to play this dvd'. i went to the ubuntu website and followed the instructions and installed** [B]libdvdcss2. when i reinserted the dvd and this time the beginning menu played but the movie is still not playing. only the sound is playing in vlc. it freezes up in movie player and doesnt play in mplayer either. i also installed repositories from medibuntu and installed w64 codecs from synaptic package manager but it still wont play. can someone PLEASE PLEASE PLEASE help me out????????
[/B]

---

### Post by igorzwx on 2009-07-28
some xine plugs are missings, perhaps

the exact instruction is this:
[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)


Play DVDs with VLC

---

### Post by davy jones on 2009-07-29
i tried it. didn't work

---

### Post by igorzwx on 2009-07-29
I simply do not believe.
It always works for me.
If it is so, then you made something wrong.
Or it is something wrong in your system.

---

### Post by uzdawi on 2009-07-29
It works for me

---

### Post by igorzwx on 2009-07-29
Hi Uzdawi!

you may find some interesting info here:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")
[http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html](http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html)

---

### Post by davy jones on 2009-07-29
no i found out that i had to go to the home folder and delete the .dvdcess file. its working after that.

---

### Post by igorzwx on 2009-07-29
Well done!!!

I should note this somewhere.

---

### Post by igorzwx on 2009-07-29
Very strange!

I have this hidden folder
~/.dvdcss

DVDs are playing without problems.
And in this folder, some information is stored about DVDs which
have been played on my box.

---

### Post by igorzwx on 2009-07-29
This might be a possible explanation:

You installed an old buggy version of **libdvdcss2**

---

### Post by Veggiet on 2009-09-29
I've been having a similar problem and I tried your solution but it still doesn't work. I used to be able to play dvd's fine until I upgraded to 9.04

---

