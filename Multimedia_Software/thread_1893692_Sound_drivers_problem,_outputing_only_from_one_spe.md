---
title: "Sound drivers problem, outputing only from one speaker"
date: 2011-12-10
forum: Multimedia Software
---

### Post by lautarox on 2011-12-10
I have an Encore ENM232-6VIA sound card, after each kernel update, I had to reinstall the Alsa debs to make my card work, last time it started working only with one speaker, I think it has changed to mono, I have searched a lot but I couldn't find the way to change it.
Also, is there a way to not reinstall Alsa each time I update the kernel?
Thanks in advance

---

### Post by editheraven on 2011-12-11
Try going to alsamixer (from bash) and select the number of channels at the end of the list.

Also try

```

mv /etc/asound.conf /etc/asoundbak.bak && mv ~/.asoundrc ~/.asoundrcbak
sudo alsa force-reload

```

---

### Post by lautarox on 2011-12-11
[FONT=monospace]The line:
mv /etc/asound.conf /etc/asoundbak.bak && mv ~/.asoundrc ~/.asoundrcbak
Says that the file /etc/asound.conf doesn't exist
Also, where's the alsamixer's channels selector?
Here is my alsamixer's config:
[IMG]http://img705.imageshack.us/img705/5100/alsa1.png[/IMG]

[IMG]http://img14.imageshack.us/img14/755/alsa2.png[/IMG]
[/FONT]

---

