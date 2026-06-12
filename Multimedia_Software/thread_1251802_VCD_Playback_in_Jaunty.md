---
title: "VCD Playback in Jaunty"
date: 2009-08-28
forum: Multimedia Software
---

### Post by yasasflash on 2009-08-28
Hi guys,

Well i tried to play a simple VCD with my ubunty jaunty. But it doesn't even recognize the vcd as a playable thing. Of course i tried several VCD's but none of them were working.

None of other video formats cause me any trouble because they play really well.

Finally i've  installed  w32codecs and libdvdcss codecs but unfortunately that isn't helped me.

I have Xine, Mplayer, Smplayer and VLC installed in. But same result from all of them.

(VCD's that i've tested were working fine with windows media player)

plz need a help guys.

---

### Post by yasasflash on 2009-08-28
Any one??  :(

---

### Post by prshah on 2009-08-28
> **yasasflash said:**
> 
play a simple VCD

I have Xine, Mplayer, Smplayer and VLC installed in. 

VCD's play fine for me, but for some reason, I can only launch them from the command line. Open a terminal (Applications-Accessories-Terminal) and give the command```
vlc vcd:///dev/cdrom
``` (replace cdrom with the actual device code on your system).

Post back the output messages if it doesn't work...

---

### Post by stinger30au on 2009-08-28
do you get any error messages when you try and play vcds???

if so, please tell us that they are

---

### Post by yasasflash on 2009-08-30
> **stinger30au said:**
> do you get any error messages when you try and play vcds???

if so, please tell us that they are

> **prshah said:**
> VCD's play fine for me, but for some reason, I can only launch them from the command line. Open a terminal (Applications-Accessories-Terminal) and give the command```
vlc vcd:///dev/cdrom
``` (replace cdrom with the actual device code on your system).

Post back the output messages if it doesn't work...

sorry guys i was not in the home for a while. well i tried the prshah's idea but
same old result. Nothing happens , instead vlc freezes itself. 
thing is, i even can't copy or play dat files from the vcd to hard disk.

but here's another thing then i boot up to my XP side and copied the dat files to the hard disk.
after that i rename those to mpg and then reboot to Ubuntu.
and ta-daa ubuntu able to play all those renamed files with no worries.

But still can't even copy a single file from a vcd using Ubuntu. How come???

---

### Post by kareempharmacist on 2011-11-10
use k3b to rip them to the hard disk
choose tools then rip vcd
another option install vcdxrip
then type
```
vcdxrip --nofiles -v -p
```
you should type this from your home directory
you will  find the files in your home directory
good luck

---

### Post by lisati on 2011-11-10
I think this old thread can go back to sleep. Thread closed.

---

