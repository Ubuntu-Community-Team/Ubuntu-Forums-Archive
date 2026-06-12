---
title: "audio-cd ripping"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by polopolo on 2007-05-30
Hello all.

Sometime, I buy christan audio-cd's, and I want to rip it into amarok.
is it possible in amarok or another program in kubuntu?

Regards,
Polopolo

---

### Post by aysiu on 2007-05-30
I believe it's possible in AmaroK. I don't have Kubuntu installed, so I don't know the exact steps.

---

### Post by malspa on 2007-05-30
you can use something like k3b to rip them and then play them in amarok, that's what I do

I don't think amarok will rip them, though

---

### Post by aysiu on 2007-05-30
> **malspa said:**
> you can use something like k3b to rip them and then play them in amarok, that's what I do

I don't think amarok will rip them, though
I think AmaroK might *appear* to rip the CD but actually call on an external program like *cdparanoia* or even *k3b*.

---

### Post by malspa on 2007-05-30
from the amarok handbook:

3. How can I rip/encode Audio-CDs with Amarok?

  Insert your CD, then click on "Play Audio CD" in the menu. The File-Browser will come up and show a tree with several folders. For normal ripping, go to the "wav" folder, select some tracks and drag them to the desired destination in a Konqueror window. For automatic encoding, drag files from the "mp3" or "ogg" folder instead.
Note
CD-ripping requires the "AudioCD KIO-slave" to be installed. It is part of KDE-Multimedia.

---

### Post by polopolo on 2007-05-30
Thank you for all you're help!

---

### Post by Steveire on 2007-05-30
There's a great way to rip cds in kubuntu:

[list]
[*] Insert CD and open konqueror
[*] Type audiocd:/ in the address bar.
[/list]
This will show folders named according to various formats (ogg, mp3, wav). You just copy the folder of the format you want and kde takes care of the rest. Neat, no?

---

