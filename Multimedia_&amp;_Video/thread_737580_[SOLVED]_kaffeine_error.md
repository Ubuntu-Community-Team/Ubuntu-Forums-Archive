---
title: "[SOLVED] kaffeine error"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by upthelum on 2008-03-27
Can someone tell me what files/plugins i need to fix this. Trying to watch dvd's burned from avi files which are ok on tv and winblows but i get this error in Kaffeine and other files i have won't play in any media players.

help

---

### Post by upthelum on 2008-03-30
Bump

This is beginning to annoy. I cant watch any dvd's in Linux and don't want to use windows much any more. I cant play some dvd's straight out the box either.

---

### Post by Whiffle on 2008-03-30
I'm guessing either libxine-ffmpeg or libdvdcss

---

### Post by upthelum on 2008-04-05
Tried installing these and got this:

root@don-laptop:~# apt-get install libxine-ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libxine-ffmpeg
root@don-laptop:~# apt-get install libdvdcss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss has no installation candidate
root@don-laptop:~#

---

### Post by benerivo on 2008-04-05
I don't think libdvdcss2 is in the reps. If you were to add the [medibuntu]("http://www.medibuntu.org/") repository, you could then install it.  Search for libxine in your package manager (adept or synaptic) and you will find the file (i think it is called libxine1-ffmpeg). After installing libdvdcss2 from medibuntu, then kaffeine might play dvd's, although using vlc (another media player) is a fine alternative if kaffeine doesn't work.

---

### Post by upthelum on 2008-04-05
I have and prefer vlc as in winblows it plays just about anything, Ok something really weird just happened. I tried to view a video stream from wwe which just opened the video window and said "transfering data bla bla", so i right clicked on it and chose open with movie player, which crashed the browser. I have no idea what's going on as i cant play any video's with any player...

---

### Post by upthelum on 2008-04-05
Did that and still getting same messages.

---

### Post by benerivo on 2008-04-05
I think it would be best if we started from the bottom up, by trying to play a video file on your hard drive, using vlc. Can you download [this]("http://www.darim.co.kr/ftp/mpegs/lions.mpg") and try to play it in vlc? From here, can you ensure that libdvdcss2 is installed, then try to play a dvd disc using vlc?

---

### Post by upthelum on 2008-04-05
Ok the first time i played the mpg it displayed about 1 second of image then went black but i still had sound and it played out the whole thing though i couldn't see it, i had audio. Then it played fine the second time. So i then tried bourne ultimatum dvd which i know works in winblows and on a tv, it opened and just stopped and the time scale was at the end as if the movie had been viewed, but it had not.

---

### Post by benerivo on 2008-04-05
Well there are some significant problems here, that are well over my head. I can only suggest that you play them 'through' a console to see what error messages (if any) vlc provides. If you don't already know how to do this, then open konsole and type vlc. Then open your video files and your dvd from vlc, and any errors will be displayed in the terminal. Even a fully working video playback will display some messages, but if you can post what you consider as pertinent messages then this may help solve this.

---

### Post by upthelum on 2008-04-05
This is the terminal output:

root@don-laptop:~# vlc
VLC media player 0.8.6 Janus
starting VLC root wrapper... using UID 1000 (don)

** (.:7972): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
[00000287] main playlist: nothing to play

It just stops with a flashing cursor and no prompt until i close vlc. Deosn't look good me thinks but hey, most things have a fix.

I also Googled this error and got nothing...

---

### Post by xc3RnbFO8P on 2008-04-05
Feisty Fawn 32 or 64 bit?

---

### Post by upthelum on 2008-04-05
Ok this post was initially for a Kaffeine error. This now seems to be partly resolved as one dvd just ran in Kaffeine, but wont in vlc, my choice of media players. There are definitely strange things going on, i just tried another file, avi, which played in vlc but only with audio.

---

### Post by upthelum on 2008-04-05
32 bit

---

### Post by upthelum on 2008-04-05
I am going to mark this as solved for the moment as some files and discs are playing now in various players. Perhaps an update had an effect, perhaps not i'm not really sure what is going on. 

Thanks to all for comments.

---

