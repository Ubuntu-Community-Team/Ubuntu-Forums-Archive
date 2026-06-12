---
title: "X-Fi Card not detected"
date: 2010-05-16
forum: Multimedia Software
---

### Post by Jademalo on 2010-05-16
Ive just installed a fresh 10.04, and my Xfi- Xtreme Music card isnt showing up ion the sound options.

Ive tried installing the latest alsa using the script thing, and its still not showing up.

Is there anything I can do?

(64 bit)

---

### Post by Jademalo on 2010-05-16
There is definatley nothing wrong with my card, I have successfully got it working on windows 7.. Ive tried pretty much everything, but the system is just not recognising the card. It used to work on 9.04.

---

### Post by lidex on 2010-05-16
Like to read?
**X-FI**
[http://ubuntuforums.org/showthread.php?t=870001]("http://ubuntuforums.org/showthread.php?t=870001")
[http://ubuntuforums.org/showthread.php?t=690490]("http://ubuntuforums.org/showthread.php?t=690490")
[http://ubuntuforums.org/showthread.php?t=1254492]("http://ubuntuforums.org/showthread.php?t=1254492")

You may need this also.
**OSS**
[http://ubuntuforums.org/showthread.php?t=1420745]("http://ubuntuforums.org/showthread.php?t=1420745")
[http://ubuntuforums.org/showthread.php?t=1355676]("http://ubuntuforums.org/showthread.php?t=1355676")
[http://ubuntuforums.org/showthread.php?t=1217259]("http://ubuntuforums.org/showthread.php?t=1217259")
[http://ubuntuforums.org/showthread.php?t=866106]("http://ubuntuforums.org/showthread.php?t=866106")

Sorry no easy answers. :(

---

### Post by Jademalo on 2010-05-18
Nothing worked. The card still does not show up anywhere.

=[

---

### Post by lidex on 2010-05-20
Using a Terminal="Applications->Accessories->Terminal"
```
sudo pulseaudio --kill
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

