---
title: "Imagination 3.0 app problem"
date: 2016-11-11
forum: Multimedia Software
---

### Post by aa4bb on 2016-11-11
In 16.04, I made a small test video with one slide and music. I tried to export it as VOB, then OGV and finally FLV. In each case, the error message "Failed to execute child process "avconv" (No such file or directory)" appeared.

How do I add the necessary libraries, or whatever it needs?

---

### Post by &amp;KyT$0P# on 2016-11-12
The problem is that it needs [avconv]("http://packages.ubuntu.com/xenial/libav-tools").  It should be using [FONT=Courier New]ffmpeg[/FONT] on 16.04.

Try this as a workaround -
```
sudo apt-get install libav-tools
```

---

### Post by aa4bb on 2016-11-12
Thank you so much, halogen2! Perfect!

---

### Post by &amp;KyT$0P# on 2016-11-12
You're welcome!  :KS

The real fix is needs to be done in the program.  You might report this to them as a bug.

---

