---
title: "Locked wav files"
date: 2015-04-21
forum: Multimedia Software
---

### Post by ray9 on 2015-04-21
I extracted some audio files to convert to mp3 and they are are locked.  I added them to soundconverter but nothing happens.  How do I unlock them?

---

### Post by Yellow Pasque on 2015-04-21
Locked? Like you need to change permissions on them? Assuming you extracted the files as sudo/root,
```
sudo chown <username>:<username> <file(s)>
```

---

