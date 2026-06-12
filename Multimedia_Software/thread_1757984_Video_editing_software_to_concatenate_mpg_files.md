---
title: "Video editing software to concatenate mpg files"
date: 2011-05-14
forum: Multimedia Software
---

### Post by Macamba on 2011-05-14
Hi,

I searched a bit, but got overwhelmed by what I got.

I have a number of mpg files which I would like to concatenate to each other so I get one big file. I know how to do this with the cat commmand:
```

cat file_001.avi file_002.avi > file.avi
```

The problem with this approach is that each small file has a time (say 3 minutes), and the concatenated file still thinks it's 3 minutes, in stead of in my example 6.

So, anyone know what I can use?

TIA,
Macamba

---

### Post by mikewhatever on 2011-05-14
I had to do the same recently, and had also discovered that the command you tried didn't work. Not sure why it's all over the internet. In the end, I've ended up using mencoder:
```
mencoder -forceidx -ovc copy -oac copy -o file.avi p1.avi p2.avi p3.avi
```

I've renamed the parts to p1.avi, p2.avi, etc. Obviously, you can use more then two or three parts in one go. Mencoder is in the repositories, so just install it.

---

