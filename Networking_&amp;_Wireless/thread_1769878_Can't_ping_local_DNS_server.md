---
title: "Can't ping local DNS server"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by admiralfreak on 2011-05-28
Last night I setup bind9 on my server.  I created a local domain (name.local). The server's ip address is 192.168.1.254

The issue that I'm having is that with my ubuntu laptop, I can't ping the name of the server.
```

user@prefect:~$ ping name.local
ping: unknown host name.local

```

But when I do the same ping from both the server and a XP computer, it will respond.

I can ping the laptop with it's name (prefect.name.local) from both the server and the xp computer.

This is my /etc/resolv.conf file:
```

user@prefect:~$ cat /etc/resolv.conf
domain name.local
search name.local
nameserver 192.168.1.254

```

Also, when I do nslookup name.local or dig name.local, the return with no errors.

Why is it that I can't use the name of the server to access it and that only the ip address works?

Thanks

---

### Post by ratcheer on 2011-05-28
My guess is that it is the firewall. I have the exact same problem reaching my Ubuntu Samba server. Turn off the firewall and it connects just fine.

Tim

---

### Post by admiralfreak on 2011-05-28
Thanks for the help Tim, but that didn't work.

I eventually figured out that it was an issue with my internal FQDN.  Apparently there is some issue with avahi in Ubuntu where 'ping x.name.local' won't work but 'ping x' will.  So I changed it from name.local to name.site and it all works

---

