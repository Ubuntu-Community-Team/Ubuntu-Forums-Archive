---
title: "Codecs in realplayer"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by willix on 2007-05-18
Hy,
On my new Ubutu 6.10 Edgy, I've installed totem (gstream), the codecs libraries and others and can read (so far) all the movies I need (mpg, wmv,...). 
I counldn't read a rtsp stream from the BBC web site so I installed Realplayer and that did the trick.

My problem is that I can't read my local files (mpeg, wmv) in Realplayer. It sais "The following components are required: mpg (or wmv)"

I thought these codecs and other required stuff was downloaded once, and then all the players would/could share them. Is'nt that so? If so, why is realplayer failing to read them but totem isn't?

Thanks

---

### Post by jrusso2 on 2007-05-18
The linux version of RealPlayer does not play wmv.  It does play ogg, rpm, and mp3

---

### Post by willix on 2007-05-19
Ok that explains why it doesn't play wmv. But why does it fail with the same kind of message for mpg? 

And although I have limited uderstanding on how things work behing the scene, if the difference between displaying an mpg and wmv or avi file is just the encoding, why can't realpayer decode and play an wmv file if it knows where to find the codec?

---

### Post by jrusso2 on 2007-05-22
I don't know but I would try xine or mplayer along with the w32 codecs to play those formats.  Real Player might not have the rights to those formats

---

