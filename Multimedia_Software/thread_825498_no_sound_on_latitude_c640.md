---
title: "no sound on latitude c640"
date: 2008-06-11
forum: Multimedia Software
---

### Post by shaharudin on 2008-06-11
hello all.. newbies here...

i'm intalling hardy server on my latitude c640...
after that i'm installing gnome-core. 
how to enabled my sound ?

```

shaharudin@ubuntuserver:~$ lspci | grep Audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
shaharudin@ubuntuserver:~$ uname -r
2.6.24-16-server

```

pls help my dear friends

---

### Post by shaharudin on 2008-06-18
ok... it works fine after installing gnome-alsamixer...

thanks all

```

$ sudo apt-get install gnome-alsamixer

```

---

