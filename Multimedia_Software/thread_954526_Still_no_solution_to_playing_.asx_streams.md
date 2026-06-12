---
title: "Still no solution to playing .asx streams?"
date: 2008-10-21
forum: Multimedia Software
---

### Post by nvlx80 on 2008-10-21
I´ve been trying to get .asx streams playing on my Ubuntu, read various discussions, still no success.

Is there anyone who succeeded in playing .asx. files?? Please share your success stories as, at the moment there seems to be no solution out there.

PS: the specific file I want to get playing is [http://meta.as34763.net/content/14.asx](http://meta.as34763.net/content/14.asx)

---

### Post by lulacLilla on 2008-10-21
I had the same problem. You can´t play asx´s under Ubuntu.

---

### Post by wolfen69 on 2008-10-21
probably because it is part of Microsoft Advanced Streaming Format.

---

### Post by kostkon on 2008-10-21
I can play *ASX* streams just fine. Do you have the *Windows* codecs package (called *w32codecs*) installed? It is offered by the [*Medibuntu* repository]("http://medibuntu.org/").

---

### Post by greyspoke on 2008-10-22
What exactly are you doing to achieve that kostkon?  I have w32codecs installed and can play things from files, but not the same files when delivered from a streaming server.

---

### Post by kostkon on 2008-10-22
> **greyspoke said:**
> What exactly are you doing to achieve that kostkon?  I have w32codecs installed and can play things from files, but not the same files when delivered from a streaming server.
I don't do anything special. The only thing that I do differently is  that I don't use the default *Totem* (*totem-gstreamer*) that comes with *Ubuntu* and uses *Gstreamer* as its backend, but *totem-xine* that uses the *Xine* backend.

---

