---
title: "Ubuntu server Internet connection"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by BenypX on 2011-06-28
Hey guys, I am trying to change my DHCP to Static IP, and I got it to do that, and on my network like from another computer on the router, I can go to my address and I see the page that tells me it got enabled, but the internet doesn't work. It's weird that I can't connect to the actual internet, if anyone can help me that would be great... also, if u need me to give you more details let me know. Thanks.

---

### Post by papibe on 2011-06-28
Could you post your /etc/network/interfaces ?

Regards.

---

### Post by BenypX on 2011-06-28
auto etho0 
iface eth0 inet static
address 192.168.1.8
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.254 (ive also tried 192.168.1.1 for gateway but no luck..)

/etc/resolv.conf

nameserver 192.168.1.1

---

### Post by papibe on 2011-06-28
It is probably 192.168.1.1 if your router also serves as DNS.

Did you restart the network services? If not try:
```
$ sudo service networking restart
```

---

### Post by BenypX on 2011-06-28
ok, yes I tried your command and it doesn't work, but the command I use 
sudo /etc/init.d/networking restart

that command works in restarting the network, im just not getting any internet connection

---

### Post by BenypX on 2011-06-28
nevermind, I got it to actually work :) thanks a lot, changing the gateway again and restarting seems to have made it work. lol thank you. Ill be closing the thread now but probably open another one later when I try to put my domain on the server I just made. Thanks!

---

