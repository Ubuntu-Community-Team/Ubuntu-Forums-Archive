---
title: "I can't play vcds with totem"
date: 2008-12-24
forum: Multimedia Software
---

### Post by mvalviar on 2008-12-24
Hi I'm trying to watch a vcd with Totem by Movie > Play Disk but it pops the error "Could not open location; you might not have permission to open the file". I tried mplayer to by opening the .dat file I get the error "seek failed". I have all the codecs and can play any media files on totem and mplayer. I'm using ubuntu 8.04. Help please. Thanks!

---

### Post by namdung on 2008-12-24
Is it a valid the movie file? Have u been able to play it in other medium?

Try changing the file permissions
sudo chmod 777 filename

---

### Post by mvalviar on 2008-12-27
Its a vcd, read only and on my cd drive. When I run totem on the terminal and try to play using Movie>play disc its says something to the effect of I/O error. Using mplayer when is select play disc there is a pop up saying something to the effect of I/O error but the disc plays. I'm fond of using totem so I wanna have a fix on this.

---

### Post by xc3RnbFO8P on 2008-12-27
You cant play VCD in Totem, use VLC> Open Disk, choose svcd/vcd

---

### Post by mvalviar on 2008-12-30
I've heard that others doesn't have a problem playing vcds in totem. Am I missing something here?

---

### Post by ellalan on 2008-12-31
I had the same problem and I installed SMPlayer from:[https://launchpad.net/~rvm/+archive](https://launchpad.net/~rvm/+archive)
Now my vcd works in SMPlayer.

---

### Post by mvalviar on 2009-01-04
I'm using mplayer now to play vcds. Although I have a pop up saying that an I/O error occurred when I play the cd it still plays.

---

