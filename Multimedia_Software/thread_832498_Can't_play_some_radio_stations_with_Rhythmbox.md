---
title: "Can't play some radio stations with Rhythmbox"
date: 2008-06-17
forum: Multimedia Software
---

### Post by Dlizard on 2008-06-17
Does someone know why I get the message "Couldn't start playback - Unknown playback error" when I try to play some stations (like BBC, RAI and Deutsche Welle) with Rhythmbox Music Player (even though I can listen to them on the Web)? I am puzzled by the fact that I can listen to some other stations (like Radio France and Radio Switzerland) with Rhythmbox without any problem. :confused: Is there any way to fix this?

---

### Post by ubume2 on 2008-06-18
Bump
Would be interested in getting BBC on Rhythmbox too. Can get other stations working using the list from:

[http://wiki.xiph.org/VorbisStreams](http://wiki.xiph.org/VorbisStreams)

---

### Post by Dlizard on 2008-06-18
> **ubume2 said:**
> Bump
Would be interested in getting BBC on Rhythmbox too. Can get other stations working using the list from:

[http://wiki.xiph.org/VorbisStreams](http://wiki.xiph.org/VorbisStreams)

I tried the stations on your list. I cannot listen to most of them on Rhythmbox either. For example, when I add [http://audio-ogg.ibiblio.org:8000/wcpe.ogg](http://audio-ogg.ibiblio.org:8000/wcpe.ogg) (a classic music station) and try to play it I get the message: "Couldn't start playback - Internal data flow error".:(

I can listen to that and other stations directly on the site though, so I guess it is a problem related to Rhythmbox.

---

### Post by ubume2 on 2008-06-18
I did get some url links from the Shoutcast website that worked in rhythmbox.

For classical I found WETA, Colorado Public Radio, Classical Music Broadcast in Michigan, KING FM, KBAQ FM in Phoenix.  
[http://radio.michiganliveevents.com:8000/listen.pls](http://radio.michiganliveevents.com:8000/listen.pls)
[http://www.cpr.org/listen/live_classical.asx?classicalwebcast.com](http://www.cpr.org/listen/live_classical.asx?classicalwebcast.com)
[http://kbaq.org:8080/livestream/connect_high.pls](http://kbaq.org:8080/livestream/connect_high.pls)
[http://www.shoutcast.com/sbin/shoutcast-playlist.pls?rn=666903&file=filename.pls](http://www.shoutcast.com/sbin/shoutcast-playlist.pls?rn=666903&file=filename.pls)

[http://stream.weta.org:8002/listen.pls](http://stream.weta.org:8002/listen.pls)

Edit: for WCPE try this:
[http://www.ibiblio.org/wcpe/wcpe.pls](http://www.ibiblio.org/wcpe/wcpe.pls)

---

### Post by Dlizard on 2008-06-19
> **ubume2 said:**
> I did get some url links from the Shoutcast website that worked in rhythmbox.

For classical I found WETA, Colorado Public Radio, Classical Music Broadcast in Michigan, KING FM, KBAQ FM in Phoenix.  
[http://radio.michiganliveevents.com:8000/listen.pls](http://radio.michiganliveevents.com:8000/listen.pls)
[http://www.cpr.org/listen/live_classical.asx?classicalwebcast.com](http://www.cpr.org/listen/live_classical.asx?classicalwebcast.com)
[http://kbaq.org:8080/livestream/connect_high.pls](http://kbaq.org:8080/livestream/connect_high.pls)
[http://www.shoutcast.com/sbin/shoutcast-playlist.pls?rn=666903&file=filename.pls](http://www.shoutcast.com/sbin/shoutcast-playlist.pls?rn=666903&file=filename.pls)

[http://stream.weta.org:8002/listen.pls](http://stream.weta.org:8002/listen.pls)

Edit: for WCPE try this:
[http://www.ibiblio.org/wcpe/wcpe.pls](http://www.ibiblio.org/wcpe/wcpe.pls)

Except for the second one (cpr.org) I can listen to all of them. I still don't know why I cannot listen to some stations that present no problem to other people who use Ubuntu. Anyway, thank you for your list!

---

### Post by markbuntu on 2008-06-19
I usually need to try the different streams from the stations until I find one that works in rythmbox, usually the windows media stream. What I do is find the station with firefox and let mplayer start playing the stream then I copy the url from the properties setion there into the rythmbox add new internet station. Some work, some don't.

There are also a few stations that are using a new windowz proprietary format that is unusable in linux. If you find one of these, email the station and complain. They really want you to listen so they will do something about it if they get enough complaints.

---

### Post by Dlizard on 2008-06-24
> **markbuntu said:**
> I usually need to try the different streams from the stations until I find one that works in rythmbox, usually the windows media stream. What I do is find the station with firefox and let mplayer start playing the stream then I copy the url from the properties setion there into the rythmbox add new internet station. Some work, some don't.

There are also a few stations that are using a new windowz proprietary format that is unusable in linux. If you find one of these, email the station and complain. They really want you to listen so they will do something about it if they get enough complaints.

Yes, write and complain to radios, companies, etc, regarding products that do not work (hardware & software) is one of the best strategies that Ubuntu users should adopt in order to enjoy more compatibility in the future. 

Regarding BBC, I did write to them and got the following message. Unfortunately, it did not help much, but at least they answered...

"Many thanks for your message.

The BBC is not able to give specific technical advice to Linux users since one user's Linux configuration could be very different to the next. However we recommend that you follow the steps outlined on this community resource site:
[http://ubuntuforums.org/showthread.php?t=540412](http://ubuntuforums.org/showthread.php?t=540412)

Some users find that this problem goes away if you revert to Firefox 2, rather than using Firefox 3 in Ubuntu 8.04.

We hope this answers your query."

Best wishes,

BBC iPlayer Team

---

### Post by icheyne on 2008-06-27
> **Dlizard said:**
> []("http://ubuntuforums.org/showthread.php?t=540412")Some users find that this problem goes away if you revert to Firefox 2, rather than using Firefox 3 in Ubuntu 8.04.

This worked for me.

[https://answers.launchpad.net/ubuntu/+faq/95](https://answers.launchpad.net/ubuntu/+faq/95)

sudo aptitude remove firefox-3.0
I clicked "n" to the first solution and accepted the second one that installed Firefox 2

---

### Post by Porpoise on 2008-06-27
BBC Radio 1 ->     <http://www.bbc.co.uk/radio/aod/radio1_asx.shtml>

works fine in Mplayer

No idea why it won't work in the others!?!

---

### Post by markbuntu on 2008-06-27
Worldservice works for me in firefox3 and in totem as a standalone player. It does not work in rythmbox. I get an error:

text/html decoder plugin is required... but not installed.

I get this with a lot of radio stations on rythmbox but have no clue how to get rythmbox to use this plugin. It seems to be installed since other apps appear to be using it.

---

### Post by Porpoise on 2008-06-27
This URL works in Rythmbox:

[http://www.bbc.co.uk/radio1/wm_asx/aod/radio1.asx](http://www.bbc.co.uk/radio1/wm_asx/aod/radio1.asx)

---

### Post by Dlizard on 2008-06-27
> **markbuntu said:**
> Worldservice works for me in firefox3 and in totem as a standalone player. It does not work in rythmbox. I get an error:

text/html decoder plugin is required... but not installed.

I get this with a lot of radio stations on rythmbox but have no clue how to get rythmbox to use this plugin. It seems to be installed since other apps appear to be using it.

I get exactly the same error message when I try to open the aforementioned radio station with rythmbox.Same thing happens with some other stations like [http://www.classical963fm.com/player](http://www.classical963fm.com/player) (a Canadian classical music station). Frustrating!:(

---

