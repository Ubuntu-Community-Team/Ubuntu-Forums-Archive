---
title: "Can't use ssh user@router-ip"
date: 2012-09-22
forum: Networking &amp; Wireless
---

### Post by Machinator on 2012-09-22
Hello I'm trying to connect to an ubuntu machine through ssh.

ssh user@192.168.x.x  - this works perfectly.

ssh user@84.190.x.x  (current external ip of the router) - this doesn't work at all, ssh command just hangs and does nothing, no error message.

I have added a rule for portforwarding for port 22 to the router.

Do I need to do anything else? Or is there any other way to do this?

Thank you.

Update: could it be loopback?! I'm trying it from inside the same network.

---

### Post by Machinator on 2012-09-22
It was a loopback. I've tried to connect through a proxy and it works. I'm sorry for disturbance.

---

### Post by hakermania on 2012-09-22
The usual way is the following (after you set up ssh):

1) You go to the modem and declare a static IP for you PC's mac address
2) You redirect a port (preferable NOT 22, because it is the default, and it is about 90% sure that you will experience attacks, change the port to the machine running the ssh server through the configuration and then redirect to this port through your modem)
3) (Optional) Setup a Dyn DNS account and link it to your modem so as to be able to access your modem without the need to know your external IP always (in case it isn't static)
4) ssh into your modem via the external IP (or the "domain name" if you have set up a dyn dns account)

---

