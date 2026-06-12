---
title: "Python 2.7- minimal requires additional plugin for this operation."
date: 2013-10-07
forum: Multimedia Software
---

### Post by bill23 on 2013-10-07
[FONT=franklin gothic medium][SIZE=4]I have some Midi's in my Music Folder. Everytem I try to play them I get "Pythin 2.7-minimal requires an addtional plugin for this operation" Then the message continues with : "The followin plugin is required; audio/midi decoder. 

In the Software Center I did a search for that and came up with; MPEG 4 Structured Audio Decoder, sfront. I installed it as well as gstreamer0.10-plugin-ugly and gstreameer0.10-plugin-bad and a number of Apps that had the name Pyhthon in them that were some how related to audio. None of that maed any difference i still get the sam message: "Python 2.7-minimal requires addtional plugin for this operation.'

I have no problem listening to any of the videos I watch in YouTube or the video's my email may have a link to. But I can't lisen to those Midi's in my Music Folder.

It is frustrating.

bill23


[/SIZE][/FONT]

---

### Post by bill23 on 2013-10-08
I had hoped to have had at least one person posting a suggestion on this dilemma. Perhaps the problem is in the Title of this thread? Would it have made any difference if the 'Title' had read  "Midi's won't play because they need additional plugin." 

bill23

---

### Post by Yellow Pasque on 2013-10-09
What Ubuntu version do you have and what program are you trying to use to play them? You may need gstreamer1.0-plugins-bad installed.

---

### Post by mc4man on 2013-10-09
> **Temüjin said:**
> What Ubuntu version do you have and what program are you trying to use to play them? You may need gstreamer1.0-plugins-bad installed.
prior posts suggest 13.04

---

### Post by bill23 on 2013-10-11
I have tried to use Gnome Media Player, Rhythm Box, MPlayer, and Parole, more on that one later. I've gsteamers0.10 good, bad an they ugly. i am running Ubuntu 13.04

---

### Post by Yellow Pasque on 2013-10-12
> **bill23 said:**
> I've gsteamers0.10 good, bad an they ugly

Okay, but you need gstreamer**1.0** good/bad/ugly packages since rhythmbox now uses **1.0**...

---

