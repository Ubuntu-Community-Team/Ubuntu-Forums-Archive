---
title: "Run a program when network connection is established"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by gagan_mishra on 2010-01-05
I want a program (shell script) to be executed as soon as my DHCP connection is established successfully.

Is there any way I can do this ?

Thanks
Gagan

---

### Post by prshah on 2010-01-05
> **gagan_mishra said:**
> I want a program (shell script) to be executed as soon as my DHCP connection is established successfully.
Is there any way I can do this ?

Maybe you can take a look at the /sbin/dhclient-script file ?

---

### Post by gagan_mishra on 2010-01-06
Hi,

I got the folder where I need to put the script.

For dhcp its /etc/dhcp3/dhcp-exit-hooks.d/
and for direct connection, to run the script as soon as network is up, the folder is (dont remember exactly ): /etc/network/if-up.d/

Thanks
GBM

---

