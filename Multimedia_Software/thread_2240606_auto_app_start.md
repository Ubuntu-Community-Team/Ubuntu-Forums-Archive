---
title: "auto app start"
date: 2014-08-21
forum: Multimedia Software
---

### Post by imoody on 2014-08-21
Hi I am running Ubuntu 14.04 64 bit and if a music player eg VLC, Rythym box  or Audacious is installed it opens autumatically after a short time . If it is closed by clicking the X button or quit on the menu it will open again.
I can only stop this by uninstalling the software. The software opneing screen also blinks rapidily.
Any suggestions on stopping this problem welcolm
Ian

---

### Post by bizhat on 2014-08-21
I don't see a reason for an application to start by itself. Anyone else using your computer ? 

Any cronjob set ? try running

```

crontab -l

```

In terminal, see any program is set to start.

---

### Post by ajgreeny on 2014-08-21
Have you checked in the list of autostart applications in **Preferences ->Default applications for LXSession** ?

Have you set the system to save and use previous sessions?

---

### Post by vasa1 on 2014-08-21
OP has tagged the thread Lubuntu, but in the post itself Ubuntu is mentioned.

---

### Post by ajgreeny on 2014-08-21
> **vasa1 said:**
> OP has tagged the thread Lubuntu, but in the post itself Ubuntu is mentioned.
So it is; I didn't notice that!

OK forget the details of my comment, but consider the ideas about saved sessions being restarted.  I do not like, nor use, unity so can't help with the details of how to deal with that possibility, but it does seem a possible cause.

---

### Post by vasa1 on 2014-08-21
> **ajgreeny said:**
> So it is; I didn't notice that!
...
I think there's a persistent forum bug causing some threads to be tagged **Lubuntu**. Here's another: [http://ubuntuforums.org/showthread.php?t=2240655](http://ubuntuforums.org/showthread.php?t=2240655)

---

### Post by imoody on 2014-08-21
> **bizhat said:**
> I don't see a reason for an application to start by itself. Anyone else using your computer ? No one else is using the PC

Any cronjob set ? try running   No no jobs running

```

crontab -l

```

In terminal, see any program is set to start.

Have also narrowed it down somewhat. 
 I reinstalled VLC and with no other programs running it does not open.
It does not open with Thunderbird running.
If I open Firefox VLC starts up and I cannot shut it down.  Each time i close it VLC reopens again.
Hope this is the way to reply as I am brand new to this forum

---

### Post by bizhat on 2014-08-22
In firefox, try disable VLC plugin. I have VLC plugin enabled in firefox (i have a software that use vlc plugin), never had such problem.

---

