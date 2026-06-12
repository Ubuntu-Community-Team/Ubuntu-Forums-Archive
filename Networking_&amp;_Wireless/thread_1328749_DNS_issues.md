---
title: "DNS issues"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by JohnCaver on 2009-11-16
Hi,

I'm having problems with dns in Ubuntu.
My router is correctly configured and has a connection to the internet. DNS is set to use my ISP's. 

The diagnostics page in the router is correctly looking up IP addresses, which I can then ping.
However if I try to ping the name of the site from the command prompt, it cannot find it, nor can I access sites by name in Firefox.

I have tried rebooting my router, and doing
```
sudo /etc/init.d/networking restart
```but nothing has helped.

Does anyone have any ideas, or some further diagnostics I could do?

Thanks

---

### Post by doas777 on 2009-11-16
can you ping 4.2.2.1?

please post the output of:
```

sudo cat /etc/resolv.conf

```

---

### Post by JohnCaver on 2009-11-16
Thanks doas777 you have just solved my problem!

The output of ```
sudo cat /etc/resolv.conf
```was nameserver 192.168.1.1
which needed to be 192.168.0.1.

I changed it accordingly and I'm back online, thanks.
It is interesting that the router has one setting and Ubuntu has another in a text file.

---

### Post by Iowan on 2009-11-16
Which release are you running?
Does machine get IP address via DHCP?

Never mind... 'ya found it!

---

