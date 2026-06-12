---
title: "Getting gnormalize set up properly"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by wilberfan on 2007-08-17
I have a big (360 tracks?!) conversion / normalize project coming up, and I can remember using gnormalize back in Edgy to great effect...

I've managed to get it installed and running in Feisty, but the following is displayed in a window inside of gnormalize when I start it up:

> Can't find "lame" in executable path. The output can't be "mp3" format.
Can't find "oggenc" in executable path. The output can't be "ogg" format.
Can't find "mac" in executable path. The output can't be "ape" format.
Can't find "flac" in executable path. The output can't be "flac" format.
Can't find "faac" in executable path. The output can't be "mp4" format.
Can't find "metaflac" in executable path. 
Can't find "normalize" in executable path. The wav files can't be normalized.
Can't find "oggdec" in executable path. The input can't be "ogg" format.
Can't find "faad" in executable path. The input can't be "mp4" format.
Can't find "vorbiscomment" in executable path. 
Can't find "ogg123" in executable path. OGG files can't be played!
Can't find "play" in executable path. APE files can't be played!

I've installed "ubuntu-restricted-extras"--but I'm kind of at a loss on how to get all of the above into wherever it needs to get to...!  :confused:

---

### Post by wilberfan on 2007-08-18
[ polite nudge ]

---

### Post by bourgo on 2007-10-20
Just happened to bump into this one; if you're already sorted out, maybe this will help someone else. Gnormalize is in Asher256's repository ([http://asher256-repository.tuxfamily.org/index.php?page=faq&lang=en](http://asher256-repository.tuxfamily.org/index.php?page=faq&lang=en)). Officially it's only supported for breezy, dapper and edgy, but the packages in the communal repository for these three releases will work just fine on feisty and even gutsy (at least gnormalize does). Add the following repository and install via synaptic. 

deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org)  ubuntu main dupdate french

Don't forget to take a look at the recommended packages and marking what you need (right click -> mark recommended for install); for full functionality just mark them all.

---

