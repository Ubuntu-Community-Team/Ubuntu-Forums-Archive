---
title: "Can't login! Graphics problem"
date: 2009-06-01
forum: Multimedia Software
---

### Post by flatcoke on 2009-06-01
When I was updating from 8.10 to 9.04, it asked me what should it do with GRUB's boot menu. I selected "open up a new terminal to further investigate the problem" then my computer stopped responding. After rebooting, I can't login! The Gnome login screen came up fine, but after I typed in my username and password and hit enter, the screen would look really messed up with several vertical lines, then after a few seconds I'm kicked back to the login screen again!
So I manually reinstalled the kernel with 
```
 apt-get --reinstall install linux-headers-2.6.28-11-generic
apt-get --reinstall install linux-image-2.6.28-11-generic
```
and then updated the whole system again. Nothing changed.

---

