---
title: "VPN Server Setup on Kubuntu"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by borivoje on 2012-11-18
This has been bugging me for a certain time.
I am trying to set up a VPN server at my home network.
This is what I read
[http://cviorel.easyblog.ro/2009/02/09/how-to-set-up-a-vpn-server-on-ubuntu/](http://cviorel.easyblog.ro/2009/02/09/how-to-set-up-a-vpn-server-on-ubuntu/)
What I don't get here is what routes I need to add to the server machine.
My network is as follows:

I connect to the Internet via Cable modem which has address 188.x.x.x
The cable modem is plugged into the Wireless Router, which gives adresses to all machines in my network. The server has address 192.168.1.3. I am trying to connect to VPN which I (somehow) set up according to the given source from the outside network (namely, my Wireless 3G Modem which is ppp0).

I also tried setups with OpenVPN, but I had no luck, reading the Community Ubuntu Documentation instructions. I thick that the above was a easier solution, if it only worked.

Thanks in advance for your help, it would be muuch appreciated!

---

### Post by ahallubuntu on 2012-11-18
There are a few steps here.  The first step (following those instructions you linked to) is setting up the VPN server.  The second step is setting up your VPN client (the laptop you'll use from outside to get in).  But to access the server from outside, you must also forward a port through your router (or through the modem if it has a router too) to the server.  The default VPN port is 1194.

I haven't setup a PPTP server and not any VPN with Kubuntu.  I've setup OpenVPN servers with Ubuntu and also on the router itself (DD-WRT firmware or Tomato).  So I can't help you with the specific steps of setting up your server.  However, there should be a server logfile you can monitor to help debug things.  FYI, PPTP is not known to be completely secure.  OpenVPN allows a higher level of security.

As far as the port forwarding goes: it's important to understand whether your modem has a router in it or not.  Your external IP is 188.xxx.xxx.xxx .  Is this also the IP your router gets on its WAN when you connect it?  You should be able to find this out in the router's connection status (login to [http://192.168.1.1](http://192.168.1.1) while connected to the wireless or to a LAN port).  If it gets that same 188.xxx.xxx.xxx as its IP, then the modem isn't running a router too; but if you get something else like 10.xxx.xxx.xxx then the modem has its own router and firewall (very common these days).  In that case, you'll have to forward 1194 through both firewalls - the modem's router's firewall and then the router's firewall to your server.

Also, does your cable company give you a static IP?  Does that 188.xxx.xxx.xxx ever change?  If so, you'll probably want to run a Dynamic DNS account somewhere to track that changing IP - otherwise, you won't be able to connect to your VPN the next time that 188.xxx.xxx.xxx IP changes to something else.

If by chance your router is capable of running DD-WRT firmware, consider installing it.  You could run the VPN server directly in the router then and not have this complication on your Kubuntu server (and you'd also be able to wake it up remotely if you don't want to leave it on 24/7).  DD-WRT also has built-in controls for a Dynamic DNS service.

---

### Post by borivoje on 2012-11-18
Thank you very much for this quick reply!

The address 188.x.x.x is my outside address, since I am able from any location to, for example ssh to my server using this address. So, in your words, there is no router on the cable modem. (As I can understand)

I gave up PPTPD setup and started fiddling with OpenVPN. From my original posting I googled a little bit more and found an easy OpenVPN setup [http://blog.johnford.org/openvpn-tunnel-to-home-server/](http://blog.johnford.org/openvpn-tunnel-to-home-server/) This works fine with me, but there are a few problems:

Tunnels are created on both sides (tun0 on the server and tun0 on the client)

When I try to connect with my 3g modem, however, tell-me-my-ip-address sites give me the dongle's address, and not my external address, namely 188.x.x.x

I am beginning to figure that routes play an important role in setting up OpenVPN to direct all traffic through the VPN server. Ant that is my weakness. I really do not understand routes. 

What I did on the server side whas this 
```
echo 1 > /proc/sys/net/ipv4/ip_forward 
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
/sbin/iptables -A FORWARD -i eth0 -o tun0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
/sbin/iptables -A FORWARD -i tun0 -o eth0 -j ACCEPT
```
Should I do the same thing on my client side with only replacing et0 with ppp0?

Thanks in advance!

---

### Post by ahallubuntu on 2012-11-18
If you can ssh into your server from the outside, then obviously you forwarded port (probably) 22 through your firewall, so I assume you have done the same with port 1194.

Unless you have setup a special firewall on your client, you shouldn't have to do anything with iptables.  I use Ubuntu 10.04 LTS on my laptop with the Network Manager OpenVPN plugin, and connecting to my OpenVPN server is very easy.  I didn't have to do anything special on the client: just copy the certificates etc for the OpenVPN configuration.  I'm  not sure what you are using for a client.

Do you see anything in your OpenVPN server logfile when trying to connect?

---

### Post by borivoje on 2012-11-18
It sound very wierd to me, because I do not use any client. I just start the service as a server (on the server side) and as a client (on the client side). What diverted me most from using the VPN Client (from MATE's network manager) is that server config does not specify for username and password, which the manager requires.

---

### Post by ahallubuntu on 2012-11-18
Just to define terminology: when you are connecting to a VPN in a "road warrior" configuration (as you seem to have), there is a VPN server and a VPN client.  Like, at the moment, I have an OpenVPN server running on my DD-WRT router at home.  I'm connected to it via my laptop remotely right now.  My laptop is the "client" machine, and the OpenVPN "client" on my laptop runs only when I am connected to my VPN.  The router is running the "server."

So, it doesn't make sense to say you aren't running a "client."  By definition, you must be if you are connecting to the server.  That's unless you are trying to run a "server to server" VPN which it sounds like you are not.

Can you please describe exactly what you are doing?  What kind of client machine are you using?  Laptop?  Running what operating system?  I know the server uses Kubuntu.

Again as an example: I'm using Ubuntu 10.04 LTS for my laptop (the client).  It has OpenVPN plug-in installed for Network Manager.  With that, I can configure (with the Gui) the type of OpenVPN connection I have (static key, password, certificates, etc.)  It was very easy to set this part up, once I installed this plug-in.  No editing of files is required, no terminal commands.  But I don't know what kind of client machine you are using, so I can't tell you exactly how to do this.

---

### Post by borivoje on 2012-11-19
Thank you ahallubuntu for the reply.

Yes, it is dumb to say that there is no client in network business. What I ment is that I ran openvpn as a deamon from both the server and the client machines.
So regarding my system for vpn I have the following: home network which  is on 192.168.1.0 subnet. I DON'T HAVE server on my router (Which is  some TPLINK). I am running the openvpn server form one of my "clients" namely  desktop which runs Kubuntu. I am accessing this home network with Acer netbook. The connection can be ppp0 (3G modem) or the network at my office at the Univerisity where, in order to "get out" to the internet, you must set up a  proxy.

Meanwhile I ran into this 

[http://askubuntu.com/questions/35647/how-do-i-setup-openvpn-so-i-can-securely-use-the-internet-from-an-unsecured-hots](http://askubuntu.com/questions/35647/how-do-i-setup-openvpn-so-i-can-securely-use-the-internet-from-an-unsecured-hots)

I think that this procedure is exactly what you were talking about.
I went on to set up the configs as described in this post on askubuntu.

The present state:

I have set up certificates and keys successfully.
I try to connect from my office via proxy:

```
 
borivoje@borivoje-AOD270 /etc/openvpn $ sudo openvpn client.conf
[sudo] password for borivoje: 
Mon Nov 19 10:06:43 2012 OpenVPN 2.2.1 i686-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Mar 30 2012
Mon Nov 19 10:06:43 2012 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Mon Nov 19 10:06:43 2012 Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Mon Nov 19 10:06:43 2012 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Nov 19 10:06:43 2012 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Nov 19 10:06:43 2012 LZO compression initialized
Mon Nov 19 10:06:43 2012 Control Channel MTU parms [ L:1576 D:168 EF:68 EB:0 ET:0 EL:0 ]
Mon Nov 19 10:06:43 2012 Socket Buffers: R=[87380->131072] S=[16384->131072]
Mon Nov 19 10:06:43 2012 Data Channel MTU parms [ L:1576 D:1450 EF:44 EB:135 ET:32 EL:0 AF:3/1 ]
Mon Nov 19 10:06:43 2012 Local Options hash (VER=V4): 'e39a3273'
Mon Nov 19 10:06:43 2012 Expected Remote Options hash (VER=V4): '3c14feac'
Mon Nov 19 10:06:43 2012 NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Mon Nov 19 10:06:43 2012 Attempting to establish TCP connection with [AF_INET]147.x.x.x:8080 [nonblock]
Mon Nov 19 10:06:44 2012 TCP connection established with [AF_INET]147.x.x.x:8080
Mon Nov 19 10:06:44 2012 Send to HTTP proxy: 'CONNECT 188.x.x.x:443 HTTP/1.0'
Mon Nov 19 10:06:49 2012 recv_line: TCP port read timeout expired: Operation now in progress (errno=115)
Mon Nov 19 10:06:49 2012 TCP/UDP: Closing socket
Mon Nov 19 10:06:49 2012 SIGUSR1[soft,init_instance] received, process restarting
Mon Nov 19 10:06:49 2012 Restart pause, 5 second(s)

```

My server.conf

```

proto tcp
dev tap
ca ca.crt
cert server.crt
key server.key
dh dh1024.pem
server 10.8.0.0 255.255.255.0
push "redirect-gateway def1"
ifconfig-pool-persist ipp.txt
keepalive 60 300
tls-auth ta.key 0
# Compress data to save bandwidth
comp-lzo
user openvpn
group openvpn
persist-key
persist-tun
# Logs are useful for debugging
log-append openvpn-log
verb 3
mute 10

```

My client config

```

client
dev tap
proto tcp
# replace 1.2.3.4 by your server IP
remote 188.x.x.x 443
http-proxy 147.x.x.x 8080
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert you.crt
key you.key
ns-cert-type server
tls-auth ta.key 1
comp-lzo
user nobody
group nogroup
verb 3
mute 20
--http-proxy-retry
```

I switched form the standard 1194 port to 443, since, it seems, that proxy does not allow the connection to the 1194, giving the Forbidden 403 errror.

I think that it is much more clear now.

Thanks for your patience!

---

