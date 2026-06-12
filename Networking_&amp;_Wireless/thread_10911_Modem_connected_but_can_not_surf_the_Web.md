---
title: "Modem connected but can not surf the Web"
date: 2005-01-12
forum: Networking &amp; Wireless
---

### Post by oor on 2005-01-12
Hello,
I installed Ubuntu, my US Robotics external modem was detected and I dial up with gnome-ppp or using pon, I now I am connected because the lights in the modem are on (like in Mandrake, Mepis, Win2k), but when I try to use Firefox, I got a message that service is not available try later and got a blank screen, same thing happen with Mozilla and Gaim or any Internet application

It seems something is blocking my Internet applications to be connected. Please help.

Thanks,

Orlando  :)

---

### Post by m_gasior on 2005-01-24
If you have network card and modem please try this:

sudo pon your_account
sudo route del default
sudo route add default ppp0

If it works you can make a script /etc/ppp/ip-up.local that changes routing table during connection

#!/bin/sh
sudo route del default
sudo route add default ppp0

Remember to make it executable 

sudo chmod +x /etc/ppp/ip-up.local

---

### Post by az on 2005-01-24
sudo tail /var/log/messages

 to see how your connection was established.

Can you ping?
Can you ping ip addresses? (ping  216.239.39.99)?
Can you ping [www.google.com?](www.google.com?)

---

