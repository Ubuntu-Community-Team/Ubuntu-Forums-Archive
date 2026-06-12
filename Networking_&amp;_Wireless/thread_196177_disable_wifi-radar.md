---
title: "disable wifi-radar"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by skale on 2006-06-13
How to do it?

---

### Post by Dr. Nick on 2006-06-13
Can you be a bit more specific? If you want to disable it then why not just apt-get remove it? I notice it runs as a service sort of, but not sure what use the program is worth if you disable it

---

### Post by skale on 2006-06-13
I was following the broadcom wireless driver instructions and when I try to install the "experimental package" it says 

> Note you need to DISABLE thndiswrapper and wifi-radar for the driver to work properly!
or something like that.
The guide shows how to disable ndidwrapper but not wifi-radar. 

Thats all.

---

### Post by Dr. Nick on 2006-06-13
open a terminal and type 

sudo killall wifi-radar

If it is running that will close it, most likely though unless you installed it yourself it should not be running. if you installed it and it must be disabled then I would just use synaptic or the like to uninstall it


Hope this answers your question.

---

