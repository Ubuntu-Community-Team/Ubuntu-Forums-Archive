---
title: "dist-upgrade broke lirc"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by lingenfr on 2007-09-17
I ran:

sudo apt-get update
sudo apt-get upgrade

on my mythbox. That broke it so that myth would not start. I did some googling and found to do a:

sudo apt-get dist-upgrade

now myth starts, but no lirc. I have done some googling and tried a few solutions, but no joy. Help.

---

### Post by tagra123 on 2007-09-19
If you are using a serial irblaster you can try this:

[http://ubuntuforums.org/showthread.php?p=3359017](http://ubuntuforums.org/showthread.php?p=3359017)

---

### Post by lingenfr on 2007-09-19
Thank for the reply. I don't use the irblaster, I just need the receiver to work. Still hoping for some help.

---

### Post by 86and96 on 2007-09-21
Did you download a new kernel with your updates?
I followed this guide to get lirc working the first time, and had to do the part where you build the modules again when I updated a couple of weeks ago and downloaded a new kernel. Scroll down about a quarter of the page to "Build lirc modules"

[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

---

### Post by lingenfr on 2007-09-21
Thanks. That is what I did as well.

---

