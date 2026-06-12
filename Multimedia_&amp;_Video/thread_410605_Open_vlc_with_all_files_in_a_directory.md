---
title: "Open vlc with all files in a directory"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by idynkydnk on 2007-04-15
When I use Totem, I do totem ~/downloads/videos and it starts playing all the files in that directory.  How can I do that with vlc?

---

### Post by dfm21 on 2007-04-15
In your case:
```
vlc ~/downloads/videos/*
```
A simple bash command that expands to e.g.:
```
vlc ~/downloads/videos/file1.aiv ~/downloads/videos/file2.mpg ~/downloads/videos/file3.avi
```

---

