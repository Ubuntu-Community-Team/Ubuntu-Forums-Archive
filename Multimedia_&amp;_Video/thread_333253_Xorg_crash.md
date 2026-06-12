---
title: "Xorg crash"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by addisor on 2007-01-07
Just installed 6.10 on a new build using Abit mobo with onboard graphics GeForce 6150/430 and my screen refresh rate was terrible, jerky mouse scrolling/dragging etc. Had a look through forum and tried following a Xorg monitor manual install except i made a complete mess of it and now no booting at all, just get the Xorg failure screen saying my graphics is incorrect. How do i roll back to old xorg? How do I check my Geforce driver and upgrade if poss to improve refresh rate? Gold star if you answer all that. thanks.

---

### Post by tseliot on 2007-01-07
> **addisor said:**
> Just installed 6.10 on a new build using Abit mobo with onboard graphics GeForce 6150/430 and my screen refresh rate was terrible, jerky mouse scrolling/dragging etc. Had a look through forum and tried following a Xorg monitor manual install except i made a complete mess of it and now no booting at all, just get the Xorg failure screen saying my graphics is incorrect. How do i roll back to old xorg? How do I check my Geforce driver and upgrade if poss to improve refresh rate? Gold star if you answer all that. thanks.

Try this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

then type:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

If all went well then you can install the latest Nvidia driver. You can do it by following this guide:
[http://www.ubuntuforums.org/showthread.php?t=301499](http://www.ubuntuforums.org/showthread.php?t=301499)
OR by using Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by addisor on 2007-01-07
Thanks for help. Really struggling today, the first bit worked, now back to generic driver. thought I'd try the envy route, except can't get ctrl/alt/F1 to access command line:-k 

Any idea's?

---

### Post by tseliot on 2007-01-07
> **addisor said:**
> Thanks for help. Really struggling today, the first bit worked, now back to generic driver. thought I'd try the envy route, except can't get ctrl/alt/F1 to access command line:-k 

Any idea's?

Try point 13 of the Problems Section of my guide:
[http://albertomilone.com/latest_nvidia_udsf_edgy.html#PROBLEMS_SECTION](http://albertomilone.com/latest_nvidia_udsf_edgy.html#PROBLEMS_SECTION)

---

### Post by addisor on 2007-01-08
Still no console access!! tried your splash removal bug fix.

---

### Post by addisor on 2007-01-08
All done, thanks. works a treat using nvidia drivers.

---

### Post by addisor on 2007-02-15
Still cant get console ctrl alt f1-6 working , any ideas

---

