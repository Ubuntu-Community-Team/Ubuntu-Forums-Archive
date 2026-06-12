---
title: "music converter app for Ubuntu 17.10 (lossless to MP3)"
date: 2017-11-16
forum: Multimedia Software
---

### Post by mrjayviper on 2017-11-16
looking for music converter that can save the output into individual folders


example: /home/my-user/Music/album-artist-here/album-here/track-here


I've tried:



[LIST=1]
[*]sound converter: does what I want BUT I  converted FLAC to MP3 _several times_ and the all tags (track number, title, album, artists and etc) are missing! I installed this app from the official Ubuntu repo.
[*]curlew - no option to save files on individual folders. from what I've seen, can only be installed by downloading the .deb file
[*]soundkonverter - not available on official repos. I've looked at 3rd party repo (click [here]("https://launchpad.net/~dominik-stadler/+archive/ubuntu/dsta-artful-ppa/+packages") for repo link) and the app didn't build for 17.10. issues with a library from what I've seen
[/LIST]

Any ideas what I could be doing wrong?


I can run dBpoweramp (a very powerful and intuitive sound conversion tool) using Wine but I'm trying to use native apps as much as possible.

Thanks!

---

### Post by ian-weisser on 2017-11-16
Funny, this looks exactly like the same question you just asked in AskUbuntu.

---

### Post by mrjayviper on 2017-11-16
> **ian-weisser said:**
> Funny, this looks exactly like the same question you just asked in AskUbuntu.

indeed. but this is a different forum? :)

at least as far as I know :)

like askubuntu is managed by stackexchange while ubuntuforums seems to be managed by Canonical...

---

### Post by wildmanne39 on 2017-11-16
It is okay to ask the question in both places as long as you do not use the formatting from ask ubuntu here, when you copy and paste it.

---

### Post by QIII on 2017-11-16
The Ubuntu Forums is hosted on Canonical's servers, but it is "managed" by the volunteer staff here.

Cross posting between sites is certainly nothing we can stop, nor do we have any particular interest in making the effort to do so.  But it isn't proper netiquette.  What happens, for instance, if volunteers here spend their time helping you and you get your answer there (or vice versa)?  Will you (not you in particular, but as a general case) just walk away from one or the other leaving one of the communities in the dark without a solution?

Just a request:  if you get your answer there, will you please share it?  Share it on Ask Ubuntu if you get the answer here?

Cheers!

---

### Post by VanillaMozilla on 2017-11-17
[LIST=1]
[*]sound converter: does what I want BUT I  converted FLAC to MP3 _several times_ and the all tags (track number, title, album, artists and etc) are missing![/LIST]
[/QUOTE]

Works for me, except doesn't save year.

As a wild guess, perhaps a user error?  Maybe you edited metadata, then saved it to wrong directory?  Some programs do not save data to same directory you opened from.  That happened to me when I first tried it.

---

### Post by Yellow Pasque on 2017-11-17
Make sure you have gstreamer1.0-plugins-bad package installed for id3 tag support.

---

### Post by mrjayviper on 2017-11-18
> **Temüjin said:**
> Make sure you have gstreamer1.0-plugins-bad package installed for id3 tag support.

that fixed my problem!

This soundconverter page ([http://soundconverter.org/gstreamer-mp3-encoding-howto/](http://soundconverter.org/gstreamer-mp3-encoding-howto/)) only mentions installing ugly which enabled MP3 encoding. no mention of the bad plugins. Thank you so much!

---

