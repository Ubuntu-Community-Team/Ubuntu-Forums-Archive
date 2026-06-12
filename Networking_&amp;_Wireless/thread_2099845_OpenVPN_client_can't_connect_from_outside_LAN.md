---
title: "OpenVPN client can't connect from outside LAN"
date: 2012-12-30
forum: Networking &amp; Wireless
---

### Post by Madi1986 on 2012-12-30
Hi everyone,

Let me start out by saying that I'm new to ubuntu server (12.10), and I am trying to use it as a VPN server.

I have followed loads of docs, and what I have accomplished is that I can connect with tunnelblick (vpn client for mac osx) to the server ONLY if I am on the LAN. With this connection I am getting the ip I want  it to get (192.168.1.128 -- the first in the list in the server-bridge config), and there is also a connection to the WWW.

My problem is that the client and server fails to make a TLS handshake when outside the LAN (if I am in a coffee shop, for instance)

my server on the lan is 192.168.1.54, externally it is 80.x.x.197. Besides that, I am using default port 1194.

I am currently using a ZyXEL NGB5715 router, and have forwarded port 1194 to 192.168.1.54

My /etc/network/interfaces file is as follows:

> 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
I am not using a static ip for my server, is this a problem?

My server.conf file for openvpn is: 

> 
local 192.168.1.54
port 1194
proto udp

dev tap0

ca ca.crt
cert server.crt
key server.key
dh dh1024.pem

ifconfig-pool-persist ipp.txt
server-bridge 192.168.1.54 255.255.255.0 192.168.1.128 192.168.1.254
server-bridge

push "route 192.168.1.1 255.255.255.0"
push "dhcp-option DNS 80.x.x.2"

client-to-client

keepalive 10 120
tls-auth ta.key 0

comp-lzo
user nobody
group nogroup

persist-key
persist-tun

status openvpn-status.log
verb 3
what should my server ip be? the one I have declared or the one that has 80.x.x.197?

This is driving me nuts.

My iptables are as follows:

> 
sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere             udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:domain
ACCEPT     udp  --  anywhere             anywhere             udp dpt:bootps
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:bootps

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             192.168.122.0/24     state RELATED,ESTABLISHED
ACCEPT     all  --  192.168.122.0/24     anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

If there is some info I have missed to post, please let me know, and I will gladly update my thread.

Thanks a lot in advance for  reading and for any help you might be able to provide.

Much appreciated.

---

### Post by ahallubuntu on 2012-12-30
If you can connect internally on your LAN with a local IP address, it's almost certainly a port forwarding problem.  I assume when you are at the coffee shop you have changed the OpenVPN config to go to a gateway of 80.x.x.197 instead of to 192.168.1.54?

What is your exact network setup?

You have DSL or a cable modem with an IP of  80.x.x.197?  The  ZyXEL NGB5715 is just a wireless router isn't it?  Or is it also the DSL or cable modem?  If you have a separate DSL or cable modem (with its own firewall), you have to forward 1194 through that firewall, too.

Make sure your are forwarding both UDP and TCP through the firewall (in case your OpenVPN is setup to do one and you are forwarding the other and not both).

Not having a static IP is only important if it changes, of course.  If you are testing and the IP doesn't change while you are testing, then that isn't the cause of this particular problem but could cause problems later.  If 80.x.x.197 isn't static, consider using a Dynamic DNS service with that so you can use a domain that tracks the IP instead of using the (changing) IP.

You should also fix 192.168.1.54 in your ZyXEL (make a DHCP reservation) so your server always gets the same IP, so you aren't surprised later if it changes.

---

### Post by Madi1986 on 2012-12-31
@ahallubuntu:

thanks for your reply :)

> 
I assume when you are at  the coffee shop you have changed the OpenVPN config to go to a gateway  of 80.x.x.197 instead of to 192.168.1.54?
No. Actually my configurations on both server and client for openvpn remains on 192.168.1.54, even when I am at the coffee shop.

> 
What is your exact network setup?
I have a DSL connection with a dynamic IP of 80.x.x.197, which connects to the ZyXEL NGB5715 router. The router has both the server and the client computer (among other pc's too) connected to it, and they get their respective LAN IP's.
I have also disabled the router's firewall.

> 
You should also fix 192.168.1.54 in your ZyXEL (make a DHCP reservation)  so your server always gets the same IP, so you aren't surprised later  if it changes.     
I have done this on the router's configuration by reserving the ip 192.168.1.54 to the server's mac address. I assume in doing so, I don't need a DynDNS service as you suggested?

What is weird, is that I get the connection on the LAN (I am actually writing this now while connected to the server through vpn) so I am pretty sure that the port 1194 is forwarded correctly.

I am wondering though, how my client (a macbook) can know which server to connect to when trying to connect to 192.168.1.54 - it might as well be an IP used in the coffee shop's LAN.

Many thanks in advance.

EDIT: I forgot to say, as you can see in the configs for the server and client, I am on a bridged connection which is started by the following script:

> 
#!/bin/bash

#################################
# Set up Ethernet bridge on Linux
# Requires: bridge-utils
#################################

# Define Bridge Interface
br="br0"

# Define list of TAP interfaces to be bridged,
# for example tap="tap0 tap1 tap2".
tap="tap0"

# Define physical ethernet interface to be bridged
# with TAP interface(s) above.
eth="eth0"
eth_ip="192.168.1.54"
eth_netmask="255.255.255.0"
eth_broadcast="192.168.1.255"

for t in $tap; do
    openvpn --mktun --dev $t
done

brctl addbr $br
brctl addif $br $eth

for t in $tap; do
    brctl addif $br $t
done

for t in $tap; do
    ifconfig $t 0.0.0.0 promisc up
done

ifconfig $eth 0.0.0.0 promisc up

ifconfig $br $eth_ip netmask $eth_netmask broadcast $eth_broadcast

route add default gw 192.168.1.1


---

### Post by ahallubuntu on 2012-12-31
192.168.1.54 is an IP on your local network.  You can't get to it directly from the coffee shop.  You have to use 80.x.x.197 (or whatever your dynamic IP has changed to by now).  Millions of computers around the world have the IP "192.168.1.54" because that IP (or 192.168.X.X) is reserved for local networks.

So, when you go to the coffee shop, you have to change your OpenVPN gateway to 80.x.x.197 .  (Let's call that "DSL IP" since it will change.  As suggested previously, use a dynamic DNS so you won't worry about it changing.)  You can also just make a duplicate OpenVPN client configuration - one for internal testing, one for "real" using your DSL IP.  Leave the server set to 192.168.1.54 (leave the server config exactly the same whether local or accessing it from the coffee shop).  You'll access that THROUGH THE FIREWALL from your DSL IP.

You may have disabled another firewall, but if you are using 192.168.1.54, by definition your NAT firewall is still on.  (Which is what you want - do not try to turn that off.)  Google for "Network Address Translation" (NAT) to learn more about how a NAT firewall works.

Port forwarding only means anything when you are trying to get through your NAT firewall.  So if you are on your local network, you don't have to forward port 1194 - it isn't blocked by a firewall.  When you are at the coffee shop, you, you have to access port 1194 of your VPN server (192.168.1.54) through your home NAT firewall, by using your DSL IP.

You didn't say whether the ZyXEL is the only switch/router on your network or whether there is a DSL modem ahead of it?  Is the phone line plugged directly int your ZyXEL?  Or is there a DSL modem with a phone line connected and that is connected to the ZyXEL?  As  I said, you must also make sure there isn't a second firewall in your DSL modem that also requires you to forward a port. If so, you have to forward port 1194 through the DSL modem's firewall too, to the ZyXEL.

You might get the dynamic DNS setup first, because for real use you're going to need that anyway.  You can probably run a dynamic DNS updater on the same Linux server that is running OpenVPN, assuming it is on all the time (to update the domain).  A couple of the formerly free services I used to use are no longer free - do some research to find out what your options are and how to set it up on your server.

But if you wish just to test it now with your DSL IP, you have to be careful it hasn't changed by the time you get to the coffee shop (or how you will you know what it has changed to?).  If you're lucky and it hasn't changed by then, as noted above change your OpenVPN client config gateway to the DSL IP and try it again at the coffee shop.

---

### Post by Madi1986 on 2013-01-01
@ahallubuntu:

Loads of thanks for your detailed answers!! Very much appreciated :)

> So, when you go to the coffee shop, you have to change your OpenVPN  gateway to 80.x.x.197 .  (Let's call that "DSL IP" since it will change.   As suggested previously, use a dynamic DNS so you won't worry about it  changing.)  You can also just make a duplicate OpenVPN client  configuration - one for internal testing, one for "real" using your DSL  IP.  Leave the server set to 192.168.1.54 (leave the server config  exactly the same whether local or accessing it from the coffee shop).   You'll access that THROUGH THE FIREWALL from your DSL IP.Nice to know. So in my client.conf I should just use > remote 80.x.x.197 1194 when outside my LAN. I have tested this by using a 3mobile dongle (mobile broadband), but I can't ping 80.x.x.197 and therefore no TLS handshake. Is this where DDNS would be good for me, or should I contact my ISP? I get the following when trying to ping:

> 
PING 80.x.x.197 (80.x.x.197): 56 data bytes
Request timeout for icmp_seq 0
Request timeout for icmp_seq 1
Request timeout for icmp_seq 2
...
...
> You didn't say whether the ZyXEL is the only switch/router on your  network or whether there is a DSL modem ahead of it?  Is the phone line  plugged directly int your ZyXEL?  Or is there a DSL modem with a phone  line connected and that is connected to the ZyXEL?  As  I said, you must  also make sure there isn't a second firewall in your DSL modem that  also requires you to forward a port. If so, you have to forward port  1194 through the DSL modem's firewall too, to the ZyXEL.
It is the only router I have at home, which means that I get a connection from the wall (ISP) directly to the ZyXEL router, and is distributed to the rest of the PCs I've got at home, including my ubuntu 12.10 server.

> 
But if you wish just to test it now with your DSL IP, you have to be  careful it hasn't changed by the time you get to the coffee shop (or how  you will you know what it has changed to?).  If you're lucky and it  hasn't changed by then, as noted above change your OpenVPN client config  gateway to the DSL IP and try it again at the coffee shop.     
As stated above, I got a hold of a mobile broadband solution so I could try doing it while I was near the server, and the WAN IP stayed the same; not possible to connect :(

I forgot to post my client configuration for openvpn, which you might want to have a look at. I have fixed it with your suggestion:

> 
client
dev tap0
proto udp

remote 80.x.x.197 1194

resolv-retry infinite

nobind

user nobody
group nobody

persist-key
persist-tun

ca ca.crt
cert vpntest.crt
key vpntest.key

ns-cert-type server

tls-auth ta.key 1

comp-lzo
verb 3

push "dhcp-option DNS 80.x.x.2"
Again, many thanks in advance for your clear explanations and suggestions.

---

### Post by ahallubuntu on 2013-01-01
The Dynamic DNS helps only to resolve the IP (which could change).  It will help you later when your IP changes and the DNS name record changes to point to the new IP. It's not going to make your VPN work if the IP you have doesn't work.

The WAN on a router does not always respond to pings.  So you can't be sure you are really seeing your IP or not when connected to mobile broadband.  Login to the ZyXEL again and look for options regarding responding to pings on the WAN.  (Not every router has this option.)

As another complication, your mobile broadband may not allow you to connect to a VPN!  (Mine does, but some providers may block it.)  It's also possible your ISP is blocking 1194 as well - you can ask them (I doubt it).

I guess I'd double check the port forwarding of 1194 in your ZyXEL again.  You can confirm that that port is open using a tool like this (which will also show your current DSL IP):

[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)


and plug in 1194.  (You can run that at home from inside your LAN.)

---

### Post by Madi1986 on 2013-01-01
@ahallubuntu:

> The Dynamic DNS helps only to resolve the IP (which could change).  It  will help you later when your IP changes and the DNS name record changes  to point to the new IP. It's not going to make your VPN work if the IP  you have doesn't work.

Great! Then that is ruled out.

> The WAN on a router does not always respond to pings.  So you can't be  sure you are really seeing your IP or not when connected to mobile  broadband.  Login to the ZyXEL again and look for options regarding  responding to pings on the WAN.  (Not every router has this option.)

Ok. I went into my ZyXEL admin -> Advanced -> Configuration -> Security -> Firewall
I have disabled Firewall Setup in the General-tab, and in the Services-tab I changed the ICMP to respond to ping on LAN&WAN (before it was only LAN).
Unfortunately, still same problem :(

> As another complication, your mobile broadband may not allow you to  connect to a VPN!  (Mine does, but some providers may block it.)  It's  also possible your ISP is blocking 1194 as well - you can ask them (I  doubt it).

I checked on their website, and luckily the port is not blocked :) I definitely will give my ISP a call tomorrow, because I am almost sure that the problem is at their side.

> 
I guess I'd double check the port forwarding of 1194 in your ZyXEL  again.  You can confirm that that port is open using a tool like this  (which will also show your current DSL IP):

[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/)


and plug in 1194.  (You can run that at home from inside your LAN.) 	

I did that, and ALL ports are blocked!! FTP, SSH, HTTP, 1194 etc. Therefore, I seriously think that my ISP has closed for all ports from the WAN - but I find this very weird.

I will give them a call tomorrow, and will get back with the outcome. If you have further suggestions in the meantime, you are welcome to come with your helpful input.

Thanks a lot.

---

### Post by ahallubuntu on 2013-01-01
> **Madi1986 said:**
> I did that, and ALL ports are blocked!! FTP, SSH, HTTP, 1194 etc. Therefore, I seriously think that my ISP has closed for all ports from the WAN - but I find this very weird.


Not weird.  Most people would have ALL ports blocked on their NAT firewall - unless they have opened one and forwarded it as you are trying to do.  If you forwarded only 1194, that's the ONLY port that should be open.  A NAT firewall blocks only INCOMING ports.  Outgoing port 80 for example (what most of use use to browse the web) isn't blocked at all unless by some other firewall.

I'd go back into the ZyXEL setup one more time and double check the setup.  What's the exact model number?

---

### Post by Madi1986 on 2013-01-02
Hmm. Interesting. I have a ZyXEL NBG5715, updated to the newest firmware - V1.00(AAAG.4).

Below is my NAT setup:

[IMG]http://ocmanagement.dk/screenshot.png[/IMG]

For me, this looks as if the ports are forwarded only for the LAN but not for the WAN.. but I can't change the Default Server to an IP outside the LAN.

Thanks again ;)

NB: Was at work and didn't have time to give my ISP a call. Hopefully tomorrow.

---

### Post by ahallubuntu on 2013-01-02
You can't forward one port to two different IP addresses at the same time.  Only one IP address at a time.  And you are forwarding 1194 to your Macbook (is it running a VPN server?) and to 192.168.1.54.  Get rid of the Macbook forwarding.

Normally it would be invalid to set forwarding of a port to two different IPs.  That's why your screenshot looked confusing to me, because it shows you forwarding 1194 to two different IPs.  I glanced at the manual for your ZyXEL, and apparently they use something called "Port Triggering" (look in the "NAT Advance" tab) to let your local devices decide (by triggering another port) which one gets forwarded the port, if two different IPs want to share it (they can't use it at the same time; they have to take turns).  If you have NO triggering rules set, then probably neither will get forwarded the port.

Anyway - I'm guessing you don't have a VPN running on your Macbook.  So just delete that rule and leave the single 1194 forward for 1.54.  Delete any triggering rules - you should not need any if you are only setting port forwarding to one port.

(Ditto for that ssh forward - get rid of one of the forwards, you probably want 1.54 again for that.)

Once you have done this, check again using the website I gave you above to see if ports 1194 (and 22) are now open.

FYI, a different way to get around the "same port to two IPs" problem is simply to use different ports.  If you wanted to run two VPN servers, you could just assign them different ports on the router (say 1195 for the second one).  Then either tell the second server to listen on port 1195 (instead of 1194) in the server config...or use a router that will forward to a different port.  The latter approach is what I use, because I use DD-WRT firmware on my routers.  But, you probably have only one VPN server anyway, right?  So not an issue for you.  Too bad you can't use DD-WRT on your ZyXEL, don't think it is supported.

---

### Post by Madi1986 on 2013-01-03
This is seriously doing my head in!! :( I just don't get it.

I disabled the macbook forwarded ports as you suggested, and ran the open port check tool again; ports 1194 and 22 are still closed.

I also took the time to contact my ISP - they say its my router. What have I done wrong? I am starting to think that maybe the ports need to be opened through my ubuntu server, but again, if they weren't, I wouldn't be able to connect through the port on the LAN.

---

### Post by ahallubuntu on 2013-01-03
Right, the OpenVPN port is already open on the Ubuntu box if you can connect to it internally.  I believe installing the OpenVPN server on it automatically opens that port, anyway.

You're just going to have to play with the port forwarding in the NAT til you get it figured out.  Again, make sure you don't have any triggering rules.  Try deleting ALL the port forwarding rules and starting over.  Are you sure disabling the firewall doesn't actually BLOCK everything?  Maybe it's also a matter of dealing with the router manufacturer to help figure out the settings.

You might even do a factory reset of the router (but of course, be careful to note down the important settings to set it back up again properly).

Usually, port forwarding in a consumer router is rather easy.  Then again, yours is the first I've seen that has that "port triggering" feature.

If you happen to have a spare router, you could turn the ZyXEL into a bridge so it just does the DSL modem function and passes on the IP to the WAN of another router that you know how to configure.  But that would be a shame to have to go to that extreme.  I'm sure you can get the ZyXEL figured out one way or another!

---

### Post by gschoppe on 2013-01-03
just to check.. earlier the replies talked about changing the ip to 80.x.x.197

this was a placeholder for the public ip address of your router.

did you properly fill in the actual public address, rather than the version with x.x in it?

---

### Post by Madi1986 on 2013-01-05
@ahallubuntu:

I finally figured it out! The ISP-worker I talked to recently seemed to not be knowing their systems well. I called them today, and apparently they close ALL incoming ports from the WAN. The solution to this is a static ip-address :) So I am just waiting for them to set it up, and will get back at you with the outcome.

Thanks for your help so far :)

@gschoppe:

Of course ;)

---

### Post by Madi1986 on 2013-01-20
@ahallubuntu:

It works now! Perfect! It was simply just a static IP I needed from my ISP, forwarding ports and voila! I can now get a client to connect to the VPN server.

But now I'm having an issue. I have connected through the VPN, but now I  can't access the VPN server through SSH, and can't get access to the  router's gateway. What is funny, is that I briefly see the router-login  at 192.168.1.1 but it doesnt fully load the page, and afterwards times  out.

Let me know which kind of information I need to post. I think it has to do with my interfaces config. I could be wrong.

Thanks in advance.

[B]EDIT::: It's now fixed. I knew it was a configuration issue. It just wasn't in the interfaces, but in my openvpn server config file. I changed the following:

```

;local 192.168.1.54
mode server

```and

```

;push "route 192.168.1.1 255.255.255.0"
push "route 192.168.1.0 255.255.255.0"

```And that solved my issue![/B]

---

