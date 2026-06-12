---
title: "OpenVPN configuration..."
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by aSteve on 2009-09-28
I'm sure I'm making at least one silly mistake, but I'm getting really frustrated trying to configure a VPN.  I'm broadly familiar with the principles of networking, but this is my first time trying to use either OpenVPN or the NetworkManagerApplet for VPNs.

I'm trying to establish a VPN from an Ubuntu netbook to Gentoo server... but I'm finding it difficult to match client and server configurations... and the error messages from the Ubuntu end don't seem very helpful.

I installed and configured my openvpn server using this 'howto' :

[http://en.gentoo-wiki.com/wiki/OpenVPN](http://en.gentoo-wiki.com/wiki/OpenVPN)

This seems to be the preferred configuration for a server - but I'm able to re-configure if the ubuntu client has other requirements.

In Ubuntu, I use NetworkManagerApplet to "Configure VPN"; I chose "OpenVPN"...

I leave "Connect automatically" unchecked; Enter my server's DNS address as "Gateway"; I leave "Type" as "Certificates TLS" - the default.  For "User Certificate" I use client.crt; for "CA certificate" I use ca.crt; for "Private Key" I use client.key - the files created using the above Gentoo howto.  I leave "Private key password" blank because I didn't specify any password when creating the private key.  In advanced, I check "use custom gateway port" - and copied the port from the server configuration.

When I select the connection from the NetworkManagerApplet icon, I get a brief message telling me that my VPN failed because the service failed to start.  The /var/log/daemon.log file gives a little more information - though not much.

--
Sep 28 20:51:04 Algiz NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'... 
Sep 28 20:51:04 Algiz NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 6917 
Sep 28 20:51:04 Algiz NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections 
Sep 28 20:51:04 Algiz NetworkManager: <info>  VPN plugin state changed: 3 
Sep 28 20:51:04 Algiz NetworkManager: <info>  VPN connection 'VPN connection 1' (Connect) reply received. 
Sep 28 20:51:04 Algiz NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'VPN connection 1' failed to connect: 'No VPN secrets!'. 
Sep 28 20:51:04 Algiz NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Sep 28 20:51:04 Algiz NetworkManager: <info>  Policy set 'Auto WLANSHIC' (ra0) as default for routing and DNS. 
Sep 28 20:51:17 Algiz NetworkManager: <debug> [1254167477.002543] ensure_killed(): waiting for vpn service pid 6917 to exit 
Sep 28 20:51:17 Algiz NetworkManager: <debug> [1254167477.002791] ensure_killed(): vpn service pid 6917 cleaned up 
--

I don't understand why it's complaining about "No VPN secrets" - since both client and server are configured to use TLS certificates and not a shared secret.

Can anyone tell me where I'm going wrong?  Ideally I'd like to use OpenVPN with TLS security (as I perceive that to be least insecure) but it is most important to me that my VPN just works... 

Any hints?

---

### Post by aSteve on 2009-09-29
Erm, is connecting to an OpenVPN server really so esoteric?
(Shameless bump hoping for a reply....)

---

### Post by bigboy7foru on 2009-09-29
> **aSteve said:**
> Erm, is connecting to an OpenVPN server really so esoteric?
(Shameless bump hoping for a reply....)
 
 
If you can't get it to work then yes... Mine is stuck too on the last part

---

### Post by mattkoehn on 2009-09-29
It's not esoteric but it isn't really a ubuntu thing. 

The log you gave is extremely vague and isn't the log from the openvpn service, not sure where that log is off the top of my head.

Are you doing all of this through gui? When I tried the network-manager plugin for openvpn it was flakey. You could try setting up a matching config file for your server which would point to the locations of the ca and keys. There should be an example config file in the install directory of openvpn. Really there are only like 7 or 8 lines necessary for the openvpn config file. Running 'openvpn configfile.ovpn' after you create your config file will give you more description of what is going on, if you can't find the log.

If you have your config for your client or server, you can post them. Just make sure you remove the line on the client where it says the location to connect to. You may want to hide which port you are operating it on, but other than that it should be fine to post.

---

### Post by aSteve on 2009-09-30
> **mattkoehn said:**
> It's not esoteric but it isn't really a ubuntu thing. 

The log you gave is extremely vague and isn't the log from the openvpn service, not sure where that log is off the top of my head.

Are you doing all of this through gui? When I tried the network-manager plugin for openvpn it was flakey. 

The log I posted was from /var/log/daemon.log - and it is the only log into which any messages relevant to the VPN are to be found.  I am using the GUI - the NetworkManagerApplet - i.e. the one that is installed by default and adequately handles connecting to 802.11 services.  There are no server-side log entries.

I agree with the assessment that it is 'flakey' - as I've discovered GUI glitches that disappear with a refresh, for example, but these are merely cosmetic.  Given the high quality of Ubuntu as a whole, it seems unlikely that such a prominent feature in the GUI simply doesn't work at all.  While I'm sure I could hack together scripts that 'work' - I really do want to use the standard GUI... and that's where I'm stuck.

I've posted  the configuration of the OpenVPN server - and I'm able to tweak this if it is incompatible with the Ubuntu GUI as is.  My problem is definitely with Ubuntu and the GUI (NetworkManagerApplet - the one with the "blue stairs graph" for wireless, or the picture of two monitors when connected to a wired network...)

I've found this:

[http://blogs.ubuntu-nl.org/dennis/2007/03/11/easy-openvpn-with-network-manager-in-feisty/](http://blogs.ubuntu-nl.org/dennis/2007/03/11/easy-openvpn-with-network-manager-in-feisty/)

Which suggests that I'm on the right track with the server-side configuration (i.e. a similar key generation technique) but the GUI in this blog is elder than the current one in Ubuntu - My NetworkManager is version 0.7.0.100, and the GUI for the OpenVPN configuration is organised differently.

---

### Post by aSteve on 2009-09-30
Some progress - but still doesn't "work"...

If I select the "Use a TCP connection" in "OpenVPN Advanced Options" from NetworkManager, I get a step further... no working VPN, but I do get more stuff in both server and client logs.

Client side...
--
Sep 30 14:46:26 Algiz NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'... 
Sep 30 14:46:26 Algiz NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 14418 
Sep 30 14:46:26 Algiz NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections 
Sep 30 14:46:26 Algiz NetworkManager: <info>  VPN plugin state changed: 1 
Sep 30 14:46:26 Algiz nm-openvpn[14422]: OpenVPN 2.1_rc11 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Mar  9 2009
Sep 30 14:46:26 Algiz nm-openvpn[14422]: WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Sep 30 14:46:26 Algiz nm-openvpn[14422]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Sep 30 14:46:26 Algiz NetworkManager: <info>  VPN plugin state changed: 3 
Sep 30 14:46:26 Algiz NetworkManager: <info>  VPN connection 'SHIC VPN' (Connect) reply received. 
Sep 30 14:46:26 Algiz nm-openvpn[14422]: /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Sep 30 14:46:26 Algiz nm-openvpn[14422]: Attempting to establish TCP connection with 10.0.1.1:21194 [nonblock]
Sep 30 14:46:27 Algiz nm-openvpn[14422]: TCP connection established with 10.0.1.1:21194
Sep 30 14:46:27 Algiz nm-openvpn[14422]: TCPv4_CLIENT link local: [undef]
Sep 30 14:46:27 Algiz nm-openvpn[14422]: TCPv4_CLIENT link remote: 10.0.1.1:21194
Sep 30 14:46:27 Algiz nm-openvpn[14422]: Connection reset, restarting [-1]
Sep 30 14:46:27 Algiz nm-openvpn[14422]: SIGUSR1[soft,connection-reset] received, process restarting
--

Then the last 10 nm-openvpn lines repeat... suggesting that the GUI is re-trying the same configuration multiple times before giving up.  I don't understand the relevance of the "WARNING" - especially as this is reported on the Ubuntu client.

Server-side, I get more feedback, too...
--
Sep 30 14:45:51 ken openvpn[22995]: MULTI: multi_create_instance called
Sep 30 14:45:51 ken openvpn[22995]: Re-using SSL/TLS context
Sep 30 14:45:51 ken openvpn[22995]: LZO compression initialized
Sep 30 14:45:51 ken openvpn[22995]: Control Channel MTU parms [ L:1544 D:140 EF:40 EB:0 ET:0 EL:0 ]
Sep 30 14:45:51 ken openvpn[22995]: Data Channel MTU parms [ L:1544 D:1450 EF:44 EB:135 ET:0 EL:0 AF:3/1 ]
Sep 30 14:45:51 ken openvpn[22995]: Local Options hash (VER=V4): 'c0103fa8'
Sep 30 14:45:51 ken openvpn[22995]: Expected Remote Options hash (VER=V4): '69109d17'
Sep 30 14:45:51 ken openvpn[22995]: TCP connection established with 10.0.1.248:38411
Sep 30 14:45:51 ken openvpn[22995]: Socket Buffers: R=[131072->131072] S=[131072->131072]
Sep 30 14:45:51 ken openvpn[22995]: TCPv4_SERVER link local: [undef]
Sep 30 14:45:51 ken openvpn[22995]: TCPv4_SERVER link remote: 10.0.1.248:38411
Sep 30 14:45:51 ken openvpn[22995]: 10.0.1.248:38411 TLS: Initial packet from 10.0.1.248:38411, sid=32acef50 e0390bb2
Sep 30 14:45:52 ken openvpn[22995]: 10.0.1.248:38411 VERIFY ERROR: depth=0, error=unsupported certificate purpose: /C=UK/ST=N/A/L=Bath/O=SHIC/CN=client/emailAddress=admin_vpn@shic.co.uk
Sep 30 14:45:52 ken openvpn[22995]: 10.0.1.248:38411 TLS_ERROR: BIO read tls_read_plaintext error: error:140890B2:SSL routines:SSL3_GET_CLIENT_CERTIFICATE:no certificate returned
Sep 30 14:45:52 ken openvpn[22995]: 10.0.1.248:38411 TLS Error: TLS object -> incoming plaintext read error
Sep 30 14:45:52 ken openvpn[22995]: 10.0.1.248:38411 TLS Error: TLS handshake failed
Sep 30 14:45:52 ken openvpn[22995]: 10.0.1.248:38411 Fatal TLS error (check_tls_errors_co), restarting
Sep 30 14:45:52 ken openvpn[22995]: 10.0.1.248:38411 SIGUSR1[soft,tls-error] received, client-instance restarting
Sep 30 14:45:52 ken openvpn[22995]: TCP/UDP: Closing socket
Sep 30 14:45:57 ken openvpn[22995]: MULTI: multi_create_instance called
Sep 30 14:45:57 ken openvpn[22995]: Re-using SSL/TLS context
Sep 30 14:45:57 ken openvpn[22995]: LZO compression initialized
--

Ignoring the small discrepancy with time-stamps, this clearly shows that there is progress... I don't understand, however, why openvpn is unhappy with my certificate.  Furthermore, I'm not clear if it is the server or client certificate that is inappropriate... The certificates were created using the Howto I posted above - so, I hope they'd have appropriate uses specified...  I didn't create them myself using openssl or anything "complicated" like that...

I still think this looks more like a Ubuntu/Network Manager issue rather than purely an openvpn issue... though I recognise that it might not be clear which component is at fault...

Can anyone see my next mistake (after not having checked "use tcp" client-side to match the "tcp" line server-side)?

---

### Post by aSteve on 2009-09-30
Erm, OK - more progress... I re-created my certificates from scratch, and this overcomes the issues with 'purpose'... and I'm presented with a bunch of other warnings/errors... but now, while I don't have a 'working' VPN, ifconfig does report a device and NetworkManager thinks it has a VPN that it is managing.

My biggest issue, I suspect, might be in establishing routes... but that, Is an openvpn thing - not particularly Ubuntu.

There definitely are issues with the error messages from NetworkManager - it could be much more helpful... but it does seem to 'work' - at least in some sense...

I'm not sure if my ramblings will help others facing similar problems - except, maybe, to note that persistence paid off for me.

---

### Post by mattkoehn on 2009-10-01
Couple things.

The gui for open-vpn is by no means core to ubuntu. It's a plugin you have to install seperate. And using a config file isn't a script, it's the default way to interface with openvpn. If you check out [www.openvpn.org/howto](www.openvpn.org/howto) it will recommend that way, as it is easier to diagnose and fix problems. You are adding a layer of complexity, whether you realise it or not, but using the gui tool.

However, you are free to do which every way you want, it just may be more difficult if you are running into connection issues which it seems like you are.

Make sure your network layout is as simple as possible.  Your server and client for testing are on the same network (get their ip addresses from the same dhcp server or same router). That will eliminate issues from port forwarding.

Your server looks like it is working correctly and accepting connections. If you copied the correct keys over, it shouldn't be an issue.

Just test your server the first time with the simplest network setup possible, then as soon as you get a connection, try it through a router or over the internet(like through dyndns).

---

### Post by amagi on 2009-10-13
When using 9.04 it was almost always (95%) that the first time I tried to connect through the network manager to openvpn that I got a message Connection Failed. But most of the time the second try did work.

Now I have upgraded to 9.10 and it seems to get even worse. I have now, out of pure frustration tried it like connecting 20 times and suddenly it connected. Howecer the first few times it gave the same message, see below.

And I repeat, I did not change ANYTHING except just connecting a few times right after each other!!!

```

When using 9.04 it was almost always (95%) that the first time I tried to connect through the network manager to openvpn that I got a message Connection Failed. But most of the time the second try did work.

Now I have upgraded to 9.10 and it seems to get even worse. I have now, out of pure frustration tried it like connecting 20 times and suddenly it connected. Howecer the first few times it gave the same message, see below.

And I repeat, I did not change ANYTHING except just connecting a few times right after each other!!!

[CODE]
Oct 13 20:43:56 localhost NetworkManager: <info>  VPN plugin state changed: 3
Oct 13 20:43:56 localhost NetworkManager: <info>  VPN connection 'RS0001' (Connect) reply received.
Oct 13 20:43:56 localhost NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'RS0001' failed to connect: 'No VPN secrets!'.
Oct 13 20:43:56 localhost NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Oct 13 20:43:56 localhost NetworkManager: <info>  Policy set 'Auto Kataru' (wlan0) as default for routing and DNS.
Oct 13 20:44:01 localhost NetworkManager: <info>  VPN plugin state changed: 3
Oct 13 20:44:01 localhost NetworkManager: <info>  VPN connection 'RS0001' (Connect) reply received.
Oct 13 20:44:01 localhost NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'RS0001' failed to connect: 'No VPN secrets!'.
Oct 13 20:44:01 localhost NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Oct 13 20:44:01 localhost NetworkManager: <info>  Policy set 'Auto Kataru' (wlan0) as default for routing and DNS.
Oct 13 20:44:05 localhost NetworkManager: <info>  VPN plugin state changed: 3
Oct 13 20:44:05 localhost NetworkManager: <info>  VPN connection 'BM' (Connect) reply received.
Oct 13 20:44:05 localhost NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'BM' failed to connect: 'No VPN secrets!'.
Oct 13 20:44:05 localhost NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Oct 13 20:44:05 localhost NetworkManager: <info>  Policy set 'Auto Kataru' (wlan0) as default for routing and DNS.
Oct 13 20:44:09 localhost NetworkManager: <info>  VPN plugin state changed: 3
Oct 13 20:44:09 localhost NetworkManager: <info>  VPN connection 'BM' (Connect) reply received.
Oct 13 20:44:09 localhost NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'BM' failed to connect: 'No VPN secrets!'.
Oct 13 20:44:09 localhost NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Oct 13 20:44:09 localhost NetworkManager: <info>  Policy set 'Auto Kataru' (wlan0) as default for routing and DNS.
Oct 13 20:44:14 localhost NetworkManager: <info>  VPN plugin state changed: 3
Oct 13 20:44:14 localhost NetworkManager: <info>  VPN connection 'RS0001' (Connect) reply received.
Oct 13 20:44:14 localhost NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'RS0001' failed to connect: 'No VPN secrets!'.
Oct 13 20:44:14 localhost NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Oct 13 20:44:14 localhost NetworkManager: <info>  Policy set 'Auto Kataru' (wlan0) as default for routing and DNS.
Oct 13 20:44:21 localhost NetworkManager: <info>  VPN plugin state changed: 3
Oct 13 20:44:21 localhost NetworkManager: <info>  VPN connection 'RS0001' (Connect) reply received.
Oct 13 20:44:21 localhost nm-openvpn[13000]: OpenVPN 2.1_rc19 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Jul 27 2009
Oct 13 20:44:21 localhost nm-openvpn[13000]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Oct 13 20:44:21 localhost nm-openvpn[13000]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Oct 13 20:44:21 localhost nm-openvpn[13000]: /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Oct 13 20:44:23 localhost nm-openvpn[13000]: LZO compression initialized
Oct 13 20:44:23 localhost nm-openvpn[13000]: UDPv4 link local: [undef]
Oct 13 20:44:23 localhost nm-openvpn[13000]: UDPv4 link remote: xxx.xxx.xxx.xxx:1194
Oct 13 20:44:23 localhost nm-openvpn[13000]: [server] Peer Connection Initiated with xxx.xxx.xxx.xxx:1194
Oct 13 20:44:24 localhost NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Oct 13 20:44:24 localhost NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Oct 13 20:44:24 localhost nm-openvpn[13000]: TUN/TAP device tun0 opened
Oct 13 20:44:24 localhost nm-openvpn[13000]: /sbin/ifconfig tun0 172.20.10.6 pointopoint 172.20.10.5 mtu 1500

```

I have no clue what is going. Unfortunately under 9.04 it mostly worked and sometimes failed, but now under 9.10 it mostly failes and only sometimes works!

---

### Post by Mark V on 2009-10-20
Hi, I have recently had a rough install of openvpn as well.  Let me explain some things I ran into.
1. I found out I was starting multiple instances of openvpn.
    You need to use something like openvpn [server config file] 
    with the full directory path to that config file
    ie. /etc/openvpn/server.conf
    and do this from the command prompt so you don't have to learn to 
    run it as a service or daemon.
    Once you start it with something like:
    openvpn /etc/openvpn/server.conf
    if it runs with no errors, it will continue to run, so don't
    use the command openvpn /etc/openvpn/server.conf again, unless
    you want two instances of openvpn running with each 
    of them overwriting each others support files/logs 
    causing you great problems.
    You can find if openvpn is running with ps -A and look for openvpn.
    If you have multiple instances you will have more than one tunnel 
    (tun0) (tun1).... when you run ifconfig.
2.  If you are getting things like
    WARNING: No server certificate verification method has been enabled.
    or
    No VPN secrets!
    Either you have not set up your server.conf file or you have 
    more than one server.conf file and the one its finding is not 
    configured properly.  Type: find / -name server.conf <enter> 
    and search your server for more than one config file.  
    I had multiple problems and several were solved by completely 
    removing and reinstalling openvpn and rebuilding the ca as well
    as the keys.  This is not as complicated as it first looks :>)
3.  Make sure you have your keys somewhere such as /etc/openvpn/keys
    so openvpn can find them. Make sure you are placing the correct 
    config and key files on the server and client.  Write notes saying
    where your files are on your server and also your client.  If you
    have your server keys at /etc/openvpn/keys, then make sure that 
    is where you store your client keys on your client.   All this 
    will help you avoid confusion. 
4.  So you have configured:
    server.conf on the server
    client.conf on the client
    type:  
    cat server.conf
    cat client.conf
    put them into a text editor and compare them side by side.
    There are single settings, that if different, will cause failure.
    review this carefully, every step is important:
[http://www.openvpn.net/index.php/open-source/documentation/howto.html#startup](http://www.openvpn.net/index.php/open-source/documentation/howto.html#startup)
5.  Did you give the complete path for?:
    ca ca.crt
    cert client.crt
    key client.key?
    These need to be like:
    ca   /etc/openvpn/key/ca.crt
    cert /etc/openvpn/key/client.crt
    key  /etc/openvpn/key/client.key

---

### Post by Mark V on 2009-10-20
> **aSteve said:**
> 
For "User Certificate" I use client.crt; for "CA certificate" I use ca.crt; for "Private Key" I use client.key - the files created using the above Gentoo howto.  

aSteve,  did your line for ca.crt  and client.key include a path like 
/etc/openvpn/keys/ca.crt 
and
/etc/openvpn/keys/client.key?

---

### Post by YesWeCan on 2009-10-20
> **aSteve said:**
> Erm, is connecting to an OpenVPN server really so esoteric?
(Shameless bump hoping for a reply....)

Maybe not so much *esoteric* as dangerously *flexible*. I'm not sure what's going wrong with your set-up but I've just set up a routed VPN between a ubuntu client and a suse host and it works and works very well. In my experience the key is to keep everything as simple as possible.

To this end I would recommend dispensing with GUI wizards and such and just edit the, quite simple, server.conf and client.conf text files yourself. In simplest form, that's all VPN uses: those two files and key file(s). The openvpn site is excellent and suggests quick and simple config files that dispense with much of the *flexibility* that you may not need at this stage.

It would help me and others to help you if you post the these two files here.

My other caution is about firewalls. If you can safely disable them while you get this working all the better. The server firewall needs to allow port 1194 traffic AND it needs to allow tun0/tap0 traffic. I don't think the firewall matters on the client side because the client initiates the tunnel.

---

### Post by aSteve on 2009-11-12
> **mattkoehn said:**
> The gui for open-vpn is by no means core to ubuntu. It's a plugin you have to install seperate. And using a config file isn't a script, it's the default way to interface with openvpn. If you check out [www.openvpn.org/howto]("http://www.openvpn.org/howto") it will recommend that way, as it is easier to diagnose and fix problems. You are adding a layer of complexity, whether you realise it or not, but using the gui tool.


I recognise that the open-vpn GUI isn't core to Ubuntu - but it is the obvious way to go about managing access to a VPN - given that NetworkManager is core.  In any case, It would be great if it worked properly... 

My problems aren't with open-vpn, per se, as far as I can tell. I've not got to the bottom of this, but I've noticed, for example, that attempts to connect have a success roughly inversely proportional to the number of network hops to the server.  It appears to be an issue mostly with some sort of time-out... and the issue also seems to relate to NetworkManager... and I only use that on Ubuntu.

It is absolutely infuriating to have something that clearly is intended to do exactly what I need... but which only works properly about 5% of the time.

---

### Post by aSteve on 2009-11-12
> **YesWeCan said:**
> 
It would help me and others to help you if you post the these two files here.


My server config:

--
# non default port to prevent worm attacks!
port 21194
proto tcp
dev tun
ca vpn/ca.crt
cert vpn/vpnserver.crt
key vpn/vpnserver.key
dh vpn/dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
keepalive 10 120
comp-lzo
user nobody
group nobody
persist-key
persist-tun
status openvpn-status.log
verb 3
keepalive 10 60
push "route 62.89.140.53 255.255.255.255" # Special route to ISP smtp
client-config-dir ccd
--

I can't find a client-side textual config file - I suspect it is done with command-line options from the GUI.

P.S. Another observation - I seem to get the 'No secrets' style of failure if a prior connection attempt has recently failed.  I seem to get further if I attempt to connect less often... This looks like a clear bug to me...

---

### Post by aSteve on 2009-11-12
> **Mark V said:**
> aSteve,  did your line for ca.crt  and client.key include a path like 
/etc/openvpn/keys/ca.crt 
and
/etc/openvpn/keys/client.key?

No, but that's not the problem... if the path were wrong to the certificates, surely this would always prevent connections?

---

