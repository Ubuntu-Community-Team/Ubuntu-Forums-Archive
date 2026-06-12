---
title: "Ubuntu 11.04 beta 1 question"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Christopher on 2011-04-03
How do i go about telling what version of 11.04 I'm running 32bit or 64bit? I did the Alt-f2 then upgraded. Thanks.

---

### Post by davidmohammed on 2011-04-03
type

uname -r

if it ends "amd64" then you are running 64 bit - otherwise you are running a 32bit kernel

---

### Post by howefield on 2011-04-03
Thread moved to "*Natty Narwhal Testing and Discussion*"

You should still be running whatever you had before in respect of 32 or 64 bit.

Try using the following command to find out, if you find x86_64 in the output, you have 64 bit, otherwise it is 32 bit ;-)

```
uname -a
```

---

### Post by Christopher on 2011-04-03
Ok thanks, this is what i got. :)

2.6.38-7-generic #39-Ubuntu SMP Fri Mar 25 21:24:57 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Dutch70 on 2011-04-03
You are running 64-bit.

---

### Post by Christopher on 2011-04-03
> **Dutch70 said:**
> You are running 64-bit.

Thats what i thought, just wanted to make sure, so far its running really good. :D

---

### Post by Dutch70 on 2011-04-03
> **Christopher said:**
> Thats what i thought, just wanted to make sure, so far its running really good. :D

Yeah, I had Ubuntu for over 2 years before I realized I could use the 64-bit version. They say it's not really any faster. I don't know about that, but it sure has a better feel to it.

---

