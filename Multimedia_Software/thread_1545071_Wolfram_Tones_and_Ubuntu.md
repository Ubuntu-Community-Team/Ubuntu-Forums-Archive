---
title: "Wolfram Tones and Ubuntu"
date: 2010-08-03
forum: Multimedia Software
---

### Post by Freiberg on 2010-08-03
For some reason, I can't get it to work in Ubuntu.  I started in Chrome, where it simply was silent.  Then I moved it to Firefox, where it said I needed a plugin to play the media, which I installed.  That didn't work.  I started following the instructions [here]("http://tones.wolfram.com/tsfaqs/linux/pluginsetup.html"), but was unable to install mozplugger.  Has anybody else gotten this to work, and, if so, how did you do it?

---

### Post by lovinglinux on 2010-08-03
[http://ubuntuforums.org/showpost.php?p=9646626&postcount=10](http://ubuntuforums.org/showpost.php?p=9646626&postcount=10)

---

### Post by Freiberg on 2010-08-03
I just tried that, but I can't find a mozplugger or plugger folder in /etc/.

---

### Post by lovinglinux on 2010-08-03
What is the output of:

```
file /etc/mozpluggerrc
```

---

### Post by Freiberg on 2010-08-03
```
/etc/mozpluggerrc: ERROR: cannot open `/etc/mozpluggerrc' (No such file or directory)

```

---

### Post by lovinglinux on 2010-08-03
> **Freiberg said:**
> ```
/etc/mozpluggerrc: ERROR: cannot open `/etc/mozpluggerrc' (No such file or directory)

```

```
sudo apt-get install mozplugger
```

---

### Post by Freiberg on 2010-08-04
Hmm.  It seemed to install correctly, and I followed the instructions from the website from there on, but it still doesn't work.  :confused:

---

