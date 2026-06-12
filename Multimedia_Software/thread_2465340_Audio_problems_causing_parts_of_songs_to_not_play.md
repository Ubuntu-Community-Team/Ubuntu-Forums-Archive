---
title: "Audio problems causing parts of songs to not play"
date: 2021-07-29
forum: Multimedia Software
---

### Post by goodstuff9 on 2021-07-29
I apologize in advance for how I am stating my question.  I am not an audio person, the whole audio setup confuses me.  I’m stating my question the best I know how.  I can supply more information if I’m told what is needed.  


Up until recently all worked just fine, I do not know what changed recently to cause the problems I’m having.  


Ubuntu 18.04.5 on a desktop computer, using Pulse Audio.  


A couple weeks ago I tried playing the Beatles song, “Back in the USSR.”  I was playing it on speakers sitting on my desk attached to my computer.  It didn’t sound right – at about the 1:25 mark where a guitar solo plays, I could not hear it at all.  I could hear the rest of the song, but not that part.  As I experimented with a number of other songs, I noticed on several of them there were parts that I could not hear.  Then, I discovered that if I made a bluetooth connection to a pair of headphones and listened to the song, everything sounded as it should.  


I tried different applications playing through the speakers on my desk:  VLC, Rhythmbox, Totem, SMPlayer, all had the same problem.  I even created a virtual machine (using Boxes) for Xubuntu, did not alter any of the out-of-the-box audio settings, went to YouTube to play the same song with the audio coming out of the host Ubuntu system, still had the same problem.  


I eventually discovered that if I played the song “Back in the USSR” on my speakers on my desk using VLC, but selected the audio setting to make the “Stereo Mode” be “Mono”, everything sounded just fine.  When I tried SMPlayer again, and made the audio setting for “Stereo Mode” to be “Mono”, it sounded fine using SMPlayer as well.  


But for Rhythmbox and Totem, and YouTube in a web browser, there is no “Mono” setting (that I could find).  


When I used Audacious, I could hear all the parts of the song, but it sounded just awful – kind of distorted, kind of like the wrong parts of the song were amplified.  I could not find a “Mono” setting in Audacious, either.  


All this leads me to think that there is something wrong with some overall audio setting on my computer.  I know that the “Mono” setting “works” in SMPlayer and in VLC, but I shouldn’t have to be messing with that for each application, should I?  Anyway, that setting doesn’t seem to exist in all applications.  I never had to mess with this in the past.  


So….  I’m looking for guidance on how to determine what is wrong with the audio setup on my computer, and how to fix it.

---

### Post by tea for one on 2021-07-30
Sound to bluetooth headphones = good
Sound to speakers = bad

Sounds like (pun intended) dodgy hardware, cable, socket connection or even the speakers themselves.

If the speakers are connected by line-out or usb, can you remove them and try some wired headphones or similar?

---

