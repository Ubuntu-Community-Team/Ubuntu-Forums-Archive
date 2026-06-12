---
title: "Wired Internet not getting connected"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by kernelguru on 2012-03-12
Hii, I just connected my nx6310 Compaq series laptop to a CAT-6 ethernet cablle. I installed ubuntu 11.10 in my system, only to find that it wasn't getting connected. I got my IP through a DHCP sever as the cable connection was plug and play. I gave in all the details such as my IP address, gateway and subnet mask. When I tried to click on the mozilla button on my desktop, it showed that server wasn't connected on the webpage. I tried each and every way out, but couldn't get my laptop connected. 


Kindly help ...!!!

---

### Post by Iowan on 2012-03-12
Can you ping an internet site by IP address? (8.8.8.8) I'm wondering if it's a DNS problem.

---

### Post by kernelguru on 2012-03-13
Yeah, I tried everything, even when I ping my local proxy servers, I am able to get responses. Moreover, when I am using windows xp system to connect to the internet, it gets connected easily and the browser also works. But in ubuntu, the browser refuses to show anything except an error message.

---

### Post by varunendra on 2012-03-14
Hi kernelguru, Welcome to the forums!

Please open a terminal and run and post outputs of:
```
ifconfig -a
cat /etc/resolv.conf
cat /etc/network interfaces
route -n
ping -c 4 google.com
```

While posting, click on **#** symbol at the top of the edit box (in which you create new posts) to auto-generate [ Code].. and .. [ /Code] tags, then copy-paste the output code in-between those tags.

---

