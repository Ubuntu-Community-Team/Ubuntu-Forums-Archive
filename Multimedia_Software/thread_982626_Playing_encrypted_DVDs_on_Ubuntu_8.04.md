---
title: "Playing encrypted DVDs on Ubuntu 8.04"
date: 2008-11-14
forum: Multimedia Software
---

### Post by fatsheep on 2008-11-14
I don't remember configuring Ubuntu to play DVDs ever being this hard.  I'm on a relatively unmodified Ubuntu 8.04 install and I've already tried installing lots of codecs from various howto's. I've been using VLC, totem, and xine in my attempts to play the DVD.  I have been unsuccessful so far.

Could I get some help on playing an encrypted DVD (I'm testing with "Batman Begins").  Thanks. :KS

---

### Post by mc4man on 2008-11-14
After installing vlc the only additional package needed is libdvdcss2. Check on that.

If no go start vlc from the terminal and then attempt playback of the disk. See what shows up in the terminal output.
(are you using the standard hardy version of vlc 0.8.6?

Xine additionally requires libxine1-ffmpeg

---

### Post by Yellow Pasque on 2008-11-15
Add the medibuntu repos to your software sources. It makes life easier. [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by mrhelpman on 2008-11-15
> **fatsheep said:**
> Could I get some help on playing an encrypted DVD (I'm testing with "Batman Begins").  Thanks. :KS

I am not an expert in DVD viewing so someone may suggest a better solution but I think you will need to have libdvdcss installed on your system. If it is not available from the repositories (apt-get install libdvdcss) then you may have to build from source. I have always had to do this but I am running a version of ubuntu that is a little older than 8.04

reply if you want more help on building from source.
JT

---

