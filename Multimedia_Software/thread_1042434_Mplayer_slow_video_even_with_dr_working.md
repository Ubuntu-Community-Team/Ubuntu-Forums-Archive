---
title: "Mplayer slow video even with dr working"
date: 2009-01-17
forum: Multimedia Software
---

### Post by astbis on 2009-01-17
Hi.

I have switched my laptop from gentoo to kubuntu hardy and since i have trouble playing back movies with mplayer (mplayer-nogui).

If i play i.e. xvid movies i notice a video delay and get an "Your system is too SLOW to play this" in the terminal.

So far i checked:
Direct rendering=Yes and working with glxgears
Audio is working fine everywhere
Harddisk dma is on
Testet different -vo options
Xine works fine

Now after checking and research on Google for 1,5 hours i need help.

What is causing it and how can i solve it?

Thanks in advance for any help.

---

### Post by andrew.46 on 2009-01-17
Hi,

Can I ask what version of MPlayer you are using? The result of:

```
andrew@skamandros:~$ **[COLOR="Red"]mplayer | head -n 1[/COLOR]**
MPlayer dev-SVN-r28337-4.3.2 (C) 2000-2009 MPlayer Team

```

might be the easiest way.

Andrew

---

### Post by astbis on 2009-01-18
I get:
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team

---

### Post by andrew.46 on 2009-01-18
Hi astbis,

> **astbis said:**
> I get:
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team

In that case one possible solution would be to try the current MPlayer which operates from an svn repository.

Andrew

---

### Post by astbis on 2009-01-19
Thanks for the reply.

Do you know any howto? What is the best way to do it in ubuntu, so my system doesn't break at system updates?

---

### Post by andrew.46 on 2009-01-19
Hi astbis,

> **astbis said:**
> Do you know any howto? What is the best way to do it in ubuntu, so my system doesn't break at system updates?

I was hoping that you would ask :-). The guide is here:

[http://ubuntuforums.org/showthread.php?t=1024592](http://ubuntuforums.org/showthread.php?t=1024592)

Andrew

---

### Post by astbis on 2009-01-19
Thanks! I will try that in the evening. It seems like going back to gentoo ... do everything by hand. :-)

---

### Post by andrew.46 on 2009-01-19
Hi astbis,

> **astbis said:**
> Thanks! I will try that in the evening. It seems like going back to gentoo ... do everything by hand. :-)

True but I have made substantial efforts with this iteration of the guide to make the installation fit fairly securely into the Ubuntu package management system. The Jaunty Jackalope version should fit even closer.

Andrew

---

### Post by astbis on 2009-02-03
Now i had enough time trying to solve the issue. But without luck. Mplayer still can't play movies synchronized.

Ubuntu is a nice system but this annoys me totally. Could it be a graphic driver issue even if direct rendering is working?

---

### Post by lzap on 2009-05-18
Direct rendering is not enought to play smooth videos. Check google for XV video output.

The truth is mplayer in the jaunty is a little bad one.

---

