---
title: "oops."
date: 2006-10-02
forum: Multimedia &amp; Video
---

### Post by pentium on 2006-10-02
I was updating my nvidia driver and when I restarted I was given the error that there was a problem and GDM was disabled until the problem is cleared. How Can i undo the driver update soI can continue on with the origional?

---

### Post by thingy on 2006-10-02
To enable the use of the nvidia driver can you try to run the

> sudo /usr/sbin/nvidia-glx-config enablecommand.


And if you want to switch back to the xorg nv driver (which is prob. what you were using before), enter the following command:


> sudo /usr/sbin/nvidia-glx-config disable

---

### Post by pentium on 2006-10-02
that worked.
thanks man.

---

