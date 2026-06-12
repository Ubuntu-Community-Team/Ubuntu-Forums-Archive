---
title: "Dvd help"
date: 2008-12-19
forum: Multimedia Software
---

### Post by enzodad on 2008-12-19
i can not make a dvd!! that playes in a player!!!! i make the iso burn to disk and nothing wtf where is a program that will take a avi or what ever and make a dvd please anyone simple retards guide or something  wasted 20+dvds already

---

### Post by bellmount on 2009-01-03
I read your other post, too so that clarified your situation slightly, although a little more details on what problem exactly you're experiencing would have been helpful.

The [quote:] "avi or whatever" might be what's causing your trouble:
Does your DVDplayer support formats like avi (divx) at all? Most players don't, so in order to play those movies you need to convert the file into something your player can actually read before burning. Or, depending on which prog you burn with, set your write option to NOT data.

Have a nice day,
bellmount

---

### Post by mpoole on 2009-01-25
I think I have the same issue running Ubuntu 8.04.  I can burn a file to a DVD but the disk will not play in a stand alone DVD player.  I have tried devede, k3b, qdvdauthor, and todisk to no avail.  The file is on the disk and I can play the file on by box and on a windows box.  I too have wasted many blank DVD's and would appreciate any help.

---

### Post by super newbie on 2009-02-01
i'm having the same problem, i used to to be able to make a back-up copy with no problem.  i recentley downgraded from 8.10 back to 8.04 and now my back-ups will only play on my ubuntu box....they will not play in my stand alone dvd player or in my windows box.  i've tried using +R, -R and RW media with no luck.  i've tried using k9copy with k3b, i've tried making an .iso with k9 and right clicking and choosing "write to disc".  no luck.any ideas as i am getting tired of making a bunch of "coasters" thanks in advance....mike

---

### Post by IanW on 2009-02-01
To make a successful DVD, your *.avi files, etc must first be changed into DVD-compatable MPEG 2 files.

From the repos install Avidemux, or (in a terminal) call ffmpeg with the following command:-
```

ffmpeg -i input.avi -target pal-dvd (or ntsc-dvd if you're USAian) -out output.mpg

```

Then pass the resulting mpg file to your DVD authoring program (Tovid,DeVeDe,etc).

PS - Enzodad, try getting some RW media. These can be erased and reused if your burn fails.

---

