---
title: "How to setup DNSCrypt &amp; Dnsmasq?"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by Marcelo Ruiz on 2012-02-17
Hi there!
I am wondering if any of you know how to setup dnscrypt and dnsmasq to work together.
I guess the idea will be to tell dnsmasq to use dnscrypt in order to have the cache working, but I am having a hard time configuring and being sure everything works as it should. 
I followed the instruccions posted here:

[http://www.webupd8.org/2012/02/encrypt-dns-traffic-in-linux-with.html]("http://www.webupd8.org/2012/02/encrypt-dns-traffic-in-linux-with.html")

Thanks!

---

### Post by Marcelo Ruiz on 2012-02-19
Well, I might I'm the only one who wants to have both services working together :P

---

### Post by foobar66 on 2012-05-05
I am trying the same thing on Ubuntu 12.04 ... no luck so far, even when starting dnscrypt on 127.0.0.2 and then using 127.0.0.1 as resolved. I am getting:

> nslookup [www.google.com]("http://www.google.com") 127.0.0.2

[INFO] Generating a new key pair
[INFO] Done
[INFO] Server certificate #1323392947 received
[INFO] This certificate looks valid
[INFO] Server key fingerprint is E07C:5F90:03C2:D764:A9FC:9A1E:6633:632A:0FE0:B1C5:5EF9:894A:FC7A:BA18:4A62:462E
[INFO] dnscrypt-proxy is ready: proxying from [127.0.0.2] to [127.0.0.1]
[WARNING] Received a suscpicious reply from the resolver
[WARNING] Received a suscpicious reply from the resolver
[WARNING] Received a suscpicious reply from the resolver

---

### Post by foobar66 on 2012-05-05
OK ... well, I found at least how to use dnscrypt-proxy.

First, disable dnsmasq ...

> sudo gedit /etc/NetworkManager/NetworkManager.conf

and comment out the line which says:

dns=dnsmasq

so change it to:

#dns=dnsmasq

Now go to NetworkManager > Edit Connections, click your connection then "Edit" and click on "IP4 settings" tab. Select "Automatic (DHCP) addresses only". In the same dialog, set your DNS server to 127.0.0.2

Then:

> sudo restart network-manager

Now start your dnscrypt-proxy:

> sudo dnscrypt-proxy -a 127.0.0.2 -t 53

And you are good to go.

So to make the latter permanent, make sure the dnscrypt.conf script in /etc/init looks as follows:

```

description "dnscrypt startup script"

start on (local-filesystems and started dbus and stopped udevtrigger)
stop on runlevel [016]

script
        exec /usr/sbin/dnscrypt-proxy -a 127.0.0.2 -t 53
end script

```

After a reboot dnscrypt should work fine.

I tried it also together with dnsmasq but for some reason it is horrendously slow !

I don't care so much about dnsmasq so the above will work without it.

Tested on Ubuntu 12.04.

---

### Post by camurgo on 2012-07-18
*¹*

---

