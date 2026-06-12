---
title: "apt.conf is not updated correctly"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by AboSamoor on 2010-06-19
Updating Synaptic with authenticated proxy settings make it works.

However, apt-get command line tool does not work.

/etc/apt/apt.conf is not updated correctly. It has the 
Acquire::http::proxy "http://10.1.1.2:80/";
instead of 
Acquire::http::proxy "http://mhm9050061:1234@10.1.1.2:80/";

Which program is responsible for updating such file ?

---

### Post by tankist on 2010-06-21
Similar problem here. Setting proxy in Synaptic works, but setting the same proxy in /etc/bash.bashrc doesn't make apt-get to work.

---

