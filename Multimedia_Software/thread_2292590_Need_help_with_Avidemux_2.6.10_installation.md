---
title: "Need help with Avidemux 2.6.10 installation"
date: 2015-08-29
forum: Multimedia Software
---

### Post by djdg on 2015-08-29
Hello!

I downloaded the tar,gz file 'avidemux_2.6.10.tar.gz' and extracted it. But there seems to be no executable file with which to start the program. How do I run Avidemux (specifically the 2.6.10 version) on my pc?

Edit: Ubuntu Software Centre installs an older version.

Thanks from the Netherlands!

---

### Post by Vladlenin5000 on 2015-08-30
[http://linuxg.net/how-to-install-avidemux-2-6-8-on-ubuntu-linux-mint-and-elementary-os/](http://linuxg.net/how-to-install-avidemux-2-6-8-on-ubuntu-linux-mint-and-elementary-os/)

---

### Post by djdg on 2015-09-01
Thanks Vladlenin5000. I tried the 2.6.8 version, but the Subtitle ripper is really buggy. When I completed the process I had a .srt file that was full of spelling mistakes. So I really need the latest version (2.6.10) of Avidemux where hopefully these bugs are fixed.

---

### Post by Portaro on 2015-09-01
Do you try to run avidemux on terminal

$ avidemux2_gtk*************************
  Avidemux v2.5.6
*************************

or 

$ avidemux


Im on Lubuntu 14.04 and I have this installed.

And you have a Getdeb repos that have the last version -> [http://www.getdeb.net/updates/Ubuntu/14.04/?q=avidemux](http://www.getdeb.net/updates/Ubuntu/14.04/?q=avidemux)

---

### Post by Yellow Pasque on 2015-09-01
> **djdg said:**
> Thanks Vladlenin5000. I tried the 2.6.8 version,

He gave you the correct link, but you didn't follow the instructions/commands to download 2.6.10

```
sudo apt-get remove avidemux2.6
sudo add-apt-repository ppa:rebuntu16/avidemux+unofficial
sudo apt-get update
sudo apt-get install avidemux2.6
```

---

