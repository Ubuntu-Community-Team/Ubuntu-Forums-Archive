---
title: "How to configure VPN?"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by karumudi7 on 2009-12-14
Hi I want to configure VPN to connect to my office.
Can any one tell me how to configure... I Have VPNC,Open VPN,PPTP clients.
I have the data of Host IP,Pair of Username & passwords thats all I have.

I tried it when I rightclick n/w applet, I can see my VPN connection but unable to connect(It is not getting selected).
Plz help me in configuring!!!

---

### Post by dgoosens on 2009-12-14
Hi,

You need to figure out what kind of connection your office accepts...
As you have a host, username and password, it is highly probable that it is a regular PPTP-vpn connection.

In that case, you need to make sure you have that installed on your computer...
```

sudo apt-get install network-manager-pptp

```

EDIT: just noticed you are on Kubuntu... In that case you also need to install the gnome network manager:
```

sudo apt-get install network-manager-gnome

```

After that, left-click on the network-manager applet > VPN Connections > Configure VPN

There you can click on "Add", select the PPTP VPN and enter host, username and password.

Finally, you will have to go into the advanced settings and configure it... I believe you have to deactivate CHAP.

On my side, I also configured the routes so that only the VPN is only used for my office's IPs.

I just googled it, this looks good as a reference:
[ http://tipotheday.com/2008/04/29/connect-to-windows-vpn-server-pptp-with-ubuntu-hardy-heron/]( http://tipotheday.com/2008/04/29/connect-to-windows-vpn-server-pptp-with-ubuntu-hardy-heron/)

Hope it helps !

---

### Post by karumudi7 on 2009-12-14
Unable to connect.
I configured the data usig PPTP cloent. On the rightclick of Knetwork manager I can find my VPN connection name, but it is not able to select i.e; If I click on that VPN connection it is in a stable state only it is not asking any credentials or nothing!

---

### Post by fuzzmo on 2010-03-13
I have exactly the same problem.  Have installed the various bits as detailed above and configured my VPN and yet when I click on it within the network manager nothing happens?...

Any ideas?  I managed to get it working in Ubuntu on another machine but not thus far on Kubuntu...

---

### Post by fazie on 2010-03-14
There is known bug, you have to restart your machine ;) and everything should work perfectly.

I've got another problem with Network Manager and VPN connection. When I connect to my work, nm overwrites my dns to 127.0.0.1.
How tell nm to don't touch my dns entries ?

---

### Post by Kostik8 on 2010-03-23
I have the same problem. Cannot activate the vpn connection. Reboot doesn't help. Are there any other workarounds for that ?

---

### Post by jrssystemsnet on 2010-03-23
You need to find out for sure what kind of VPN you are trying to connect to.  The PPTP client isn't going to connect to an IPSEC VPN, and vice versa.

---

### Post by Kostik8 on 2010-03-23
The problem is it just do nothing! I click on VPN connection and it does nothing. Even nothing in log.
VPN is PPTP, Ubuntu 9.10, pptp-linux is installed.

---

