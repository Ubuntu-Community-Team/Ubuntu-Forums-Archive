---
title: "Will mythbuntu serve my needs?"
date: 2007-11-26
forum: Mythbuntu
---

### Post by onesojourner on 2007-11-26
I am upgrading my computer so my old machine may be turned into a myth box. Right now I am using xbmc on an xbox to stream videos over the network to the tv.
------------------------------------------------------------------------------------------------------------------------------------------
The primary function of the myth box would be to stream video over the network(smb shres)  to the tv via s video. I would also have some videos stored directly on the hdds in the myth box. I am assuming the myth tv has no problem playing various video file types. Eventually I will need to stream hd content.
------------------------------------------------------------------------------------------------------------------------------------------
Some secondary functions would be nes/snes/n64 emulator using usb adapters for controllers, web browser, dvd player, download torrent files, sirius radio streams, watch live tv (I wont be using schedules direct for now), stream pictures over the network, suspend/hibernate or very fast boot time, 


System specs
AMD 2500
1g memory
D-link wiki card
nvidia 5200 64mb (s-video and dvi)
windows mce remote
hauppauge pvr-150

---

### Post by aznewsh on 2007-11-27
I am already doing pretty much everything you mentioned so I guess the answer is yes

---

### Post by onesojourner on 2007-11-27
alright thanks for the response. I will give it a go.

---

### Post by Calash on 2007-11-27
By default MythTV stores it's streams as files, even during live viewing.  This gives you the ability to rewind, pause, and all that cool stuff.

MythTV has 2 components, the Backend and the Frontend.  The Backend handles the recording and card management, while the Frontend handles the GUI and interface.  On the standard configuration these are on the same system, but you can easily add another Frontend to a Linux system and get full access to all the functions, including LiveTV.  There is a post over at BYOPVR.com where a person was able to stream HD content over Wireless.  I am not sure I would do this, but it is nice to know it is possible.

There are also a few Windows fronends, however last time I checked they were a bit under developed and buggy, but they do work to a point.

---

### Post by dannyboy79 on 2007-11-29
if you still want to utilize your xbox on a different tv and also go to mythtv, there's a python script you can put in the scripts folder of xbmc and it's a mythtv frontend which allows to watch recordings, see your backend status, see your upcoming recordings, edit or even make new recording schedules. Supposedly you can even watch live tv but I can't get it to work.

---

### Post by newlinux on 2007-12-01
One thing to keep in mind is that the mythvideo plugin you will be using to play myth files of SAMBA shares expects all files to be stored in one directory tree. So if you have files spread all over the place you'll need to use mountpoints and symlinks to get them all in one directory tree. just an FYI, but yes it can do what you want... Haven't ran into a format that I couldn't get to play (non-DRM formats, that is).

I love the emulators. I don't play any new games, but PSX and super nintendo and nintendo games are all I need...

---

