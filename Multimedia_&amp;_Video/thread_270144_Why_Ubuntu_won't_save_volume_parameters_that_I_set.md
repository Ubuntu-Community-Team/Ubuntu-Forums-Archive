---
title: "Why Ubuntu won't save volume parameters that I set?!"
date: 2006-10-02
forum: Multimedia &amp; Video
---

### Post by Turin Turambar on 2006-10-02
It's quite annoying actually. Everytime I restart the PC ubuntu changes the volume settings (e.g. master returns to 87%). Is this a bug or am I missing something here? Thanks.

---

### Post by henriquemaia on 2006-10-02
Try this command (on a terminal):

```
sudo alsactl store 0
```

Where 0 is the number of your soundcard. This should keep the volumes remembered.

---

### Post by Turin Turambar on 2006-10-03
Unfortunately, that didn't help. :(

---

