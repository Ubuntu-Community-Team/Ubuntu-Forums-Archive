---
title: "PPTP not working from NetworkManager in Jaunty"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by extraspecialbitter on 2009-05-04
I've just installed Jaunty and thought I'd try connecting to my workplace VPN via pptp.  I configured MSCHAP and MSCHAPv2 on as recommended elsewhere on the forums, but so far run haven't been able to get around the following error:

```
May  4 16:40:01 bangcrunch /USR/SBIN/CRON[14338]: (root) CMD ([ -x /usr/sbin/upd
ate-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  4 16:40:32 bangcrunch NetworkManager: <info>  Starting VPN service 'org.fre
edesktop.NetworkManager.pptp'... 
May  4 16:40:32 bangcrunch NetworkManager: <info>  VPN service 'org.freedesktop.
NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 14521 
May  4 16:40:32 bangcrunch NetworkManager: <info>  VPN service 'org.freedesktop.
NetworkManager.pptp' just appeared, activating connections 
May  4 16:40:32 bangcrunch NetworkManager: nm-vpn-connection.c.900: NeedSecrets 
failed: dbus-glib-error-quark Rejected send message, 1 matched rules; type="meth
od_call", sender=":1.14" (uid=0 pid=3551 comm="/usr/sbin/NetworkManager --pid-fi
le /var/run/Netwo") interface="org.freedesktop.NetworkManager.VPN.Plugin" member
="NeedSecrets" error name="(unset)" requested_reply=0 destination="org.freedeskt
op.NetworkManager.pptp" (uid=0 pid=14521 comm="/usr/lib/network-manager-pptp/nm-
pptp-service "))
May  4 16:40:32 bangcrunch NetworkManager: <WARN>  connection_state_changed(): R
ejected send message, 1 matched rules; type="method_call", sender=":1.14" (uid=0
 pid=3551 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo") interface="
org.freedesktop.NetworkManager.VPN.Plugin" member="Disconnect" error name="(unse
t)" requested_reply=0 destination="org.freedesktop.NetworkManager.pptp" (uid=0 p
id=14521 comm="/usr/lib/network-manager-pptp/nm-pptp-service ")) 
May  4 16:40:32 bangcrunch NetworkManager: <info>  Policy set 'Auto eth0' (eth0)
 as default for routing and DNS. 
May  4 16:40:45 bangcrunch NetworkManager: <debug> [1241469645.002626] ensure_ki
lled(): waiting for vpn service pid 14521 to exit 
May  4 16:40:45 bangcrunch NetworkManager: <debug> [1241469645.002738] ensure_ki
lled(): vpn service pid 14521 cleaned up 
```

---

### Post by philtrim on 2009-05-06
I was struggling with VPN for hours last nite.  I set everything 
up according to the forums...but kept getting NO SECRETS error.
SO, I thought, Let me do a complete restart, I did, retried the VPN connection, and BOOM, connected.  But, now I am having trouble brwosing, or even pingin anything on the remote side.

---

### Post by extraspecialbitter on 2009-05-06
I Googled the error message "NetworkManager.vpn fails -- nm-vpn-connection.c.900: NeedSecrets" and found [this post]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1469893.html"), whose simple workaround - making sure no root or sudo terminals were open - seemed to do the trick.  I had been tailing /var/log/syslog in an effort to troubleshoot - not realizing that I was actually contributing to the problem!  Granted, it seems that this is a bug, but I can live with the workaround for now.

---

### Post by dwiel on 2011-04-11
I was having this same problem in Lynx.  It started when I installed network-manager-openvpn.  To fix the problem I restarted the network manager and networking:

```
sudo /etc/init.d/network-manager restart
sudo /etc/init.d/networking restart
```

After this, connecting to an openvpn network worked

---

