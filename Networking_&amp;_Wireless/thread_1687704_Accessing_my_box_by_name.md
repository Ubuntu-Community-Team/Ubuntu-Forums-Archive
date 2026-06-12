---
title: "Accessing my box by name?"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by VolatileVoid on 2011-02-14
Hi all -

I've just installed Ubuntu 10.10 on my new box, along with all the required updates, etc. I named my box when prompted, and it even shows up on my router's configuration page by name in the list of DHCP clients.

I then installed openssh-server and tried to ssh into my box from my laptop. All I did was:
**ssh myservername**
Sadly, this did not work. But when I did:
**ssh 192.168.1.130 **(or whatever its IP address was at the time), it worked just fine.

What do I need to do to be able to access my box by name instead of by address? 

Thanks! :)

---

### Post by cjhabs on 2011-02-14
The easiest way is to simply add it to the hosts file on the laptop - this works if the laptop is Windows or Ubuntu, just the file locations are different.
/etc/hosts on Ubuntu
c:\windows\system32\drivers\etc on windows

---

### Post by Grenage on 2011-02-14
Just make sure that the machine IP address won't change.  The easiest thing to do is set a DHCP reservation in the router configuration.

That basically ensures that a device with a particular MAC address, gets a particular IP address - then your hosts file entry will always be valid.

---

### Post by VolatileVoid on 2011-02-14
> **cjhabs said:**
> The easiest way is to simply add it to the hosts file on the laptop - this works if the laptop is Windows or Ubuntu, just the file locations are different.
/etc/hosts on Ubuntu
c:\windows\system32\drivers\etc on windows

Ah so there's no way to have the router resolve it directly, then? I figured it'd be smart enough to look up the server name in its DHCP Client list. Bah. :)

Thanks.

---

### Post by Grenage on 2011-02-14
You'd think so, wouldn't you?  My home router knows the name of my computers - it lists them next to the DHCP reservation.  Unfortunately it doesn't usually resolve it for the clients.

---

### Post by tgm4883 on 2011-02-14
DHCP doesn't do name resolution. That would be DNS. IIRC, it depends on what you have your DNS server set to on your laptop. If it's set to your router, it should resolve the machine name just fine. If it's set to something external of your network, then it won't work because you ISP's DNS server doesn't know about your machine.

---

### Post by Iowan on 2011-02-14
I took DHCP away from my router/modem, and gave it to another machine (server) that has **DNSMasq** (which seems to do a wonderful job of combining DHCP and DNS).

---

