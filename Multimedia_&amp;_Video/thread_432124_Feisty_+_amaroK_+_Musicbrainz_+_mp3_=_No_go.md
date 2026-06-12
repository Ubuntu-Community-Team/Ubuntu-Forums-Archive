---
title: "Feisty + amaroK + Musicbrainz + mp3 = No go?"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by Archmage on 2007-05-03
When I'm trying to let amaroK search with the help of Musicbrainz for the artist and title of my MP3 than I either got the information that Musicbrainz isn't install to use MP3s or after installing the right package it use 100% of my CPU and never finish.

HOW can I make amaroK and Musicbrainz work so that they can search titles and artist of my MP3s?

---

### Post by jollemeyer on 2007-08-08
Same problem here.

Please help.

---

### Post by jollemeyer on 2007-08-08
Fixed it myself:
see  [http://www.howtogeek.com/howto/ubuntu/fix-amarok-error-fingerprinting-of-mp3-files-is-not-supported/](http://www.howtogeek.com/howto/ubuntu/fix-amarok-error-fingerprinting-of-mp3-files-is-not-supported/)

All you need to do is completely close down Amarok (make sure it's not in the tray either), and then open up a terminal and run the following command:

    sudo apt-get install libtunepimp5-mp3

Restart Amarok, and you should be able to immediately start using MusicBrainz

---

