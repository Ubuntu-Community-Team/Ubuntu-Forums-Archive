---
title: "Changing default Apache2 port"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by kprice789 on 2011-10-12
So I have to change the default Apache2 port to something other than 80 because of my ISP blocking that port. So I change the listening port to 8000. However when I run a netstat test it shows that tcp 0.0.0.0:8000 is open and listening but under the program name it is blank. any ideas thanks for helping :)


already port forwarded 8000 in router

I don't have to change the virtual hosts do I? Already tried and didn't seem to work.

---

### Post by Dangertux on 2011-10-12
check out the file /etc/apache2/ports.conf

That should have your answer :-)

---

### Post by 11notes on 2011-10-12
Make sure your VirtualHost and VirtualNamedHost look the same```
NameVirtualHost *:8000
<VirtualHost *:8000>
```

something like this!

---

