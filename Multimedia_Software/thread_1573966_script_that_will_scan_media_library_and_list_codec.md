---
title: "script that will scan media library and list codecs used"
date: 2010-09-13
forum: Multimedia Software
---

### Post by jimmah6786 on 2010-09-13
Hello all,

I am trying to find a script or command or program out there that would scan a directory for a/v files and display the codecs they use.

For example, let's say i have 3 avi files, 1.avi, 2.avi, 3.avi. I want to be able to figure out what each of them contains for video and audio tracks.

I know ffmpeg -i will show me what I want, but how do i incorporate it to do an entire directory.

Thanks,

Look forward to your ideas.

---

### Post by 0004tom on 2010-09-13
```
file *
```

or 

```
ffmpeg -i *
```

you could have it put all the outputs to a file also with

```
file * >> list.txt
```

---

