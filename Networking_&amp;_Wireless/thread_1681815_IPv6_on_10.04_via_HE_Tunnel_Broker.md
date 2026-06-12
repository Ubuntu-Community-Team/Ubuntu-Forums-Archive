---
title: "IPv6 on 10.04 via HE Tunnel Broker"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by trmentry on 2011-02-04
Thought I would make a post in the hopes others will find it useful. :)

I finally got around to messing with Hurricane Electric's IPv6 [Tunnel Broker]("http://www.tunnelbroker.com") service. 

This is how I got things running on my 10.04 Server with a pfSense FW.   

1/ After you request your tunnel from HE time to get things setup.

2/ I added the following to my /etc/network/interfaces file.

```


auto he-ipv6
iface he-ipv6 inet6 v4tunnel
        endpoint xx.xx.xx.xx # HE IPv4 Server IP
        address <Client IPv6 Addy from HE>
        netmask 64
        ttl 64
        up ip -6 route add default dev he-ipv6
        down ip -6 route del default dev he-ipv6


```

3/ Change /etc/sysctl.conf to allow IPv6.  Change the following 2 lines to =1 or add them if needed.
I had 1 but not the other in my file.
```


net.ipv6.conf.all.forwarding=1

net.ipv6.conf.default.forwarding=1

```

Then get the changes to take effect.

```

sysctl -p

```


Once that was done, I had to allow Protocol 41 in via my pfSense firewall.  This was fairly easy to do in the System --> Advanced 
Scroll down to the IPv6 section and tick both boxes.  Enter the IP address of you host in your lan where the tunnel is terminating.  

5/ Test to make sure things are working.  You should be able to ping IPv6 hosts at this point from your server.

```


root@hoth:~# ping6 -c5 ipv6.google.com
PING ipv6.google.com(lax04s01-in-x68.1e100.net) 56 data bytes
64 bytes from lax04s01-in-x68.1e100.net: icmp_seq=1 ttl=59 time=46.3 ms
64 bytes from lax04s01-in-x68.1e100.net: icmp_seq=2 ttl=59 time=45.6 ms
64 bytes from lax04s01-in-x68.1e100.net: icmp_seq=3 ttl=59 time=45.6 ms
64 bytes from lax04s01-in-x68.1e100.net: icmp_seq=4 ttl=59 time=44.8 ms
64 bytes from lax04s01-in-x68.1e100.net: icmp_seq=5 ttl=59 time=46.1 ms

--- ipv6.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 44.883/45.742/46.333/0.517 ms

```


Now for the fun part on getting my machines on the LAN to work as well.  This was a bit harder for me.  I tried like mad to get radvd to work, but in the end I couldn't get it working right on handing out IPv6 addresses.  It would had them out, but my LAN hosts didn't know the gateway to use properly.  

I ended up using my Windows 2008 server and set up DHCPv6 on there.  That worked out better.  I just config'ed ::4 on my network interface in Windows for the IPv6 protocol with the ::3 of eth0 on Linux host as the GW.    I told Windows 2008 to exclude ::1 - ::10 from the scope/pool.

I had to give my eth0 on linux server an IPv6 address as well so that it would act like the gateway.

So back to the /etc/network/interfaces file.  I added the following.

```


auto eth0

<SNIP IPv4 info>

iface eth0 inet6 static
address <HE IPv6 /64 block::3>  #  I just took the next address
netmask 64

```

Restarted networking.

```

/etc/init.d/networking restart

```

Once that was done, my lan hosts got an IPv6 address and are able to get to IPv6 hosts now on the internet.

[http://ipv6.google.com](http://ipv6.google.com)
[http://www.v6.facebook.com](http://www.v6.facebook.com)



Hope this helps people out.

[SIZE="2"]
Sources:
[https://erikbandersen.com/wordpress/?p=28](https://erikbandersen.com/wordpress/?p=28)

[http://www.itechtalk.com/thread1818.html](http://www.itechtalk.com/thread1818.html)

[http://www.itechtalk.com/thread1819.html](http://www.itechtalk.com/thread1819.html)
[/SIZE]

---

