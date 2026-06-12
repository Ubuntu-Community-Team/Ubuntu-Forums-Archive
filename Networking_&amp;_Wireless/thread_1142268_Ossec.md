---
title: "Ossec"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by ehsun7b on 2009-04-29
*[COLOR="SandyBrown"]At first: I'm not sure it is a right place to ask such a question or not![/COLOR]*

I've installed OSSEC Intrusion Detection System on my machine [COLOR="DarkRed"](HP dv6000 laptop - Intel - Ubuntu 8.10)[/COLOR]. During the installation process it asked me for installation path and it was suggesting **/var/ossec** and I entered** /var/ossec/local_install**.
Now I want to remove the software. How can I do that? I know It may not be possible by means of **apt-get remove** command, since I have not installed it using the package manager. 
**So what should I do? Can I just delete the directory (/var/ossec)? **

---

### Post by ehsun7b on 2009-04-30
I found this somewhere, please tell me if you think it is not enough:

[B]rm -rf /var/ossec
rm -f /etc/init.d/ossec
rm -f /etc/ossec-init.conf [/B]

---

