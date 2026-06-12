---
title: "Having gtkpod convert ogg to mp3 (or have iPod play AAC) help needed"
date: 2009-01-13
forum: Multimedia Software
---

### Post by SlaughterDog on 2009-01-13
I've got an iPod shuffle, which unfortunately plays only MP3 and AAC. Given the two choices, I first chose AAC but unfortunately using either Hipo or gtkpod, when I transfer the files to the iPod, it won't play them. It will play MP3 though, so I figured I could rip my CDs to my computer in OGG format and have gtkpod autoconvert them to MP3. However, I get errors such as: Conversion of 'Paradigm Shift' failed: '/usr/share/gtkpod-aac/scripts/convert-2mp3.sh   ' returned exit status 5.

Can anybody help me? Perhaps you know of alternative iPod managers?

---

### Post by logos34 on 2009-01-13
well, you could try Amarok--works well with ipod shuffle, I hear (i don't have an ipod nor will I ever probably).  It's also the best music organizer IMO.  I run it without problems on my gnome de.

---

### Post by giovex on 2009-11-01
the error you get is 5 therefore the problem is with encoding back into mp3. Try installing a package called lame (mp3 encoder) with synaptic, it resolved the problem for me. if the encoding you need is to aac, then the package needed is called faac (aac encoder).

---

### Post by surfernsk on 2010-01-17
> **SlaughterDog said:**
> I've got an iPod shuffle, which unfortunately plays only MP3 and AAC. Given the two choices, I first chose AAC but unfortunately using either Hipo or gtkpod, when I transfer the files to the iPod, it won't play them. It will play MP3 though, so I figured I could rip my CDs to my computer in OGG format and have gtkpod autoconvert them to MP3. However, I get errors such as: Conversion of 'Paradigm Shift' failed: '/usr/share/gtkpod-aac/scripts/convert-2mp3.sh   ' returned exit status 5.

Can anybody help me? Perhaps you know of alternative iPod managers?

sudo aptitude install vorbis-tools lame faac faad

---

### Post by B0rat on 2010-01-19
> **giovex said:**
> the error you get is 5 therefore the problem is with encoding back into mp3. Try installing a package called lame (mp3 encoder) with synaptic, it resolved the problem for me. if the encoding you need is to aac, then the package needed is called faac (aac encoder).


Thank you! Helped me while Googling for this error ;)

---

### Post by mr_frostee on 2011-07-12
For anybody else as dumb as myself:  make sure to have the codec installed for the filetype you are converting FROM as well as to.  Thought I had FLAC installed and spent a lot of time chasing my tail only to discover the problem was not the encoder, it was my lack of the proper decoder.

> sudo apt-get install flac

That would have saved me a lot of time and frustration.  Hope it helps somebody down the road.

---

