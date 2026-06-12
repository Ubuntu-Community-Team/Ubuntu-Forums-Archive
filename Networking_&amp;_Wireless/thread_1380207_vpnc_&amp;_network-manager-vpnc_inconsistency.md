---
title: "vpnc &amp; network-manager-vpnc inconsistency?"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by nasp on 2010-01-13
Hey all!

I've been trying to connect to my office Cisco VPN several time using the network-manager-vpnc GUI in Ubuntu Karmic with no success. I read a couple of articles and i tried using the direct command line way:

```
sudo vpnc office
```

with the following /etc/vpnc/office.conf file:

*This is fictional data*

```
IPSec gateway vpn.office.com
IPSec ID office
IPSec secret 0ff1c3
```

which worked perfecly.

So i went back to the Network Manager GUI way and i used the same credentials.

*Same fictional data*
[IMG]http://dl.dropbox.com/u/2759157/network-manager-vpnc.png[/IMG]

I got a libnotify message telling me it couldn't connect.

Anyone know how i could troubleshoot this issue? Would be great to have it integrated in gnome instead of running a background command which is not tracked by nwm.

Thanks!

Simon

---

### Post by nasp on 2010-01-13
Did anyone encountered the same issue?

---

### Post by PsyWolf on 2010-03-21
Yea, I'm having the same problem.  I can connect fine with vpnc through the command line, but I can't get it to work through the network manager.  
This is what my vpnc config file looks like (where the things in italics are of course replaced with what they happen to be in my specific case)


```
IPSec gateway *GatewayName*
IPSec ID *GroupName*
IPSec secret *GroupPassword*
Xauth username *MyUserName*
Xauth password *MyPassword*
Local Port 0
```

This isn't a complicated config file.  (btw, adding .conf import support to the network manager plugin would be awesome)

---

### Post by rickzoll on 2010-03-25
Yes, I'm having the same problem.

---

### Post by yoshim on 2010-09-11
yea i was searching for this, does anyone have a solution to this, i dont want to go to command line everytime to log in. I think the VPN network manager is showing me that its logged in, but I can't access anything at school when I connect through network manager.

---

### Post by Orlsend on 2010-12-23
I also eaxpeirence the very same Problem. any ideas? I may just have to use the cli version. but this is a MUST for Ubuntu!

---

### Post by shrijith1 on 2011-03-14
I had the same issue, but the solution was simple and weird....I just unchecked "Available to all users" and it worked for me....Check it out...

---

