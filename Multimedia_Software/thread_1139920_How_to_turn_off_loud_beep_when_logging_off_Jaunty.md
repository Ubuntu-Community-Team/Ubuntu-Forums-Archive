---
title: "How to turn off loud beep when logging off Jaunty"
date: 2009-04-27
forum: Multimedia Software
---

### Post by VinnyM69 on 2009-04-27
This is just a minor irritation that probably has an easy fix, but how do I disable the loud beep when logging off of Jaunty 9.04 (Ubuntu)?  I have the Ubuntu Gnome sound effects already turned off in the System > Preferences menu.  Thanks.

Vince

---

### Post by kpkeerthi on 2009-04-27
[http://ubuntuforums.org/showthread.php?t=1139490]("http://ubuntuforums.org/showthread.php?t=1139490")

---

### Post by VinnyM69 on 2009-04-28
I followed the tread above and made the suggested changes.  This did not fix the problem on my system.  Any other suggestions?

Vince

---

### Post by bonfire89 on 2009-08-03
I just did a reinstall of jaunty and only rembered vaugely how to do this, and I cam accorss this thread and found what it linked to really confusing.

But then I found this and it worked for me.


open /etc/modprobe.d/blacklist by typing 

```
sudo nano /etc/modprobe.d/blacklist
```


then add this text

```

# Mute CPU speaker
blacklist pcspkr

```





and then press 

Ctrl-x

then 

y

then 

enter

to save and exit

---

