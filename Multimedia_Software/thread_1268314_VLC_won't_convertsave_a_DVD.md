---
title: "VLC won't convert/save a DVD?"
date: 2009-09-16
forum: Multimedia Software
---

### Post by cfogelberg on 2009-09-16
Hi all,

I'm trying to convert a DVD I have using VLC, but it generates a weird error message:

> Playback failure:
DVDRead could not open the disk "/dev/sr0@1 :audio-track=1 :sub-track=1".
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0@1 :audio-track=1 :sub-track=1'. Check the log for details.

This is especially weird as VLC plays the DVD fine...

If anyone can offer any help that'd be great!

Thanks,
Christo

---

### Post by vinutux on 2009-09-17
VLC is just a mediaplayer.....convert fuctions is not working good like video converters and dvd rippers.....

use dvd rippers like Handbrake, thoggen, K9copy for ripping videos from dvd:)

---

### Post by Labello on 2009-09-17
> **vinutux said:**
> VLC is just a mediaplayer.....convert fuctions is not working good like video converters and dvd rippers.....

use dvd rippers like Handbrake, thoggen, K9copy for ripping videos from dvd:)

Sorry but this is complete Nonsense. VLC is NOT just a videoplayer. First of all it is as the name suggests a client for a huge range of mediafiles broadcasted over a huge range of protocolls. So it first of all it is very capable of handling video streams. Thus it is able to stream into any fileformat you find logical.

So just open up a stream, direct it into a file, setup the codec and containers as you whish and you are done.

Make shure that you have got the package "libdvdcss2" installed to ashure that your playback of DVDs goes flawlessly.

As far as i know, the latest vlc, that kan be found in their official repo even has got a menu entry called "convert"

---

### Post by pattinsonrobert on 2009-09-17
Hi Everyone..

My VLC media player has been acting up. when ever I am watching a movie the player for no reason switches to 4:3 ration or 16:9 or makes the volume loud or quiet. its really weird what do you recommend? i am running on a vista system

---

### Post by rob-ward on 2009-09-17
> **pattinsonrobert said:**
> Hi Everyone..

My VLC media player has been acting up. when ever I am watching a movie the player for no reason switches to 4:3 ration or 16:9 or makes the volume loud or quiet. its really weird what do you recommend? i am running on a vista system

Install Ubuntu... Other than that right click on the video pane and then go to video, in there you can specify the aspect ratio instead of default, I think that should keep the aspect ratio fixed(you will have to try) as for your audio I don't have any ideas(are you sure that the media was encoded with equalised audio and it isn't the volume in the audio changing???)

---

### Post by mc4man on 2009-09-17
> I'm trying to convert a DVD 
Probably better to go from the streaming option, disc, and pick 'no dvd menus' (dvdsimple) 

( are you trying to 'convert' to another format (realtime+) or 'rip' to mpeg-ps (6 -10  mins for main title

---

