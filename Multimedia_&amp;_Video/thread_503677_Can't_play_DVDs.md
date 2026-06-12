---
title: "Can't play DVDs"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by eljoeb on 2007-07-18
Hmm, descriptive title.  I'm interested in playing (Legally obtained) DVDs in Ubuntu.  I followed the instructions in help, specifically "Play movies and videos" and I also installed everything listed in "Multimedia codecs" because I had no idea what I needed.

Whenever I start gxine and start the DVD, it says its playing a 3 second video (which happens to be black).  I tried VLC, I don't get anything.  Totem plays for three seconds and then says "Paused (Streaming)".  Mplayer doesn't seem to do anything when I press "play" after i select the DVD.

I understand very specific information is needed to help out in these circumstances.  Please tell me what information you will need.

Thank you in advance,

Joe

---

### Post by eljoeb on 2007-07-18
Nobody?

---

### Post by Teddy_P on 2007-07-18
Bump...
Same problem.


Teddy

---

### Post by RomeReactor on 2007-07-18
Hi. You can get instructions on how to enable DVD playback [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs"). Post back if you're having trouble with any of the steps.

---

### Post by dasunst3r on 2007-07-18
I would like to say that the most important thing to install is *libdvdcss2*.

---

### Post by Gremlinzzz on 2007-07-18
I play dvd with smplayer works good. im using smplayer package (Qt3; without KDE support)
[http://wesley.debianbox.be/packages/](http://wesley.debianbox.be/packages/)
if it doesnt work for you 
sudo apt-get autoremove smplayer
:guitar:

---

### Post by Teddy_P on 2007-07-18
I did this:
```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb
```

Then went in synaptic package manager and searched for Xine
Installed Totem-xine
Which removed Totem-gstreamer

The only reason was I did not want all of the non-free stuff just what it took to play a dvd.


Teddy

---

