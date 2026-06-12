---
title: "MiniDLNA doesn't see anything on external USB HDD"
date: 2018-06-09
forum: Multimedia Software
---

### Post by demonikhan2 on 2018-06-09
Can someone here with some knowledge of Ubuntu and miniDLNA take a look at my Ask Ubuntu post? My post got buried :(
PS: I am a Linux/Ubuntu newbie. I installed less then a week ago, but I've been doing a LOT of reading :)

[https://askubuntu.com/questions/1044674/minidlna-doesnt-see-anything-on-external-usb-hdd](https://askubuntu.com/questions/1044674/minidlna-doesnt-see-anything-on-external-usb-hdd)

---

### Post by demonikhan2 on 2018-06-09
I found an error log in something called /var/log/syslog:

Jun  9 00:02:12 demonikhan minidlna[18008]: [2018/06/09 00:02:12] minidlna.c:631: error: Media directory "V,/media/demonikhan/usbdrive/Videos" not accessible [Permission denied]  
  
I know very little about chmod/chown as I have only been using Ubuntu for about 1 week. I've been reading and researching like crazy, but now I know this is the issue. Can you help?

---

### Post by demonikhan2 on 2018-06-09
[COLOR=#111111][FONT=Ubuntu]I figured it out. I had to sudo nano /etc/default/minidlna and add the USER="root" and the GROUP="root" to that file. I win the day :)[/FONT][/COLOR]

---

