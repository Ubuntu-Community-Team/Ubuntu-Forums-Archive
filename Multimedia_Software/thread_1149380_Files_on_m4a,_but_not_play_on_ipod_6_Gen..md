---
title: "Files on m4a, but not play on ipod 6 Gen."
date: 2009-05-05
forum: Multimedia Software
---

### Post by azmo35 on 2009-05-05
:(Hi,i have this question? If i rip cds to AAC "m4a" on audio cd extractor in Ubuntu they play just fine on rhythmbox, but when i try play them on itunes/ipod/quicktime nothing, no sound. Any suggestions will be appreciated thanks.

---

### Post by azmo35 on 2009-05-05
Help me please](*,)

---

### Post by azmo35 on 2009-05-06
](*,)Please,Please,Please,help me,thanks.

---

### Post by AlanR8 on 2009-05-06
I've had a similar issue with m4a files in Songbird so I just converted them all to mp3 files using soundkonvertor.

---

### Post by azmo35 on 2009-05-06
Mate my problem is not on play them in ubuntu but on ipod, well on windows,so if i rip on itunes and them play back on ubuntu play just fine but not vice versa, but thanks.

---

### Post by mc4man on 2009-05-06
It's probably encoding using the 'main' profile where you'll need the LC profile.
Any decent ripper/encoder should default to LC (grip, rubyripper, abcde, ect.

Not sure if audio cd extractor uses the gstreamer pipeline, if so in hardy and probably intrepid it defaults to 'main' profile.

If so you can edit the gstreamer pipeline for AAC to use 'profile 2' though I'm not the one to ask in regards to gstreamer

I believe it would be something basically like this (get confirmation first
> audio/x-raw-int,rate=44100,channels=2 ! faac profile=2 ! ffmux_mp4

mediainfo is good to get info (pick your ubuntu ver. you need to dl the 2 libs and the gui, install the libs first (libzen0 first) then open mediainfo and drop your track into

[http://mediainfo.sourceforge.net/en/Download](http://mediainfo.sourceforge.net/en/Download)

---

### Post by azmo35 on 2009-05-06
mc4man that is correct but the problem is that if i play them on windows/itune/ipod no sound, any sugestions,thanks.

---

### Post by mc4man on 2009-05-06
Atm I'm on a live jaunty cd building something so at a bit of a disadvantage to showing some things

Have had no problem adding albums in .m4a format to my ipod when ripped to LC and tagged half decently.
As far as playback with itunes on my vista laptop same thing

Grip works good, I've always used rubyripper and now abcde. I believe if you encode with faac they'll get tagged, I use neroAacEnc which was a pain to tag in rubyripper.
Atm I've got abcde ripper using neroAacEnc, atomicparsley to encode and tag

Are you producing LC .m4a's will some basic tags?

are you still using hardy? (my main install

---

### Post by azmo35 on 2009-05-06
mc4man, you lost me,yes i'm still in hardy, but i'm not sure about this but in itunes the rips hare like this mpeg-4 aac "codec" on ubuntu/audio cd extractor is mpeg-4 aac(Lavf1d.51.10.0)"codec" maybe this help or not, thanks again.

---

### Post by mc4man on 2009-05-06
Here are 2 screens maybe can clear up, Note the extension is .m4a

The first screen is a track ripped by itunes in vista

The 2nd shows a track ripped in ubuntu that plays fine in itunes in vista

In this case I used neroAac, but the only thing that matters is highlighted (and I believe you should have a couple of tags at the min. (for itunes

Screens from mediainfo in html view

Can you post a mediainfo screen (or you can copy and paste from the 'text' view

---

### Post by logos34 on 2009-05-06
the gstreamer pipeline for aac that mc4man gave you is the right one--*should* work according [to this]("https://help.ubuntu.com/community/CDRipping#AAC%20Encoding"). 

You can also get more options by running:

> gst-inspect faac

My advice is to do as suggested above and switch to a [different ripper]("https://help.ubuntu.com/community/CDRipping#Other%20CD%20Ripping%20Software").  Just forget sound juicer/cd audio extractor--it's needlessly complicated to configure codec rip settings, and the gstreamer-plugins since Gutsy are screwing up mp3 vbr output--I had to rollback to Feisty-era gstreamer (from 0.10.7.0 to 0.10.5.2) to fix mine (I only use soundjuicer/audio extractor for troubleshooting purposes).  Wouldn't surprise me if there's also a problem in how it handles aac/m4a.

hope that helps

---

### Post by azmo35 on 2009-05-06
Ok, ther is what you ask 1-st rip on vista, 2-sc on ubuntu | audio cd extractor,thanks again.

---

### Post by mc4man on 2009-05-06
from ubuntu

> Format version                   : Version 4

Format profile                   : Main   [COLOR="Red"]<---[/COLOR]

from itunes

> Format version                   : Version 4

Format profile                   : LC

You've either got to edit your AAC gstreamer profile to use 'profile 2' or use a better ripper (non gstreamer

(note : jaunty gstreamer now defaults to profile 2 (LC)

---

### Post by azmo35 on 2009-05-06
ok,> You've either got to edit your AAC gstreamer profile to use 'profile 2' or use a better ripper (non gstreamersince you have being so heplfull, can you guide me for the edit of the gstreamer, and for the better riper which one, thanks again.

---

### Post by azmo35 on 2009-05-07
mc4man, I apologize you were right from the beginning
> audio/x-raw-int,rate=44100,channels=2 ! faac profile=2 ! ffmux_mp4 and I have this > audio/x-raw-int,rate=44100,channels=2 ! faac profile=2 ! mp4muxso I make a new profile on sound juicer add > 
audio/x-raw-int,rate=44100,channels=2 ! faac profile=2 ! ffmux_mp4 with extencion to m4a and this solve my problem,thanks to all that reply.

---

