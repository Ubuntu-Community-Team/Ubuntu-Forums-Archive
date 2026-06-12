---
title: "How to install a server VPN , virtual private network, in simply 3 steps only"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by frenchn00b on 2009-11-22
How to install it for having a VPN PPTP for WINDOWS XP?

we are going to use PPOTOP which is in the repositories.

username will be the user login to get access to vpn
secretpassword will be the user password to get access to vpn
10.1.1.5 will be the server vpn IP adress on the local network, that you want to gain access.
10.10.1.10-20 is the range of IP that you will gain and that are reserved.

(1) apt-get install pptpd
(2) add this to /etc/pptpd.conf
```

debug
localip 10.1.1.5
remoteip 10.10.1.10-20,10.1.1.245

```
(3) echo "username * secretpassword * " >> /etc/ppp/pap-secrets

and you can 
```
/etc/init.d/pptpd restart
```

Nota: Openvpn is more secured than PPOTOP
--
here are the client config:
[http://poptop.sourceforge.net/dox/](http://poptop.sourceforge.net/dox/)
xp german: [http://poptop.sourceforge.net/dox/pptp_winxp/VPN_Verbindungsaufbau_mittels_PPTP.pdf](http://poptop.sourceforge.net/dox/pptp_winxp/VPN_Verbindungsaufbau_mittels_PPTP.pdf)

---

