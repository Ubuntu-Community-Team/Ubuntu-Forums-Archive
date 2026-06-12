---
title: "not recignizing sound card"
date: 2006-03-22
forum: Multimedia &amp; Video
---

### Post by milen on 2006-03-22
Is there anything I can do to make the system recognize my sound card? It tells me I  don't have appropriate GStreamer plugin installed but actually I have - I've just installed all of them. So I suppose the problem should consist in something else. Maybe I haven't configured anything in the proper way, or something...

---

### Post by FarEast on 2006-03-27
Hi milen,

Let me help you;) .
Execute the command below to know if the system recognizes the sound card.
$ cat /proc/asound/cards

---

