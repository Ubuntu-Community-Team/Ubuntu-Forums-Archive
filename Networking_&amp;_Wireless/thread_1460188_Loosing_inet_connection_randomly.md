---
title: "Loosing inet connection randomly"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by orrie on 2010-04-22
My server has two interfaces eth0 and eth1.

The internet is located at eth0, and the local net is on eth1.
On this server I have squid installed, to let other computers in the local net surf the internet without having a internet-connection at the physical computer, but through the server.

This was working pretty well, until now when the server loosing the internet-connection at every minute or so.
This is starting to be very annoying, and I want to fix it asap.

There's no problem with the local net, just the internet.

The temporary solution to fix this, is to run a *dhclient eth0* on the server, and it gets internet again.
But the point is gone, if I'm going to do this every minute.

How to fix this?

---

### Post by terazen on 2010-04-22
When the internet goes away can you still ping your eth0 default gateway and external dns servers?

If you can ping the default gateway, but not the external dns, then it might be a routing issue where your server thinks the internet connection is eth1.

---

### Post by Iowan on 2010-04-22
It seems an unlikely cause, but can you check the lease time (expiration)?

---

### Post by computer13137 on 2010-04-22
Is the Internet connection actually failing on the server, or is it just the computers that rely on it for connectivity?

During this failure, do you have any problems contacting the server from the internal network?

Kirk

---

### Post by orrie on 2010-04-22
> **terazen said:**
> When the internet goes away can you still ping your eth0 default gateway and external dns servers?

If you can ping the default gateway, but not the external dns, then it might be a routing issue where your server thinks the internet connection is eth1.

The only way to get logged into the server now, is by running ssh to my machine through the inet and then ssh to the server through the local net, since the server isn't responding to ssh-requests at the inet (eth0).

Since it at the moment working I can't find out, but what if I can't do it and the routing isn't a problem?



> **Iowan said:**
> It seems an unlikely cause, but can you check the lease time (expiration)?
```

root@unixcoder ~ ;) cat /etc/dhcp3/dhclient.conf | grep lease
#send dhcp-lease-time 3600;

```



I'm suspecting that it is the integrated network card that is the problem here, but I'm not really sure about it.
What's your opinion?

---

### Post by Iowan on 2010-04-22
> **orrie said:**
> 
```

root@unixcoder ~ ;) cat /etc/dhcp3/dhclient.conf | grep lease
[COLOR="Red"]#send dhcp-lease-time 3600;[/COLOR]

```
This line is commented out. You might check */var/lib/dhcp3/dhclient.eth0.leases*

---

### Post by orrie on 2010-04-22
> **Iowan said:**
> This line is commented out. You might check */var/lib/dhcp3/dhclient.eth0.leases*
Correct. That's why I tried to emphasize it.


Attached is the file *dhclient.eth0.leases*, and as you can see this is very old IP-adresses that are not in use at all today. (That's why I'm not censoring it)

---

