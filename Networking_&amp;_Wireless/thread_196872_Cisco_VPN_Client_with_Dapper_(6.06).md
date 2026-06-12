---
title: "Cisco VPN Client with Dapper (6.06)"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by K0LO on 2006-06-14
Has anybody gotten Cisco's VPN Client working with Dapper? I ran version 4.7.00 on Breezy (5.10) for a long time without any problems. After upgrading to Dapper, I couldn't get the Cisco client 4.7.00 to assemble without errors. After reading several posts, the recommendation was to use Cisco VPN Client version 4.8.00, which assembled without error and works.

HOWEVER, the client will not start up as a normal user. I get the following error message:
privsep: unable to drop privileges: group set failed.
The application was unable to communicate with the VPN sub-system.

If I start the client as root (sudo vpnclient connect (profilename), then it works fine.

Any suggestions?

Yes, I know about vpnc or kvpnc; I've tried to get these working several times now and they don't authenticate with my company's VPN concentrator; only the Cisco client will work.

---

### Post by K0LO on 2006-06-15
Got it. From [ http://jason.roysdon.net/?p=780#more-780]( http://jason.roysdon.net/?p=780#more-780)

> 
     [SIZE="1"] iaincurt said,
      May 29, 2006 at 12:00 pm

      Jason,

      I have managed to get rid of the privsep error by running:
     ** chmod 4111 /opt/cisco-vpnclient/bin/cvpnd**
      Hope this helps.

      Iain[/SIZE]

It did. No more error message. Now the VPN client can be started by a normal user without needing root privileges.

Mark

---

