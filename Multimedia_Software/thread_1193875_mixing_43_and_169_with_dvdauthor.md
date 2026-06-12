---
title: "mixing 4:3 and 16:9 with dvdauthor"
date: 2009-06-22
forum: Multimedia Software
---

### Post by hurtstotalktoyou on 2009-06-22
**The background:**

Usually when I author DVDs, I start off with DVD-ready mpeg files:

file1.mpg
file2.mpg
file3.mpg
(etc.)

To create the DVD image, I run the following simple terminal commands:

```
dvdauthor -o outputdirectory -t file1.mpg file2.mpg file3.mpg
```

```
dvdauthor -o outputdirectory -T
```

```
mkisofs -dvd-video -o outputfile.iso outputdirectory/
```

These three commands get me a simple DVD with a single title, and with each file making up a chapter on that title.  And this is great for DVDs with a single continuous aspect ratio.

**The question:**

But I have now run into a situation where file1.mpg and file2.mpg are 16:9, but file3.mpg is 4:3.  To put these on a DVD, I need to make them into different titles, and not just different chapters.  How can I do that with dvdauthor in terminal?

PLEASE NOTE:  I have never used scripts or xml, and it's probably best if I don't start now.

Thanks!

---

