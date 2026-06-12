---
title: "resolution assistance"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by fbs2007 on 2007-06-24
im new to ubuntu, and im having a problem getting my monitor to display 1600x1200....any ideas?

athlon x2 4400+
dfi lanparty nforce4
nvidia 7800gt

im thinking theres just some configuration file i have to locate and edit...but whenever i start thinking things dont end well

---

### Post by logos34 on 2007-06-24
did you install the nvidia driver (binary or proprietary)?

---

### Post by Gremlinzzz on 2007-06-24
I got ths from the guide and it works for my computer
sudo apt-get install xserver-xorg-video-intel
then rebooted and it cofig its self. my resolutions are 1440 x 900 wide screen
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by logos34 on 2007-06-24
you don't necessarily need the nvidia driver, you might be able to just edit xorg.conf file.  You might want to just copy and post it,  Open a terminal and type:
gedit /etc/X11/xorg.conf

You can also run the interactive configuration:

**sudo dpkg-reconfigure xserver-xorg**

---

### Post by fbs2007 on 2007-06-24
alright thanks a lot for your help

had to change the administrator password

---

