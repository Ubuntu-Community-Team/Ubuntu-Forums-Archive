---
title: "Video problems when starting from hibernate"
date: 2011-05-01
forum: Multimedia Software
---

### Post by banjo.mole on 2011-05-01
Hello! I recently upgraded to Ubuntu 11.04. I didn't really find the Unity interface useable (I didn't like Ubuntu Netbook Edition for this exact reason) and am running it in Classic mode.

I have a Acer Aspire One D255, Intel Atom processor, etc.

When I start the computer up from a hibernate, the screen goes black with a set of random colored pixels at the top corner. I have a mouse but nothing else.

Can anyone help me find a fix to this problem? I can provide more information if needed, but I don't know what. Thanks!

-Nick

---

### Post by banjo.mole on 2011-05-01
Bump

---

### Post by banjo.mole on 2011-05-02
Nothing? Ugh, I might switch to mint. Power consumption on 11.04 is a real bitch anyway.

---

### Post by trehanabhinav on 2011-05-02
hey Nick
same problem was also reported by some users of maverick
till now no support has been provided on the topic as far as i know
best option is to never start the hibernate mode if u could avoid it
will post as soon as I find out something new buddy.

---

### Post by sami_hentunen on 2011-05-24
Exactly the same problem with Aspire one AOA-150 (ZG5) installed with 11.04.

"Convenient" workaround after resuming from hibernate is to Ctrl-Alt-F1, and to blindly logon, and then again to blindly issue request to suspend:

```
sudo pm-suspend
```

followed by your password. After suspend-resume cycle your display will behave itself until next hibernate-resume cycle.

---

