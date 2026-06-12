---
title: "DVD wont play even with packages"
date: 2010-01-15
forum: Multimedia Software
---

### Post by mikedero on 2010-01-15
I cannot for the life of me figure out how to get DVDs to play. I believe I installed the proper packages, including the region setter. I set my region to 1 and still no luck. 

When I first put the DVD in, it would just lock up the player, both VLC and xine. I installed some packages that allow me to play encoded DVDs and I got a screen that said something along the lines of "this dvd wont play in your region". I then installed the regionset package and set my region to 1, which is the right one for me. Now when I try to play a DVD, the region message wont show, but I get a bunch of colorful pixels and a frame of the movie every once in a while. Also, VLC shows this: "Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc." Followed by the player crashing. I have been searching and searching all day and i cant find what I'm looking for. I'm running Karmic. Please help, this is extremely frustrating.

---

### Post by mc4man on 2010-01-16
Assuming that libdvdcss2 is installed, though if not sure than run this
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
(if libdvdcss2 wasn't installed after installing do a restart and then try playback 

If it was already installed then  try going into home folder (view -> show hidden files) and delete the .dvdcss folder.
Then try playing a dvd in vlc again

(you may wish to start vlc from terminal for possible error messages
either just this than open the dvd from media -> open disk
```
vlc -vv
```
or directly (assumes dvd is in /dev/sr0
```
vlc -vv dvd://
```

---

