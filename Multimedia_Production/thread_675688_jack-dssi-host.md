---
title: "jack-dssi-host?"
date: 2008-01-22
forum: Multimedia Production
---

### Post by money2themax on 2008-01-22
```

Failed to execute child process "jack-dssi-host" (No such file or directory)

```
I tried starting the "Oscilloscope" i i keep getting the above in a Error box

---

### Post by money2themax on 2008-01-23
bump

---

### Post by vemon on 2008-02-19
You're probably missing jack-dssi-host binary. It can be found from the dssi-host-jack package.

Just do this and try to start the oscillator again:
sudo apt-get install dssi-host-jack

---

