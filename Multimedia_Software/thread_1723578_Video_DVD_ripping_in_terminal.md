---
title: "Video DVD ripping in terminal"
date: 2011-04-07
forum: Multimedia Software
---

### Post by Ghost_Mazal on 2011-04-07
Lo guys , I was wondering , is it possible to rip a Video DVD to hdd with a command line command ? Or with a bash script. What I want it to do is to rip the Video DVD as is in VIDEO_TS structure to the HDD. No encoding to other formats.

Can it be done ? And How ?

---

### Post by vanadium on 2011-04-07
```

vobcopy -m

```

---

### Post by Ghost_Mazal on 2011-04-07
> **vanadium said:**
> ```

vobcopy -m

```

As simple as that ? I am amazed. But obviously one will have to give input and output paths ?

---

### Post by Fire_Chief on 2011-04-07
Here's the man page for the vobcopy command so you can review the syntax and options.

[http://manpages.ubuntu.com/manpages/maverick/man1/vobcopy.1.html]("http://manpages.ubuntu.com/manpages/maverick/man1/vobcopy.1.html")

Cheers!

---

### Post by Ghost_Mazal on 2011-04-07
Thanx guys

---

### Post by vanadium on 2011-04-07
> **Ghost_Mazal said:**
> As simple as that ? I am amazed. But obviously one will have to give input and output paths ?

Yes, as simple as that. I would not even know how to specify another DVD reader than the default if you have any.

---

