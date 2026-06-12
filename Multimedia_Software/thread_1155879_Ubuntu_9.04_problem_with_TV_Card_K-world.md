---
title: "Ubuntu 9.04 problem with TV Card K-world"
date: 2009-05-11
forum: Multimedia Software
---

### Post by DachaArh on 2009-05-11
I have ubuntu 9.04 and K-World Multimedia PVR-TV 7131 TV Card I have tried to enable it like in ubuntu 8.10 with this :

```
sudo gedit /etc/modules

and add in new line :
saa7134

then 
sudo gedit /etc/modprobe.d/saa7134

options saa7134 card=65

and the same with bttv 
```

and then installing TV Time, when I restarted in 8.10 everything worked fine, but here in 9.04 When I turn on TV Time 

I have in up-right corner "No video source"

and down-left " Frames too short from pac207"
"Cannot open capture device /dev/video0"

can someone help please ?

---

### Post by DachaArh on 2009-05-11
any help ?

---

### Post by DachaArh on 2009-05-14
and no one can help ? :(

---

