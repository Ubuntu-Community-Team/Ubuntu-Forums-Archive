---
title: "Internet access problem"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by chitragurung on 2011-01-18
Hello,
 
Finally I got success in setting up of CDMA USB modem but I could not access the internet or browse the internet. I can only download message and send messages using through evolution. But can browse internet.
 
How can I fix it.

---

### Post by dineshs on 2011-01-19
After connecting,
If you get reply for ```
ping -c3 4.2.2.1
```but not for ```
ping google.com
```try this
Rightclick [COLOR="Blue"]Network manager[/COLOR] icon on left top -edit connecctions-mobile broadband-select the connection-edit-ipv4-method=Automatic (ppp addresses only) -Give DNS as 4.2.2.1-apply then reboot PC.
If you are connecting via [COLOR="Blue"]wvdial[/COLOR] run```
sudo gedit /etc/resolv.conf
```
and add this as first line
```
nameserver 4.2.2.1
```
Then reboot

---

