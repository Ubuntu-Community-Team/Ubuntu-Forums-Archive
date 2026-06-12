---
title: "Make Windows XP remotely connect to the internet"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by gyppo on 2009-08-12
I'm on a Jaunty machine connected to the internet through one running XP. While I can remotely startup (Magic Packets) and shutdown (net rpc shutdown -I 192.xxxxxxx) the XP machine, it does not automatically connect to the internet. Instead it needs a username and password. When I connect to the XP machine Ubuntu tries to make it connect, but (I suspect becuase my passwords and usernames are different on the different machines) it fails. The XP machine just keeps retrying, I suspect using my Ubuntu login details.

I'm sure there's a setting somewhere I've overlooked, but I have no idea where to look for it anymore. Could someone point me in the right direction?

Also, how could I prompt the XP machine to connect to the internet manually, even if it didn't try to connect automatically?

Hope you can help,
Thanks

---

### Post by superprash2003 on 2009-08-12
is this a DSL connection or cable?

---

### Post by gyppo on 2009-08-12
Lan cable to the xp machine which has a USB modem to DSL (I think).

---

### Post by superprash2003 on 2009-08-13
so do you use a dialer in windows xp to connect to the internet?

---

### Post by gyppo on 2009-08-14
Yes, I'm pretty sure I do.

---

### Post by superprash2003 on 2009-08-14
do you know the username and password of the DSL connection? if so , you could insert them in your DSL modem so that the modem automatically connects to the internet when it gets disconnected , you dont have to worry about the dialer anymore.. which ISP do you use?

---

### Post by gyppo on 2009-08-15
Yes, I know the username and password, and the ISP is Tiscali. However, I still want to have to put in a password to access the internet from the XP machine. Is there a way to give Ubuntu the credentials of the XP machine? At the moment Ubuntu is forcing the XP machine to try and connect using my Ubuntu username/password, whenever I connect the two.

---

### Post by superprash2003 on 2009-08-17
i dont think that is possible , ubuntu will not be able to tell xp to connect , you could try bridging the two interfaces in the xp and then try creating a dialer in ubuntu ( similar to xp , go to system->preferences->network configuration->DSL ) , but then only ubuntu would get internet access and not windows

---

