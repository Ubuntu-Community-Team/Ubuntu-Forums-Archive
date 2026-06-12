---
title: "KMid Midi player help... PLEASE"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by Centrex on 2007-04-17
Ok, i have downloaded and installed the KMid midi player from the "Add/Remove" software thing in the applications menu, but when ever i start it up it just tells me that /dev/sequencer Probably another program is using it.

[IMG]http://i111.photobucket.com/albums/n158/Storm984/Screenshot.png[/IMG]

Please help me. Thanks. :)

---

### Post by Zeroangel on 2007-04-21
I too am having problems with getting KMid working, but I work around that by using Timidity instead.
```
sudo apt-get install timidity timidity-interfaces-extra freepats
```And then running it using
```
timidity -ig
```That should bring up its user interface.

-----------
[This post]("http://ubuntuforums.org/showthread.php?t=363753") might help you get around the error, but it didnt work for me since i'm having a different problem with kmid.

---

### Post by Zeroangel on 2007-04-22
Found another thing too. I can run KMid using the timidity backend by enabling timidity's ALSA interface in /etc/default/timidity . Nice!

---

