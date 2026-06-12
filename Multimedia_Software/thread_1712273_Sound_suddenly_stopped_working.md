---
title: "Sound suddenly stopped working"
date: 2011-03-22
forum: Multimedia Software
---

### Post by adieyal on 2011-03-22
All of a sudden my sound stopped working. I've checked the obvious mixer settings etc. As a test - I've tried aplay, skype, vlc etc. Nothing works.

I ran the alsa-info.sh script - results are posted here:
[http://www.alsa-project.org/db/?f=187ae4bd1a6dffb2a54005bf59c6047c52efe461](http://www.alsa-project.org/db/?f=187ae4bd1a6dffb2a54005bf59c6047c52efe461)

Anyone have any ideas?

---

### Post by lidex on 2011-03-22
Was this after a suspend/resume? A recent update? Try booting into an older kernel and see if it works.

---

### Post by adieyal on 2011-03-23
> **lidex said:**
> Was this after a suspend/resume? A recent update? Try booting into an older kernel and see if it works.
No - I didn't change anything. One minute sound was working. The next it stopped.

---

### Post by lidex on 2011-03-23
What is the make/model of your computer?

---

### Post by adieyal on 2011-03-25
It doesn't have a make/model - it's a no-name branded desktop computer.

---

### Post by lidex on 2011-03-31
Post this info please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

