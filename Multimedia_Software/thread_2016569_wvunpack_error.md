---
title: "wvunpack error"
date: 2012-07-04
forum: Multimedia Software
---

### Post by yesongs on 2012-07-04
Hi there,
I 'm trying to unpack a rather big iso.wv file (about 2GB).
I'm recieving an error "can't write .WAV data, disk probably full!"
The disk is actually a 500GB ext4 disk with almost 120Gb free.
What could be wrong?

---

### Post by msammels on 2012-07-04
Perhaps it has something to do with tmp folder that your extracter is using. What software are you using?

---

### Post by yesongs on 2012-07-04
I'm on Ubuntu 12.04 and using "WVUNPACK  Hybrid Lossless Audio Decompressor  Linux Version 4.60.1" in terminal

---

### Post by shantiq on 2012-07-05
ok    a simple question


have you done this first?

rename your ```
file.iso.wv
```

to    ```
file.iso
```    then unpack the iso



AND THEN   decompress the wv contained therein to wav with wvunpack


if you go straight from the ```
file.iso.wv
```    it does not work as you are in effect trying to unpack an iso with wvunpack




PS   if you know all this ignore my interjection:KS

---

### Post by yesongs on 2012-07-05
YES!!
That's it!
Thank you very much!!

---

### Post by msammels on 2012-07-05
Glad you got it sorted, yesongs :)

---

### Post by yesongs on 2012-07-05
how do I tag the thread as SOLVED?

---

### Post by yesongs on 2012-07-05
OK..
Ifound it!
Thanks again!

---

