---
title: "Cannot play dvds, libdvdcss etc. installed (an old question, I know)"
date: 2009-06-23
forum: Multimedia Software
---

### Post by mlinchits on 2009-06-23
[Ubuntu Jaunty]

I know this is a recurring question on this forum, but I haven't yet found a solution to my problem. I have libdvdcss, dvdnav, dvdread (all latest versions) installed, along with ffmpeg, xine or gstreamer and its plugins. I ran the install shell script for dvdread as fake root. I have tried to play the dvd in VLC, Xine, mplayer and totem. VLC can only show the menu, while the others show nothing. DVD plays fine in VLC on Windows XP. I can also play unencrypted DVD's in Ubuntu without problem. Drive region is set to 1(North America). I remember trying to play dvd's on a different ubuntu system and could likewise not get beyond the DVD menu. Are the players not recognizing libdvdcss or something? Can many dvd's simply not be read with libdvdcss? 

Should I be looking at other dvd reading libraries?
 
Much appreciated

---

### Post by LKjell on 2009-06-23
Hi. Just to make sure let us install the restricted extra for ubuntu. You will get more than just dvd read support. ```
sudo apt-get install ubuntu-restricted-extras
```

Try now to open totem. Under Movie select play Disc. Totem will skip the menu and play the content.

---

### Post by mlinchits on 2009-06-23
restricted-extras has already been installed.

---

### Post by LKjell on 2009-06-23
Interesting have you tried the guide at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") ?

---

### Post by Hamchan on 2009-06-23
> **LKjell said:**
> Interesting have you tried the guide at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs") ?

I was having the same problem a couple of weeks ago. I tried this guide and that knocked it right out.

---

### Post by mlinchits on 2009-06-23
Yes, I've tried all the steps in that guide. I am surprised that the guide is all it takes for many people, because I have never had much luck with it.

Is libdvdcss compatible with the drive region being set to North America:confused:

---

### Post by LKjell on 2009-06-23
To be honest I really do not know what the problem could be. But you might try to read the .vob files directly. Usually they are located at /cdrom/VIDEO_TS.

---

### Post by mc4man on 2009-06-23
Why don't you try something simple and see if anything shows up.

first go into home folder and delete the .dvdcss folder (hidden

Then open a terminal and use this to start vlc with 

```
export DVDCSS_VERBOSE=2 && vlc > vlc_output 2>&1

```
Try to play the dvd (media -> open disc), after whatever happens close the terminal and look in home folder for a file named vlc_output, post contents.

Then maybe also start vlc from the terminal with this and again try to play dvd
```
vlc -vv
```

The terminal output will be quite large, see if anything of interest shows up

---

### Post by mlinchits on 2009-06-23
thanks a lot mc4man. all I had to do was delete that folder!

---

### Post by stinger30au on 2009-06-23
mmmm... interesting fix

im glad you got it sorted

---

### Post by mc4man on 2009-06-23
most players that use libdvdcss2 will always look in .dvdcss for a folder matching the volume label (id) of the disc. If found they'll use the key files inside whether they are correct or not, complete or incomplete.

so removing .dvdcss is always a good first step.

Ex. (same disc, small snippet

with no matching volume folder in .dvdcss

> libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002ab317
libdvdcss debug: getting title key at block 2798359 the classic way
libdvdcss debug: requesting AGID
libdvdcss debug: drive authenticated, using variant 0
libdvdcss debug: authentication established
libdvdcss debug: GetASF authenticated, ASF=1
libdvdcss debug: [COLOR="Blue"]initial disc[/COLOR] key 36:77:cb:3a:7a
libdvdcss debug: decrypted title key cd:08:a5:8f:b6
libdvdcss debug: title key is cd:08:a5:8f:b6

With a match in .dvdcss

> libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002ab317
libdvdcss debug: title key [COLOR="Blue"]found in cache[/COLOR] cd:08:a5:8f:b6
libdvdread: Elapsed time 0

Another thing that can work when all else fails is to try changing the method of acquiring keys. (an export in this case lasts till a reboot, the vlc default is disc key

Ex. same disc, no folder in ,dvdcss
```
export DVDCSS_METHOD=title && vlc dvd://


```

> libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002ab317
libdvdcss debug: [COLOR="Blue"]cracking title key[/COLOR] at block 2798359
libdvdcss debug: successful attempts 1/1, scrambled blocks 1/2
libdvdcss debug: vts key initialized
libdvdcss debug: title key is cd:08:a5:8f:b6

---

### Post by dragonhunter on 2009-06-28
Thanks Mc4man your instructions worked really well.

I was having exactly the same problem as mlinchits and removing that folder make my dvd play againg!

---

### Post by MatMan on 2009-07-08
Good work, worked for me too. This should be included in the multimedia sticky guide. I have had the same problem for days and day &c.

thanks.

---

