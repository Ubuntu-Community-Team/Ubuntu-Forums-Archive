---
title: "DVDauthor Disc Plays In PC but Not In DVD Player"
date: 2009-02-15
forum: Multimedia Software
---

### Post by umechanism on 2009-02-15
I'm using the following to edit and create DVDs of home movies:

[LIST=1]
[*]Kino to capture the video into .dv format
[*]Cinerella to edit the video (cut, clip, fades, etc)
[*]Q-DVDauthor to write the files to a DVD in the NTSC format required to play in home DVD players.
[/LIST]

The discs I have created will play in any computer.  For example, I put the disc in my drive and Movie Player (ubuntu 8.10) opens up and asks if I wish to play the movie.  I accept and the movie plays.

If I put the same disc in my Sony DVD player, it will not play.  I get a message that says, "Cannot Play Disc".  What have I done wrong?

Thanks?

---

### Post by umechanism on 2009-02-15
I just learned something.  I took the exact same media (same DVDs) and burned a family video to a DVD using Kino and then the same tracks using K3B.  The tracks burned with Kino worked great but the tracks burned with K3b did not.  So maybe K3B is my problem.

I've been burning "Data Discs" in K3B.  Is this correct or is there some "Make a Video DVD" selection that I'm missing here?

---

### Post by 5BallJuggler on 2009-02-15
If the disks work in any computer but not in a DVD player, the issue might have something to do with finalising the disk.

---

### Post by mc4man on 2009-02-15
I don't use k3b but a quick look suggests that if you are inputing a VIDEO_TS folder then

From the 'quickstart' menu choose "further actions..'-> "New Video DVD Project"

If your inputting an iso then the iso needs to be correct (DVD VIDEO format.

The requirements are 

DVD VIDEO format - how the 'iso is created


How it's burnt (responsibility of burning app
> The standard requires an UDF Bridge format: UDF version 1.02 plus ISO 9660 Level 1. 


---

### Post by Cresho on 2009-02-16
You cannot make a data dvd disk and expect a home dvd player to play it back.  you need to have qdvd author (if it has this option) createa an iso image and use k3b to burn iso image to dvd.  It works for me but of course I use devede.  I do know for a fact you cannot create data dvd and expect those files to play.  There are standards you know

---

### Post by Perkins on 2009-02-16
Two possibilities:

1.  Tell qdvdauthor to burn the disc for you.  That's what I usually do.  At the very least you can tell it to compile an image that you can burn.

2.  Depending on your DVD player, I have found more than a few which are picky eaters when it comes to burnt discs.  Some older ones in particular I have found to have problems with anything faster than 4x discs.  You can usually find 4x in stores that don't have a lot of turnover.  Alas, they won't be any cheaper than the faster ones.  But it might be worth a try.

---

