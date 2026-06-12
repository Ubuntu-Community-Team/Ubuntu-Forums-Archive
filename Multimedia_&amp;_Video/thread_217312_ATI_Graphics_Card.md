---
title: "ATI Graphics Card"
date: 2006-07-16
forum: Multimedia &amp; Video
---

### Post by darkzar99 on 2006-07-16
Is the ATI Radeon X700 Pro PCI-Express graphics card currently supported in Ubuntu AMD64?  I am having difficulties with it, i keep getting different errors about displays not being found and i find myself stuck at a command prompt, one of the errors was "RuntimeError: could not open display"

---

### Post by Dubbayoo on 2006-07-17
I think what matters is that its supported by the version of Xorg you're using and/or the version of the binary ATI driver you're using if so.

---

### Post by sangaya on 2006-07-17
I don't have 64bit dapper installed but the following got me up and running with my ATI x1800xt.  Note that I have dual monitors, if you don't, I think you can just run aticonfig once without any parameters.
```

sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-`uname -r`
sudo reboot now
sudo aticonfig –initial=dual-head –screen-layout=right
sudo aticonfig –dtop=horizontal –overlay-on=1
sudo reboot now

```

The linux-restricted-modules and using the repository binary driver versus downloading it from ATI were the two big helpers I found. Since you'll be getting the packages through apt-get 64bit shouldn't make a difference because you'll be using the 64bit repositiory.

-sangaya

---

### Post by darkzar99 on 2006-07-17
thanks sangaya, it worked

heres what i had to run:
```
sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-`uname -r`
sudo reboot now
sudo aticonfig --initial --input=/etc/X11/xorg.conf
sudo reboot now
```

---

### Post by sangaya on 2006-07-17
glad it worked for ya! :)

---

