---
title: "DVD help!"
date: 2009-11-30
forum: Multimedia Software
---

### Post by Waldvogel on 2009-11-30
I'm on Ubuntu 9.10 and I would like to watch a DVD.
But even with VLC the file cannot be read.
How could I watch DVDs?

Also could someone recommend a good programme I could play CDs and store the music?
I.e something which fulfils the same quota as Windows Media Player.

---

### Post by jacobs444 on 2009-11-30
sudo apt-get install ubuntu-restricted-extras libdvdread4 amarok

i think amarok will rip and save music.

---

### Post by Waldvogel on 2009-11-30
That looks like some kind of command-do I enter this in Terminal?

Thanks for the advice.

---

### Post by xc3RnbFO8P on 2009-11-30
In Terminal (Karmic Koala):
> sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
> sudo apt-get install libdvdcss2
> sudo apt-get install w32codecs
> sudo apt-get install libdvdread4
> sudo /usr/share/doc/libdvdread4/install-css.sh
> sudo apt-get install ubuntu-restricted-extras

---

### Post by SuperSonic4 on 2009-11-30
For dvd install **libdvdcss** as above

For Music I'd suggest K3B to rip (it also burns CDs, unlike brasero which burns coasters) and either Amarok or Exaile to play

---

### Post by Waldvogel on 2009-11-30
Your Terminal instructions were perfect thank you.

---

