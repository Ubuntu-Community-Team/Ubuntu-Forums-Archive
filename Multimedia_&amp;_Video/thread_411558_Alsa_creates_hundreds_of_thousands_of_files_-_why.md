---
title: "Alsa creates hundreds of thousands of files - why?"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by jussiam on 2007-04-17
I'm using Amarok and just noticed that after Amarok has been up and running for over a week I found **230778** files form my /tmp. All the files were named like "alsa-dmix-6698-1176186902-966307".

What are these files and why are they clobbering my harddrive?

---

### Post by deadgobby on 2007-04-17
What are you doing with Amarok to create all those files?
Gobby

---

### Post by jussiam on 2007-04-17
> **deadgobby said:**
> What are you doing with Amarok to create all those files?
Gobby

Listening to my mp3 collection :-)

I took another look and it seems that all those files are actually sockets!

```
cpt2jmo@batman:/tmp$ file alsa-dmix-6698-1176790334-498435
alsa-dmix-6698-1176790334-498435: socket
```

---

### Post by jussiam on 2007-04-17
I removed all the socket files and after 30 minutes I have over 2500 socket files in my /tmp. All I do is listen to mp3's with Amarok (version 1.4.3 using KDE 3.5.2).

---

