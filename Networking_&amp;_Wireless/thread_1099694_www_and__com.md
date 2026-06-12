---
title: "www and  com?"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by rplantz on 2009-03-18
I have set up a web server on my Ubuntu desktop machine. I wish to keep it visible only on my LAN. (See [http://ubuntuforums.org/showthread.php?t=1096058](http://ubuntuforums.org/showthread.php?t=1096058) )

Firefox on my Vista machine finds [http://bob-desktop/~bob](http://bob-desktop/~bob) just fine.

But Firefox on my Ubuntu laptop and on my Mac OS X insists on changing it to [http://www.bob-desktop.com/~bob](http://www.bob-desktop.com/~bob)

Who is inserting the "www" and "com" on Ubuntu and Mac OS X?

---

### Post by ugm6hr on 2009-03-18
Can you access it using the ipaddress?

If yes, it is presumably a dns resolution issue.

If you use DHCP, this might help: [http://www.cyberciti.biz/faq/howto-get-linux-static-dhcp-address](http://www.cyberciti.biz/faq/howto-get-linux-static-dhcp-address)

Just replace *vivek-laptop* with **bob-desktop**

---

### Post by punx45 on 2009-03-18
is firefox auto filling the www and com in the address bar while you type, or is it automatically adding it after?   i dont have that issue on my mac.   i have an /etc/hosts file set up on it, so that might make a difference.

---

### Post by rplantz on 2009-03-18
> **punx45 said:**
> is firefox auto filling the www and com in the address bar while you type, or is it automatically adding it after?   i dont have that issue on my mac.   i have an /etc/hosts file set up on it, so that might make a difference.

Firefox adds it a few seconds after I type. The problem with using /etc/hosts is that my router is set to be a DHCP server. I could change it to static IP addresses, but it seems like there should be a way to do everything dynamically.

> **ugm6hr said:**
> Can you access it using the ipaddress?

If yes, it is presumably a dns resolution issue.

If you use DHCP, this might help: [http://www.cyberciti.biz/faq/howto-get-linux-static-dhcp-address](http://www.cyberciti.biz/faq/howto-get-linux-static-dhcp-address)

Just replace *vivek-laptop* with **bob-desktop**

Yes, I can access it with the IP address. But since I'm using DHCP server on my router, I have to look up the current IP address each time.

Thank you for the link. I'll take a look.

BTW, this is a learning situation for me. I realize that I could get it to work by using static routing, etc. I'm retired, and I simply enjoy playing with this stuff. :-)

---

### Post by punx45 on 2009-03-18
before or after you hit enter?

so the dhcp server is managing host names?   by the way, general rule of thumb is that servers get static ips, even locally.   its pretty easy to do.

---

### Post by rplantz on 2009-03-18
> **punx45 said:**
> before or after you hit enter?


I think it's after. The other machines are not up right now, and I have to run off to a class I'm taking on parallel processing.

> 
so the dhcp server is managing host names?   by the way, general rule of thumb is that servers get static ips, even locally.   its pretty easy to do.

I'm coming to the conclusion that I should set up my router for static IP addresses on my LAN. Then I can simply use /etc/hosts for name resolution. I will still connect to my ISP with DHCP since I don't don't really have a need to pay extra for a static IP address from them.

Thank you for your help. Am I headed in the right direction?

---

### Post by ktrnka on 2009-03-18
If you ran your own dns server, it would make it so you wouldn't have to edit the /etc/hosts file on every machine.

---

### Post by punx45 on 2009-03-18
the only  computer that needs to have a static IP is the one with the web server, and you dont need to configure it in the router, it is configured on the machine itself in /etc/network/interfaces

---

### Post by rplantz on 2009-03-20
> **punx45 said:**
> the only  computer that needs to have a static IP is the one with the web server, and you dont need to configure it in the router, it is configured on the machine itself in /etc/network/interfaces

Thank you. I finally figured it out:
```

bob@bob-desktop:$ cat /etc/network/interfaces
auto eth0
iface eth0 inet static
address 192.168.1.47
netmask 255.255.255.0
gateway 192.168.1.1

```

But now when I boot my machine it spends 5 minutes
```

Configuring network interfaces...

```
(It takes so long that it drops into terminal mode.)

I still have my router configured as a DHCP server for my other machines.

Where should I be looking for this 5 minute delay?

---

