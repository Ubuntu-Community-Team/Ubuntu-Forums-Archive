---
title: "Can't get rid of low graphics mode, running gutsy"
date: 2008-06-30
forum: Multimedia Software
---

### Post by nemesis256 on 2008-06-30
I recently ran updates on my gutsy machine ( last Wednesday if I remember correctly) and since then Ubuntu has been booting into low graphics mode.  I tried re-configuring xserver (with dpkg-reconfigure xserver-xorg) but that didn't help.  When I select "normal" or "extra" from the visual effects prefs, it used to tell me that it found new drivers and to reboot, but that didn't work either.  Now for some reason when I select those two options I get the message saying effects could not be enabled.

Any ideas?

---

### Post by xc3RnbFO8P on 2008-06-30
Read this:
[http://ge.ubuntuforums.com/showthread.php?t=798881]("http://ge.ubuntuforums.com/showthread.php?t=798881")

---

### Post by wolfen69 on 2008-06-30
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by nemesis256 on 2008-07-03
> **wolfen69 said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
I ran that command and it worked as far as fixing the resolution problem. I'm back to 1280x1024. But now when I try to enable desktop effects and reboot, the problem is back.  Any ideas why enabling desktop effects would screw up the resolution and put Ubuntu into safe mode?

---

