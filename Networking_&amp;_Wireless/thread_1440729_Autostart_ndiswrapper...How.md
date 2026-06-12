---
title: "Autostart ndiswrapper...How?"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by sdpimpy on 2010-03-27
Can some kind soul tell me how to autostart ndiswrapper in Xubuntu 9.10?

I've got my wireless working but I have to run modprobe ndiswrapper in terminal after each reboot.

---

### Post by chili555 on 2010-03-27
There is a file that loads modules automagically on boot called */etc/modules*. Let's add ndiswrapper. Open a terminal and do:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```That's it!

---

### Post by sdpimpy on 2010-03-28
Thank you very much Chili, that did the trick. \\:D/

---

