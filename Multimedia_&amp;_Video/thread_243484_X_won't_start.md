---
title: "X won't start"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by ickopicko on 2006-08-25
My X won't start. It just says:
> (EE) No devices detected.

Fatal server error:
no screens found

XIO: fatal IO error 104...

I think it happened when something was upgraded automatically. I had earlier changed /etc/X11/Xorg.conf, so i copied back the original config file and tried to restart, but nothing happened. If also tried running "sudo dpkg-reconfigure xserver-xorg", but that didn't help.

What do I need to do?

---

### Post by tseliot on 2006-08-25
Read this:
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)


OR:
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```

and reboot:
```
sudo reboot
```

---

### Post by ickopicko on 2006-08-25
Thank you tseliot!

---

