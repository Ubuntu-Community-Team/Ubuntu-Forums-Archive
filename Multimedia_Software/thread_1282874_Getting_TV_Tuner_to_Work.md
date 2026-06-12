---
title: "Getting TV Tuner to Work"
date: 2009-10-04
forum: Multimedia Software
---

### Post by ks0ft on 2009-10-04
Hi folks,

I am having a heck of a time trying to watch Cable Television on my linux box.  I purchased a card because the linuxtv.org folks specifically point out that it is in fact compatible with the built-in drivers. 

With VLC i get a beautiful picture but cannot change channels because VLC requires that all the channels be predefined in it's configuration tool.  So If I want to watch one channel all day long this would probably work hehe.

TV Time doesn't work because the driver doesn't have any I/O streaming API.

MythTV can actually scan the channels but it's far too bulky to play in a little window while I'm gaming (plus I never really got it working )

xine, mplayer, these are all great but they require a channels.conf ... and I've had no luck using the scan or w_scan command in trying to create one - all of the initial tuner files appear to be for europe / satscan ... the atsc files just don't pick anything up off the tuner!

Ubuntu Version = 9.04
TV Tuner Card =  Hauppauge WinTV HVR 1600
Cable Service = Comcast (Houston, Texas)

So, if someone can tell me how I can create a proper channels.conf or get my card to work or have another TV Tuner app that can scan / and show TV I would really appreciate it, because right now I'm stuck!

Ks0Ft

---

### Post by jaakan on 2009-10-04
you might want to try this

[http://www.mythtv.org/wiki/Working_QAM_cable_layout](http://www.mythtv.org/wiki/Working_QAM_cable_layout)

Comcast does change the ClearQAM channels from time to time

---

### Post by Sin@Sin-Sacrifice on 2009-10-05
I have the same card and am looking for a channels.conf for time warner in NE Ohio. I tried the scan command but it doesn't find anything using the files in /usr/share/dvb/atsc. I have channels in mythtv but every time I need to change something it asks for a password that I defined but tells me it's wrong. Plus it doesn't like pulseaudio or ALSA whereas vlc's sound is nice. I actually want to use a script with elisa and channels.conf. Anything on the subject would be much appreciated and welcomed.

---

### Post by ks0ft on 2009-10-05
It's amazing how incredibly difficult this has been - i have seen that site before and tried to use the TW Channels.conf from the houston area circa 2007 but it doesn't seem to work for my Comcast service

---

### Post by ks0ft on 2009-10-06
[SIZE=2]I finally have a solution that works for me.  I learned that VLC could be launched with it's PVR interface directed to a frequency on the capture card, so I found a listing of frequencies from my cable provider that matched all of the channels I wanted to watch, I tested each one of them from the command line and got a good picture.  Then I took the same list and put it in to a VLC playlist so i can effectively change the channel using keyboard shortcuts designed to navigate a playlist.  Kind of a hack, but it works for me !

-kS0fT
[/SIZE]

---

### Post by HappyFeet on 2009-10-06
Check out the CSMonkey on screen TV "remote". Just right click, open with java. It works for my PVR150. [http://sourceforge.net/projects/tvremote/](http://sourceforge.net/projects/tvremote/)

---

