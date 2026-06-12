---
title: "Audio recorder error - shared libraries"
date: 2019-12-19
forum: Multimedia Software
---

### Post by oygle on 2019-12-19
I was able to use audio-recorder on 16.04.6, however after it was installed on 18.03.3 LTS, got this error

> audio-recorder: error while loading shared libraries: libappindicator3.so.1: cannot open shared object file: No such file or directory

The install was done with the PPA mentioned in [https://itsfoss.com/record-streaming-audio/](https://itsfoss.com/record-streaming-audio/)

---

### Post by oygle on 2019-12-19
This fixed it ..

```
sudo apt install libappindicator3-1
```

---

