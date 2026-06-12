---
title: "dhclient writing bad address for DNS server"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by rcdawson on 2011-01-12
After installing 10.04 I found that URLs could not be resolved.  Checked /etc/resolv.conf and found that it listed 208.55.220.220 and 208.55.222.222.
My router says that it its primary and secondary DNSs are 208.67.220.220 and 208.67.222.222.  

I "fixed the problem by adding a line in /etc/dhcp3/dhclient.conf after the "request subnet-mask, ........, domain-name-servers, ........ command.  The added line reads:  prepend domain-name-servers 208.67.222.222, 208.67.220.220;

With those changes I now get the following DNSs in etc/resolv.conf: 

208.67.220.220
208.67.222.222
208.55.220.220

Where can the 208.55.220.220 address be coming from?  I thought perhaps that I could eliminate the "domain-name-servers, from the request, but when I did that, even with the prepend statement in place, there were no DNS servers listed in resolv.conf.

Thank you in advance.

Richard

---

### Post by suseendran.rengabashyam on 2011-01-12
Hi,

Remove the line 
> prepend domain-name-servers 208.67.222.222, 208.67.220.220;
from /etc/dhcp3/dhclient.conf

Create a file /etc/dhcp3/dhclient-enter-hooks.d/nodnsupdate with the following content
> 
#!/bin/bash
make_resolv_conf() {
        :
}


Save and close the file and set the permissions:
# sudo chmod +x /etc/dhcp3/dhclient-enter-hooks.d/nodnsupdate

Now make the necessary changes to /etc/resolv.conf and reboot the machine.

Let me know if this works.

---

### Post by ripat on 2011-01-12
You can also use the *supersede* rule instead of *prepend* in the dhclient.conf file.

---

### Post by rcdawson on 2011-01-12
But where do the 208.55.220.220 and 208.55.222.222 addresses come from?  Is my router giving out a faulty address, or is there somewhere in my computer that this address is created?

Just curious.

---

### Post by ripat on 2011-01-12
If you don't have them hard coded in your resolv.conf or dhclient.conf it can only be coming from a DHCP server. Are you sure you only have one DHCP server on your lan?

What's the result of:
```
$ sudo dhclient
```

---

### Post by basketcase on 2011-01-12
> **suseendran.rengabashyam said:**
> Hi,

Remove the line 

from /etc/dhcp3/dhclient.conf

Create a file /etc/dhcp3/dhclient-enter-hooks.d/nodnsupdate with the following content


Save and close the file and set the permissions:
# sudo chmod +x /etc/dhcp3/dhclient-enter-hooks.d/nodnsupdate

Now make the necessary changes to /etc/resolv.conf and reboot the machine.

Let me know if this works.

Doesn't work for me...

---

### Post by ripat on 2011-01-12
Although creating a hook works, I would not recommend it. You could forget you have created one and when you take your laptop on another network you end up not knowing why dhclient doesn't get a suitable dns nameserver adress from the dhcp server. Use the *prepend* rule in the dhclient.conf file.

---

