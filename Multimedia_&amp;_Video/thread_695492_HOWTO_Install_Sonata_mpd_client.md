---
title: "HOWTO: Install Sonata mpd client"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by Emblem Parade on 2008-02-13
Sonata is in the repositories, but not in good shape.

1. There's an updated package for Gutsy available at the Sonata site. For Ubuntu, it's only 1.4.1, but you can install the 1.4.2 Debian package without any trouble. (Version 1.4.1 has a bug which won't let you move the progress bar.)

2. To get Ubuntu's installation of Sonata to fetch lyrics and edit tags, simply install these packages:

```
sudo aptitude install python-zsi python-tagpy
```

In my opinion, mpd with Sonata is the most elegant way to play music on Ubuntu. mpd impresses me with how well it handles my very large collection (of all the other players, only Amarok with MySQL could handle it, but Amarok is a beast, especially when you're running GNOME). Sonata impresses me by being just such a perfectly minimalist application, and yet nicely customizable, that it's a pleasure to use. I haven't enjoyed a desktop music player so much since foobar2000 on Windows! (By the way, foobar200 runs reasonably well on WINE, if you miss it.)

Why isn't all this in the repos? It's really too bad that this killer combo is isn't packaged well in Gutsy! Hopefully this will be fixed for Hardy.

(By the way, Sonata can handle Last.fm scrobbling for you, but that's one thing that I'd rather have running separately. See my [HOWTO on getting lastmp to run on Gutsy]("http://ubuntuforums.org/showthread.php?t=695480"). Another bad package.)

---

