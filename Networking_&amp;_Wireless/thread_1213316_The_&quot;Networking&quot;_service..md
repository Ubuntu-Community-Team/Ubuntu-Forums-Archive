---
title: "The &quot;Networking&quot; service."
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by CrAzYoNi on 2009-07-14
Hi all,
I'm working with Ubuntu Jaunty 9.04, 32bit GNOME.

I'm configured my Network (Ethernet as backup network & Wireless as my primary network) statically via X11 --> Network connections.

** Both of my networks are working OK!! **

Though I noticed that if I open a terminal window, stopping the Networking service (sudo service networking stop) I still can ping my router & surf the Internet, how come??

I was assuming that stopping the Networking service will disable all network communication on my system..

I'll really appreciate your information related to this topic.

P.S I'm just learning Linux better, this is how I noticed "this bug".

Cheers,
Yoni D.

---

### Post by martinbaselier on 2009-07-14
service runs the script in /etc/init.d/
It uses ifdown to bring the network down.
I don't have network-manager installed. That might make a difference, since I noticed network-manager works around ifconfig and /etc/network/interfaces.
Try killing network-manager. Use "ps -e | grep net -i" to find the correct name. Then either use kill with the procesid or killall and the name, maybe -KILL as an option to force it. 
After you've done that try stopping the networking service again.

---

### Post by CrAzYoNi on 2009-07-14
You was right, thank you!!
There is another service that controlling the GNOME network communication - I'll check it later on KDE & XFCE env's.

The service name is: NetworkManager.

Thank you.

---

### Post by martinbaselier on 2009-07-14
xubuntu also uses the gnome network manager. Somehow I don't think KDE does ;)

---

