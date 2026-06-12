---
title: "problems with ATI driver 8.33.6"
date: 2007-01-31
forum: Multimedia &amp; Video
---

### Post by blunile on 2007-01-31
Hello everyone ,

I'm using Ubuntu for few months now, and i have a little strange problem.

I recently installed kubuntu 6.10, and I managed to install latest ATI driver 8.33.6 and it worked fine.I adjusted it to 1024x768 and life couldn't be happier !!!!

The very next day the screen resolution dropped to 600x480 with huge icons and big menus !!!!
I can't adjust it - through system settings - because there are no resolutions above 600x480 !!!

when I type fglrxinfo in command line, it shows me that everything is fine , fglrx driver is installed and working !!!!
my graphic card is radeon x1600 pro .

Can somebody help me fix this ???!!!!!

---

### Post by pay on 2007-01-31
Can you run these few commands and post the results ```
glxinfo
cat /etc/X11/xorg.conf
fglrxinfo
```

---

### Post by blunile on 2007-02-01
well, I reinstalled my kubuntu and everything is going well so far . Thank you anyway

---

