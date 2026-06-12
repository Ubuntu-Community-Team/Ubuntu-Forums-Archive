---
title: "Touchpad crash"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by up2early on 2011-04-01
Updated from 10.10 to the 11.04 beta overnight on Dell Latitude D810. Was running fine this morning, then ran update manager, rebooted and now everytime I touch either the touchpad or touchpad buttons it reboots. An attached USB mouse works fine, any ideas?

---

### Post by drbcladd on 2011-04-01
No answers, same question.

Update manager from alpha 3 to beta 1 this morning and the same behavior.
Running the failsafe vesa X drivers. I haven't taken a look at the xorg.conf file yet; all of the xorg stuff was upgraded, though.

---

### Post by jsevi83 on 2011-04-01
It's a known bug, as you can see here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/747126](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/747126)

There will be an update soon to fix it, but if you cannot wait, you can manually install one of these files (the first is for i386, and the second for amd64)

[https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.3.99+git20110116.0e27ce3a-0ubuntu10/+buildjob/2421132/+files/xserver-xorg-input-synaptics_1.3.99%2Bgit20110116.0e27ce3a-0ubuntu10_i386.deb](https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.3.99+git20110116.0e27ce3a-0ubuntu10/+buildjob/2421132/+files/xserver-xorg-input-synaptics_1.3.99%2Bgit20110116.0e27ce3a-0ubuntu10_i386.deb)


[https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.3.99+git20110116.0e27ce3a-0ubuntu10/+buildjob/2421130/+files/xserver-xorg-input-synaptics_1.3.99%2Bgit20110116.0e27ce3a-0ubuntu10_amd64.deb](https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.3.99+git20110116.0e27ce3a-0ubuntu10/+buildjob/2421130/+files/xserver-xorg-input-synaptics_1.3.99%2Bgit20110116.0e27ce3a-0ubuntu10_amd64.deb)

---

### Post by gunashekar on 2011-04-01
thsnk you. it worked

---

### Post by up2early on 2011-04-01
Worked for me also.

Thanks!

---

### Post by jsevi83 on 2011-04-01
up2early, you could mark it as solved to help other people find a solution.

---

### Post by giant420 on 2011-04-01
Awesome, works for me as well! Gotta love these fast fixes from the devs.. :guitar:

---

### Post by jsartti on 2011-04-01
Thanks for the quick response.

---

### Post by ReyPorUnDia on 2011-04-01
Thanks, it worked on Dell Inspiron 1318!

---

### Post by Quackers on 2011-04-01
Same problem, but I only just found it :-)
The .deb file linked to is now an update. 
Thanks anyway!

---

