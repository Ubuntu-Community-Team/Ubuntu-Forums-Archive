---
title: "Access &quot;NetworkManager.conf&quot; as root"
date: 2012-12-22
forum: Networking &amp; Wireless
---

### Post by abelgkb on 2012-12-22
I've been having trouble accessing NetworkManager.conf in Ubuntu 12.10 as root. I need to change the "False" to "True" on NetworkManager. So far, I've tried opening it through terminal as sudo, but no luck. I keep getting the "no such file" message from Bash.
HELP please! I need to get my ethernet working ASAP.
Thanks in advance.

---

### Post by chili555 on 2012-12-22
Please try:```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```The file will open in the text editor and you may make your change. Proofread carefully, save and close gedit. For your change to take effect, you'll need to restart NM:```
sudo service network-manager restart
```

---

### Post by Cheesemill on 2012-12-22
> **chili555 said:**
> Please try:```
sudo gedit /etc/NetworkManager/NetworkManager.conf
```
Don't use sudo for graphical applications, you should always use gksudo instead.

---

### Post by chili555 on 2012-12-22
> **Cheesemill said:**
> Don't use sudo for graphical applications, you should always use gksudo instead.Could you please tell us what the practical difference is? What does gksudo do that sudo does not or vice versa?

---

### Post by Cheesemill on 2012-12-23
> **chili555 said:**
> Could you please tell us what the practical difference is? What does gksudo do that sudo does not or vice versa?
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by chili555 on 2012-12-24
> **Cheesemill said:**
> [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)Thank you.

---

### Post by abelgkb on 2012-12-28
Thanks a lot, that did the trick.

---

