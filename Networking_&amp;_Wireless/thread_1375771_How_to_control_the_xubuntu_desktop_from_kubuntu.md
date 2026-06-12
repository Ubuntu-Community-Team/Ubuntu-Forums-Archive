---
title: "How to control the xubuntu desktop from kubuntu?"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by LK_gandalf_ on 2010-01-08
Hi all, I have a computer with xubuntu 9.10 and a pc with kubuntu 9.10, and I need to operate on the xubuntu desktop from kubuntu. 
On KDE there are Krfb/krdc for the desktop, but what can i install on xubuntu to do this?
Thank you :)

---

### Post by maybeway36 on 2010-01-08
I like to use the minimalist method: install xvnc4viewer and then run it from the terminal or Alt+F2:
```
xvnc4viewer 192.168.1.100
```
(Replace the IP address, of course.)

---

### Post by LK_gandalf_ on 2010-01-08
I have an unexperienced user on the xubuntu side, so I hope this method won't be so difficult :)

what do exactly I have to do? I have to launch that command from xubuntu, without installing anything? and what do I do then after that on kubuntu?

---

### Post by LK_gandalf_ on 2010-01-11
any help?:(

---

### Post by LK_gandalf_ on 2010-02-09
I really need to control my remote computer at home,  it's going crazy, and I'm 2000 km distant. Can anyone help me?
I have a newbie user on the xubuntu side, so I need simple instructions to tell him.
Thank you

---

### Post by Jose Catre-Vandis on 2010-02-09
Needs securing, but for easy access:

[http://bimma.me.uk/2010/01/31/xubuntu-904-quick-and-dirty-vnc-remote-access/](http://bimma.me.uk/2010/01/31/xubuntu-904-quick-and-dirty-vnc-remote-access/)

---

