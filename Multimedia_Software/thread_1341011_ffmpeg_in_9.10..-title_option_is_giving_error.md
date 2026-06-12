---
title: "ffmpeg in 9.10..-title option is giving error"
date: 2009-11-29
forum: Multimedia Software
---

### Post by abhigyan91 on 2009-11-29
```
ffmpeg: unrecognized option '-title'

```

this is wt aloways comes supposing i want to include the metadata.. this never happend in 8.10.. ihave installed the unstripped version of ffmpeg using the command:

```
sudo apt-get install ffmpeg libavcodec-extra-52

``` 

does ne1 else have this problem?

---

### Post by FakeOutdoorsman on 2009-11-30
You're using an outdated command.  Try:
```
-metadata title="Your Title"
```

---

