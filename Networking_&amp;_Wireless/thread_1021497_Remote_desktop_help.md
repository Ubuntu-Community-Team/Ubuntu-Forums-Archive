---
title: "Remote desktop help"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by adamovera on 2008-12-25
I need to setup a remote desktop from one hardy box to another that is not within the network (a few streets over). Basically, my girlfriends mother wants to be able to control her grandson's PC to check his history & make sure he's off the computer after 10:00pm (& turn it off remotely if he's not). I have been able to do this from my girlfriend's & my computer, but they are in the same home network, in the same house. His grandmother is on the same ISP, but down the street, so not on our home network. When I go to remote desktop viewer on her PC, what host & domain do I need to input? It would not be local & the IP address (of the grandson's PC) is not working in the host name box. I've been able to do this before, maybe a year ago with 7.10, & for the life of me I cannot remember how. Someone please help me, I don't want to be the net nanny, I've got way too much to do as it is.

BTW: All PC's in question are running 8.04 LTS, so no conflicts there. I am also aware that it is unsecure to remote view & control over the internet, but we're talking about an 11 year old here (who only plays games & BS's online) so I don't really care. Any help would be appreciated.

---

### Post by cariboo on 2008-12-25
You need to setup port forwarding on the Grandmothers's router, then access it using her external ip address. I would suggest using a strong password, as remote desktop access seems to be an easy way for crackers to break into computers.

Jim

---

### Post by adamovera on 2008-12-25
The grandmother does not have a router, only a cable modem. Do I need to use the broadcast address of the grandson's PC (located underneath the IP address in connection information) instead of the IP address? Do I insert that address in the host box in the remote desktop viewer on the grandmother's PC?

---

