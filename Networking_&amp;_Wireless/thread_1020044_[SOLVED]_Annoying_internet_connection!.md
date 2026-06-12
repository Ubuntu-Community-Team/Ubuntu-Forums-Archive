---
title: "[SOLVED] Annoying internet connection!"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by lonecrow on 2008-12-23
Hello all, 

At every say 2-3 hours, my internet connection will just disconnect and I have to reboot the computer to get it back working. This is really annoying and I'm sure there is a way to juste restart that?! I tried /etc/init.d/networking restart but it doesnt work.

Any ideas?

Thanks and happy holidays :)

---

### Post by ieee488 on 2008-12-23
[http://www.cyberciti.biz/faq/ubuntu-restart-start-stop-networking-service-howto/](http://www.cyberciti.biz/faq/ubuntu-restart-start-stop-networking-service-howto/)

---

### Post by lswb on 2008-12-23
Is your network connection normally handled by Network Manager or some other method? Are you perhaps connecting directly to a DSL modem (no router) using pppoe? If so a command like "pon dsl-provider" or "pppd call dsl-provider" may work. "dsl-provider" may need to be replaced with the name of the relevant file for your connection from /etc/ppp/peers.

Can you check in your log files ( /var/log/syslog or /var/log/messages ) and see what the errors are when the network disconnects?

---

### Post by lonecrow on 2008-12-25
UPDATE:

As I previously said, here is the excerpt of my ```
networking restart 
```command:

```
matt@AQUARIUS:~$ sudo /etc/init.d/networking restart
[sudo] password for matt:
 * Reconfiguring network interfaces...Ignoring unknown interface wlan1=wlan1.
                                                                         [ OK ]
matt@AQUARIUS:~$
```

And regarding the ```
/var/log/syslog
```and ```
/var/log/messages
``` There is nothing in there regarding my wireless device when it disconnects. By the way, it doesn't disconnects, it just stop transfering data FROM and TO. Meaning, I'm still connected. But when I just disconnect and try to reconnect, it never does.

Any other ideas?

---

### Post by lonecrow on 2008-12-26
bump

---

### Post by lswb on 2008-12-26
There are many variations of networking and solutions to problems must be tailored to the circumstances. Please post the output of the command "ifconfig" while the connection is working and while it is not working. More information would be helpful. You mentioned wireless in one post, is that what you connect with. Is your system using Network Manager to handle the connection or some other method? What is the nature of your upstream network connection, i.e. cable/DSL modem, router, etc.

---

### Post by lonecrow on 2008-12-27
Well I finaly figured it out thanks to the help of another forum. I now use Wicd for my connection manager, and deluge as my client (torrent).

Eveyrthing is perfect now :)

---

### Post by htmlland on 2008-12-27
You can set threads as "Solved" under thread tools at the top of the thread.

Thanks :)

---

