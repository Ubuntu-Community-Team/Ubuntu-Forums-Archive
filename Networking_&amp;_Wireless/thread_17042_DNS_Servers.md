---
title: "DNS Servers"
date: 2005-02-25
forum: Networking &amp; Wireless
---

### Post by mark52230 on 2005-02-25
Hi,

I've just installed Ubuntu and it's going great but I'm having a problem with my Internet. My computer is connected to a router which acts as my DHCP server. It should send the correct DNS servers to Ubuntu but it does not. Ubuntu thinks that the I.P of the router is a DNS server which is wrong. This results in it taking longer to access websites. When I attempt to use the network settings tool to input the correct DNS servers, they just get wiped on reboot and the I.P of the router is put back there. How can I prevent it resetting every time I reboot?

Thanks..

Edit: Just seen the sticky thread about this very subject and nothing in there worked..

Edit 2: I've just noticed that Firefox 0.9.3 is installed and apt-get tells me that it is the latest version however version 1.0 has been out for a long time and 1.01 was actually released today. Is software not updated that often?

---

### Post by az on 2005-02-25
"a router which acts as my DHCP server. It should send the correct DNS servers to Ubuntu but it does not. Ubuntu thinks that the I.P of the router is a DNS server which is wrong. "

Well, is it a dns server or is it not?  Routers usually do dns caching for you.


"input the correct DNS servers, they just get wiped on reboot and the I.P of the router is put back there. How can I prevent it resetting every time I reboot?"

Tell your router to use whatever nameservers instead of what it is getting by dhcp or pppoe...



"Edit: Just seen the sticky thread about this very subject and nothing in there worked.."

That thread seems pretty useless to me.


"Edit 2: I've just noticed that Firefox 0.9.3 is installed and apt-get tells me that it is the latest version however version 1.0 has been out for a long time and 1.01 was actually released today. Is software not updated that often?"

Once a release is out, the packages do not change.  Look for more recent software in Hoary.  It is not stable yet, though.

---

### Post by mark52230 on 2005-02-25
I'm slightly confused by your post but thanks for replying..

My router gets the correct DNS servers from my ISP but it doesn't pass them to Ubuntu.. Ubuntu just thinks that 192.168.0.1 is the only DNS server when that is the I.P of the router.. If that makes sense..

Edit: The correct DNS servers are 194.106.56.6 and 194.106.33.42..

---

### Post by az on 2005-02-25
Your /etc/resolve.conf is rewritten every time youmake  a dhcp connection.

Typically, a router runs it's own dns server which keeps addresses in memory (cache).  This is supposed to make routing faster.  That is why a computer which gets it's ip address by dhcp from a router will get the router's ip address as the dns nameserver.

It's not really a dns server but dns masquerading.  Anyway.

Usually, you can tell the router to pass on certain nameservers instead of the router's.  


You can also connect your computer to your router with a static address.  You then have control of your nameservers.  Resolve.conf is only rewritten if you make a dhcp or pppoe connection.

---

