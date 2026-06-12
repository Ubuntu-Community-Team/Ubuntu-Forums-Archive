---
title: "Kaffeine - Able to play DivX but not Xvid .AVI files"
date: 2006-12-26
forum: Multimedia &amp; Video
---

### Post by solderhead on 2006-12-26
I'm using Kubuntu/Edgy.  I have installed the multimedia codecs using Automatix2.  Everything seems to be working fine, except that I am having a problem playing one subtype of .AVI video files.

Kaffeine has no problems at all playing .AVI files that have been encoded with DivX.  It won't, however, play  a file that's been encoded with Xvid.  When I attempt to play and Xvid encoded file, I get a dialog box that pops up with the following error:

```
xine error -- Kaffeine player

No plugin found to handle this resource.  

xine: couldn't find demux for >/home/bob/Desktop/filename.dvdrip.xvid.ac3-fov.avi<
xine: found input plugin : file input plugin
```

Any ideas?  TIA.

---

### Post by netyire on 2006-12-26
OK, I am not sure if this will work for you, but feel free to try anyway. Type the following in the terminal:

```
sudo apt-get install libxine-extracodecs
```

Does it work?

---

### Post by solderhead on 2006-12-26
Thanks for the help.  As it turns out, I already had the most current version of that file:

```
~$ sudo apt-get install libxine-extracodecs
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
libxine-extracodecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I have to admit, I'm really confused by what could be causing this.  :-?

---

### Post by e_james on 2006-12-30
I'm no expert (especially with Linux): I stumbled across this thread looking for divx references. Is it possible that you know the file is xvid but the the software does not? The usual method of format identification of an avi file is the 4cc (4 character code) at the beginning of the file. I just ran a quick test. My xvid codec offers me three 4cc values 'XVID', 'DIVX' and 'DX50'. These seem to be inserted in the file as 'xvid', 'DIVX/xvid' and 'DX50/xvid'. I don't know how intelligent your software is, but there seems to be some room for confusion.

---

### Post by 1337homeboyRicky on 2007-01-01
Yeah i have the same problem, but when i try to play a .AVI format video (xvid), using ubuntu 6.06, it just shows a black screen and just skips through the whole movie, and i am using kaffeine to play this video. any help please xD
much appreciated guys 
and btw im very new to ubuntu

---

### Post by Valhalla on 2007-05-20
I don't know if you guys are still having problems with this, but I stumbled across this issue on a fresh install. I fixed it by installing libavifile-0.7c2 and avifile-xvid-plugin
Hope this helps. Cheers.

---

### Post by Sunlust on 2008-01-18
Sorry for reviving old thread, but that's the closest what I found on forums to my problem

I have a movie that my friend ripped for my from his dvd, and it's in xvid format, but I can't play it in any way,
I'm using Ubuntu 7.10, on gnome with e17 as window manager.
I have smplayer movie player, movie player, mplayer movie player, kaffeine and vlc, none of them can play the movie.

kaffeine returns an error:
```

22:14:51: xine: couldn't find demux for >/home/krystian/Videos/Family_Man.DVDRip.XviD-aXXo.avi<
22:14:51: xine: found input plugin : file input plugin

```

Movie player gives similar "can't find a plugin for this resource"
I installed newest w32 plugins, then I tried with automatix, nothing changes, i tried several different threads and nothing.

Any help?

---

### Post by rvm4000 on 2008-01-18
What does mplayer say?

---

### Post by Sunlust on 2008-01-18
> **rvm4000 said:**
> What does mplayer say?

Funny enough Mplayer just dies, I have to kill it otherwise it just freezes and stays like that, but Smplayer just freezes, but I'm able to close it, with a 10 sec+ delay.
I tried launching through terminal, they don't show any errors, just "playing his and this file" but nothing happens.

---

