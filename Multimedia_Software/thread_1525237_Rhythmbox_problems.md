---
title: "Rhythmbox problems"
date: 2010-07-06
forum: Multimedia Software
---

### Post by jmfal on 2010-07-06
Just installed 10.04 ,I like it no problems. My printer even works!
I managed to add two music-cd's to the library, while adding another one a error window popped-up: error transferring track
               unable to locate encoding profile for mime-type

Everything else in rhythmbox works and sounds good. No errors or glitches while installing. Should note that I'm using 64bit.

---

### Post by lidex on 2010-07-07
Try this, in a terminal:
```
sudo cp /usr/lib/libtotem-plparser.so /usr/lib/libtotem-plparser.so.12
```

---

### Post by jmfal on 2010-07-07
LIDEX thanks for reply.  tried that in terminal , could not open no such file in directory
  I was going to try to purge rhythmbox and reinstall but I dont know the correct command

---

### Post by lidex on 2010-07-07
```
sudo aptitude purge rhythmbox
```
I think will work. If not substitute apt-get for aptitude. Before the re-install, I would go into your home folder and delete anything pertaining to rhythmbox - those would be config files not removed that may be problematic.
To find:
```
sudo updatedb
locate rhythmbox
```

---

### Post by jmfal on 2010-07-08
lidex tried those commands, updateb no command found 
 did complete removal and reinstalled through synaptics, still same error
when I opened rhythmbox my music that Iripped was still there, shouldn't it have been deleted???
 thx for reply, keep'em coming I know there's a fix for this somewhere

---

### Post by jmfal on 2010-07-08
bump

---

### Post by jmfal on 2010-07-10
As of now I, haven't solved my problem but I have a way around it:::

applications>sound-video> audioCDextracter(soundjuicer)

open audioCDextr >pop in cd > hit extract button

click on edit>preferences make sure music folder set to music

set track names how you want

set format to your liking (cd losess)

I'm trying guayadeque,amaork, and rhythmbox update library and you'll have all your cd music on your player.

I hope this helps the newbie like me, or the ones who are afraid of the terminal

---

### Post by emotionlovesyou on 2011-01-02
This may also not be the solution you're looking for but, USE BANSHEE

I used Rhythmbox for the longest time. It's an amazing program but Banshee is just a bit better. And I no longer experience the CD ripping problem which I too experienced in Rhythmbox. Check it out if you can't get it to work: [http://banshee.fm]("http://banshee.fm/")

---

