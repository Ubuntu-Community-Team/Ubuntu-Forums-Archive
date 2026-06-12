---
title: "Amarok trouble"
date: 2009-08-27
forum: Multimedia Software
---

### Post by Vik Vasilev on 2009-08-27
Maybe its a missing codec or something but my mp3`s play in other programs. My girlfriend has the same problem with Amarok -> When i start the app, it works well makes the list of songs, etc but when I click play nothing happens.  :confused: No error messages, nothing. How do I fix this?

---

### Post by Elfy on 2009-08-27
I've needed to install the libxine1 ffmpeg package to get it to work.

```
sudo apt-get install libxine1-ffmpeg
```

---

