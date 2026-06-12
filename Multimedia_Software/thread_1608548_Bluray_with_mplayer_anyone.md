---
title: "Bluray with mplayer anyone?"
date: 2010-10-29
forum: Multimedia Software
---

### Post by tripmix on 2010-10-29
So I've been trying all day to get bluray to play in mplayer and I almost got it now :D This is my current output, still no video though.  ```
bluray bd:////media/cdrom0/ -vo vdpau -vc ffh264vdpau -fs -zoom
MPlayer SVN-r32561-4.4.3 (C) 2000-2010 MPlayer Team

Playing bd:////media/cdrom0/.
Opening /media/cdrom0//BDMV/STREAM/00000.m2ts

Unknown type 80 in clipinf
MPEG-PES file format detected.
```
The disc is spinning and mplayer is using the cpu but alas nothing. I'm done for the night/day but I though I'd post what I did here first.

I started by getting, compiling and installing libbluray and libaacs from vlc git repo. Then I compiled and installed mplayer from svn, remember to get the libs you need first like libvdpau-dev. To not mess up your regular mplayer compile with --prefix= option. After that I needed to get a file called KEYDB.cfg and put it in /home/user/.dvdcss/ lucky for me the bluray I wanted to play was not in the list but mplayer outputted a long hex number that was useful for the first argument in the KEYDB.cfg. To get the other hex numbers I needed I got an app called aacskeys, the disk label I just guessed and haven't found a proper way to get (don't know if it's important). Every app here can be found trough google. I wasn't sure if it's ok to post links to things people with money don't like here, but if it is I'll type up a more complete tutorial later. Please experiment and post your results so we can figure this out, I for one will not surrender to sony.

EDIT: Damn, it works! I just tried another bluray that I knew the keys where correct for and it plays perfectly. I whipped up a simple script so I can play them with just one command. > #!/bin/bash
sudo mount -t udf -o loop /dev/cdrom /mnt/bd &&
track=`du /mnt/bd/BDMV/STREAM/* | sort -n -r | head -n 1 | cut -c30-34`
~/bluray/bin/mplayer bd://"$track" -vo xv -fs -zoom && # -vo vdpau -vc ffvc1vdpau
sudo umount /mnt/bd you'll need to edit the path to your own custom mplayer and maybe make the /mnt/bd folder to use this. edit2: Oh and the stuff after # is just because i screwed up vdpau when compiling mplayer so I'm stuck with xv till I bother fixing it.

---

