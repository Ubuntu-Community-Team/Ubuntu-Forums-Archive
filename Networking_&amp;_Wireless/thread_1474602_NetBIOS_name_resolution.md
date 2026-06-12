---
title: "NetBIOS name resolution"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by benjsec on 2010-05-06
Hi all,

I'm having some trouble addressing computers by name. I've just upgraded most my my box's to Lucid, and it was all working fine, but suddenly stopped - not quite sure why, or what I did, but I need it to come back!
At first I thought it was my old router dying (which it was) but a new router hasn't helped.

I've now moved DHCP from the router to my server, and that's working fine, giving out static IPs from MAC addresses, and so forth, but I still can't address anything by name.
My server is on 192.168.100.1 and called myth-server, if I ```
ping myth-server
``` I get the response
```
ping: unknown host myth-server
```
pinging 192.168.100.1 works fine.
I've tried installing samba on the server (samba-common, samba-client, samba, samba4, and probably some others) but that doesn't seem to help, and I'd rather not have to, as I don't have any windows PCs on the network.
The same also applies between any other PCs on the network and is getting very annoying now! I've also tried nsblookup and get the following 
```
ben@ben-laptop:~\ nmblookup ben-desktop
querying ben-desktop on 192.168.100.255
name_query failed to find name ben-desktop
```
I don't know why it's going for .255, there's nothing there, my router's .254 and the server's .1

In case it helps here's my dchpd.conf

```

default-lease-time 600;
max-lease-time 7200;

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.100.1;
option routers 192.168.100.1;
option domain-name-servers 212.139.132.24, 212.139.132.25, 208.67.222.222, 208.67.220.220;
#option domain-name "local";
option netbios-name-servers 192.168.100.1;
option netbios-node-type 8;

host ben-desktop {
hardware ethernet <MAC ADDR>;
fixed-address 192.168.100.2;
}

host myth-server {
hardware ethernet <MAC ADDR>;
fixed-address 192.168.100.1;
}

subnet 192.168.100.0 netmask 255.255.255.0 {
range 192.168.100.10 192.168.100.30;
}

```

Many Thanks for looking,

Ben

---

### Post by i.r.id10t on 2010-05-06
If you are giving out addresses based on MAC address then you could just set up DNS for your internal lan...

---

### Post by myk.dinis on 2010-05-06
Here -> "querying ben-desktop on 192.168.100.255" it's doing a broadcast to try and get a response.
(Ubu)
sudo gedit /etc/hosts
Below the ipv4 address for the machine you're on add 
192.168.100.1<hit TAB>myth-server
(Win)
winkey+r
notepad %systemroot%\system32\drivers\etc\hosts
Below the 127.0.0.1 add
192.168.100.1<hit TAB>myth-server

Don't forget, with all OSs going IPv6, they prefer IPv6 when querying the network, but if your SOHO router doesn't support it, it'll timeout and stuff...

Hope this helps!

CHeers!
-myk

---

