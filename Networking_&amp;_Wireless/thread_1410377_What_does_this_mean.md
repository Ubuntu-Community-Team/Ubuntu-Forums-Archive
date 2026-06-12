---
title: "What does this mean?"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by duncanmaybury on 2010-02-18
Hello 
I just bought a Edimax EW-7711UTn usb wireless stick. I was going to put it on a machine in a friends cafe for the public where we want to run Karmic instead of windows.
Just checked on the hardware support(abit late) It says it doesnt work!! Anyone know if it works on older distributions?

---

### Post by wojox on 2010-02-18
Open your terminal:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Put it at the bottom.

---

### Post by Enigmapond on 2010-02-18
Pull up the terminal and type in

```
gksudo gedit etc/modprobe.d/blacklist.conf
```add blacklist rt2800usb to the file and save it and then reboot.

---

### Post by duncanmaybury on 2010-02-18
Sorry folks, I changed the message, just looked closer and it says the exact one i have bought doesnt work.
Sorry for being inaccurate with my first post.

---

### Post by duncanmaybury on 2010-02-18
Thanks for the replys though.

---

### Post by duncanmaybury on 2010-02-18
Sorry for wasting your time. I just found [this thread]("http://ubuntuforums.org/showthread.php?t=1326232&highlight=Edimax+EW-7711UTn+usb") will try it out.

Regards
Duncan

---

