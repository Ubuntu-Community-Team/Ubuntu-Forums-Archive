---
title: "pptpd to secure services on one server"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by leobard on 2009-05-30
ran around a curious problem today that should be doable with pptpd, but can't wrap my head around it...

I run a small group server on the web "friends.example.com" with a public IP. It will be used by me and some friends for samba shares and apache/http. I want to block access to these samba and apache ports and hide them from normal web users, only users connected to friends.example.com using pptp should be able to access samba and http(s). All pptpd, samba, and httpd run on one server. 

Installing pptpd and configuring it to give IP addresses to logged in users worked, but I found no documentation how to use pptpd to tunnel to local services. I would also like that logged-in users can keep accessing websites out of the vpn as normal, a.k.a the server should route, I did not immediately understand how to make it work.

I get the feeling I need to setup a virtual 192.168.0.* network inside this server, have people log into it via pptpd, configure samba and httpd only on to accept clients from that network, and enable routing from 192.168.0.* to the internet. Sadly, I don't know if this is the right idea or, if it is, what to do next to realize it.

Is there somewhere a tutorial showing how to use pptpd for my "one server" scenario to block access to an apache or samba on the same machine?

my installation worked like this, assuming the server has public IP address "friends.example.com":
```

apt-get install pptpd

vi /etc/pptpd.conf
localip 192.168.0.1
remoteip 192.168.0.100-200

vi /etc/ppp/chap-secrets
# client server secret IP addresses
vpn pptpd mypassword *

```

using ssh tunneling or openvpn is no fallback option for us. setting this up for the typical "windows noob" client is too much, pptpd and samba are both available native on windows and macos and ubunto, so my choice of tools seems right to me.

---

### Post by leobard on 2009-09-09
After weeks of fumbling around, I finally got it working, but it is not useful much.
**what really sucks hard, is that both SAMBA and PPTPD are too self-obsessed with passwords to support /etc/passwd authentification. I wanted one username/password combination for shell, vpn, and samba. This is impossible with /etc/passwd shell authentification and seems to be possible if you configure ldap for a week. Of course, for "security" it is not supported, but its the 80% case everyone wants to do in a small group environment.**

[SIZE="3"]Alias Network[/SIZE]

We create an alias network 192.168.1.2 only visible inside the server.

pico /etc/network/interfaces

add this:
```
# private network for PPTP
auto eth0:0
iface eth0:0 inet static
  name Ethernet alias for samba
  address 192.168.1.2
  netmask 255.255.255.0
  network 192.168.1.0
  # no gateway!
```

# restart the network
/etc/init.d/networking restart 

[SIZE="3"]PPTPD[/SIZE]
get it:

apt-get install pptpd

edit the options:

vi /etc/ppp/pptpd-options
	#set the name....I did not do more

vi /etc/pptpd.conf

```
# commented the following because of http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/797000738931, 
# Plugin /usr/lib/pptpd/pptpd-logwtmp.so is for pppd version 2.4.4, this is 2.4.5 
#logwtmp

localip 192.168.1.199
remoteip 192.168.1.200-250

```

setup the passwords, I use some made-up password in plaintext
vi /etc/ppp/chap-secrets
```
# client server secret IP addresses
vpn pptpd mySecretPassword *
```

[SIZE="3"]Samba[/SIZE]
according to [http://samba.org/~tpot/articles/multiple-interfaces.html](http://samba.org/~tpot/articles/multiple-interfaces.html) (see there how to check if you did it right!)

apt-get install samba
vi /etc/samba/smb.conf

```
# we bind only to the alias network and to loopback. Loopback is needed for smbpasswd commandline to work!
interfaces = eth0:0 lo
bind interfaces only = yes

```

For all users, create smb-passwords as root:
# initialize it to a password, here is null
smbpasswd -a myuser -n

[SIZE="3"]Client-side setup[/SIZE]
get a smbpassword! see above for smbpasswd.
Must know PPTPD password!

then use the public IP address of the server to connect:
VPN: public.example.com
user: vpn 
pwd: mySecretPassword

Once inside VPN, connect to the eth0:0 IP of the samba server, in my case: 192.168.1.2

In windows: \\192.168.1.2\myuser should get you to your home directory.

In the VPN/Network/TCP/IP/enhanced, remove the check "standardgateway für das remotenetzwerk verwenden".

... and then do the usual setup of Samba.

hth

---

### Post by deltateam2 on 2009-10-26
Use OpenVPN.

---

