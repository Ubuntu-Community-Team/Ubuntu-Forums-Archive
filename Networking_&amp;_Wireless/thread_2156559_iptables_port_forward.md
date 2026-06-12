---
title: "iptables port forward"
date: 2013-06-22
forum: Networking &amp; Wireless
---

### Post by bangobng on 2013-06-22
hey guys i have ubuntu server with PPTP VPN server installed on it. 
I have no idea how IPtables works so,

my problem is i want make a port forward between Server public ip and one of VPN users with localip :192.168.0.234 on port 1604

thanks in advance

---

### Post by Lars Noodén on 2013-06-22
Just as long as you know that PPTP is not any help with security, it is so insecure that it should be considered unencrypted.

[http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html](http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html)

You can use it, just be aware that it does not do what many people think it does.

---

### Post by Lars Noodén on 2013-06-22
About the forwarding, it is quite easy to set up, though I personally feel that iptables can be a little bit of work to deal with.

But first you have to turn on ip forwarding:

```

sudo sysctl net.ipv4.ip_forward=1

```

To make it permanent, you would have to edit /etc/sysctl.conf.  Otherwise, that setting will be cleared on next reboot.

Then the forwarding is easy.  I guess you want port 1604 on the outside facing machine to be forwarded to port 1604 on 192.168.0.234:

```

sudo iptables -t nat -A PREROUTING -p tcp --dport 1604 -j DNAT --to 192.168.0.234:1604
sudo iptables -t nat -A POSTROUTING -j MASQUERADE

```

Note that this setup works when checked from another machine, it does not work when tested from the same machine that the forwarding is occuring on.  

You can display your handiwork with [iptables save](http://manpages.ubuntu.com/manpages/raring/en/man8/iptables-save.8.html)  And if you regret it or made a mistake you can delete the changes:

```

iptables -t nat -D POSTROUTING 1; iptables -t nat -D PREROUTING 1

```

I'm not sure, though, of the official way of making the forwarding permanent.  There are many ways to do it, but I don't know the official one.

---

### Post by bangobng on 2013-06-22
Thanks ,

The main reason was make port forward because my ISP does not allow port forward so I don't care about security of the Vpn

Last think if i want to forward UDP port will it be the same command with replace TCP ?

---

### Post by Lars Noodén on 2013-06-22
Forwarding UDP should be similar, just change the appropriate  -p or --protocol from tcp to udp. 

The best way is to try experiments yourself.  One of the first things to try though is to restore iptables back to its whatever defaults you prefer.

Keep checking the manual page for iptables from time to time and it will slowly (or quickly) become less mysterious.

---

