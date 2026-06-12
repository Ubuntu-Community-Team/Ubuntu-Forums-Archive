---
title: "Changing IP address to remove conflict"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by davelbarton on 2009-02-07
OK, this may be more newbie stuff, but I can't find anything that *quite* covers this.  I am using a specialized VPN server and that server uses an IP address range "for its own purposes" that clashes with mine.  How can I find another appropriate IP address?  Do I have to ask my ISP?  Can I use my actual, physical IP address (as opposed to those fairly standard 192.168.inchy.squat numbers?  How can I move my IP address out of the conflict zone?

---

### Post by davelbarton on 2009-02-08
Bump.

I *really* need help with this.

---

### Post by FishRCynic on 2009-02-08
> **davelbarton said:**
> OK, this may be more newbie stuff, but I can't find anything that *quite* covers this.  I am using a specialized VPN server and that server uses an IP address range "for its own purposes" that clashes with mine.  How can I find another appropriate IP address?  Do I have to ask my ISP?  Can I use my actual, physical IP address (as opposed to those fairly standard 192.168.inchy.squat numbers?  How can I move my IP address out of the conflict zone?

is your vpn server this one?
[http://forums.bit-tech.net/showthread.php?t=132029](http://forums.bit-tech.net/showthread.php?t=132029)

---

### Post by davelbarton on 2009-02-08
> **FishRCynic said:**
> is your vpn server this one?
[http://forums.bit-tech.net/showthread.php?t=132029](http://forums.bit-tech.net/showthread.php?t=132029)

I'm afraid not.  Mine is some super duper Cisco specific VPN server.  Let me be specific; I'm a client trying to get onto the server, and that's where the IP address clash is.

---

### Post by FishRCynic on 2009-02-08
do you have the cisco vpn client?

see if these help

[http://thoughtworker.in/2008/11/19/ubuntu-cisco-vpn-client-installation-on-intrepid/](http://thoughtworker.in/2008/11/19/ubuntu-cisco-vpn-client-installation-on-intrepid/)

[http://blog.evolutioncreations.com/2008/06/installing-cisco-vpn-client-48-on.html](http://blog.evolutioncreations.com/2008/06/installing-cisco-vpn-client-48-on.html)

[http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/](http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/)

---

### Post by superprash2003 on 2009-02-08
do you mean your local 192.168.x.x ip is conflicting with your vpn ips ( which are also in the 192.168.x.x range) .. if so , just change the ip address of your router..

---

