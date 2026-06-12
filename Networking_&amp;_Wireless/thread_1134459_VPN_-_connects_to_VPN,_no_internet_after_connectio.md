---
title: "VPN - connects to VPN, no internet after connection"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by mykrob on 2009-04-23
I am running Ubuntu 9.04 Gnome on my laptop. I set up an Untangle server at my church, and I am running the OpenVPN server component on it. I distributed a key to myself to test, and I am able to connect to the church VPN from the next city over just fine, I printed a test page to a friend's office to make sure it worked, and he confirmed it works.

One problem... While connected to the VPN, i have no external internet connection. The second I release the VPN connection, my internet connection resumes.

I assume this is due to a faulty configuration in Network Manager. When I am just using the internet connection, running the route command in terminal give the appropriate output. WHen connected to the VPN, i get blank output from the route command.

I need help properly configuring network manager to still allow me to use the internet while connected to the VPN.

help?

Thanks,
-myk

---

### Post by mykrob on 2009-04-24
bump

---

### Post by coutts99 on 2009-04-24
What kind of VPN? OpenVPN, IPSEC?

---

### Post by mykrob on 2009-04-24
OpenVPN through an Untangle Network Gateway
[www.untangle.com](www.untangle.com)


It works fine using a Windows machine, I have verified the setup on the server end is good, just need to figure out proper network manager configuration.

thank you

---

### Post by coutts99 on 2009-04-24
I never use network manager for openvpn configuration, just a hand crafted openvpn conf file and away it goes :)

---

### Post by mykrob on 2009-04-24
Just puzzling, I can access all the remote network resources, just cant browse the web. Where might I locate the VPN config file, I assume that NM has made one somewhere

---

### Post by coutts99 on 2009-04-24
/etc/openvpn maybe?

Is the server side set to dish out a default route?

---

### Post by zaomaster on 2009-04-24
If you are using NetworkManager and network-manager-openvpn to make your connections, then there should be a selection under "Routes" in the vpn config tab "IPv4 Settings" that controls the routes. A check box should be there to route only requests to ip's on that server through the vpn. If checked everything else should be routed over your normal internet connection.

I will grant that I'm looking at the config for a pptp connection, but I would assume they are mildly the same in regards to routing.

hope this helps.

---

### Post by wmgries on 2009-04-24
I'm experiencing a similar problem with Ubuntu Server 8.10 (Server side, obviously) and Mac OS 10.5.6 with Viscosity.  Once VPN'ed in, I can connect to my server with ssh and see the Apache server from Safari with the internal IP address, but I cannot access anything else on my home network or the internet.  

Primarily, I'm trying to have a connection to my server so I don't have to use FTP, but I want to also be able to connect to the internet.  At first I thought I had set something up wrong on my Mac, but I've played around with every setting on it with no luck.

My case seems similar, so I'd thought I'd post I'm also having the problem but I apologize if it turns  out to be a completely different issue.

---

### Post by wkulecz on 2009-04-24
> Once VPN'ed in, I can connect to my server with ssh and see the Apache server from Safari with the internal IP address, but I cannot access anything else on my home network or the internet

I've no great experience in the VPN world, but this behavior seems the norm in my experience.  Think about it, if the VPN software allows your machine to connect to the internet at large and you get hacked, then your machine via the VPN access would become a tunnel into the other network and your home network bypassing any firewalls.

While this may be what you want, the security implications of allowing it by default need to be carefully thought out, which is why I suspect the default VPN setups don't allow it.

--wally.

---

### Post by wmgries on 2009-04-24
> **wkulecz said:**
> I've no great experience in the VPN world, but this behavior seems the norm in my experience.  Think about it, if the VPN software allows your machine to connect to the internet at large and you get hacked, then your machine via the VPN access would become a tunnel into the other network and your home network bypassing any firewalls.

While this may be what you want, the security implications of allowing it by default need to be carefully thought out, which is why I suspect the default VPN setups don't allow it.

--wally.

Well I certainly am not trying to discount your experience, but being able to have the extra connectivity is important to me.  I have the connection setup so that I can work on my web stuff when I'm not on my home network, and not having access to the outside internet hurts my overall mission about having a VPN.

Also, I assume mykrob has a similar reason why he'd be able to access the internet while connected to the VPN.

---

### Post by wkulecz on 2009-04-24
You are going to have to learn how to setup VPN to do what you want if the default setup doesn't do it.  I just hope you understand the security implications of doing what you desire.

---

### Post by wmgries on 2009-04-24
> **wkulecz said:**
> You are going to have to learn how to setup VPN to do what you want if the default setup doesn't do it.  I just hope you understand the security implications of doing what you desire.

Yes, I know - that's why I'm asking for help.  I've spent a week and a half trying to track down stuff on the internet about it but I can't seem to figure out how to do it.  Also, it is implied by many sites I've found that the capability to access the internet and other devices on the network.

Furthermore, what is the point to using a VPN if I can't do anything but ssh into my server?  I want to be able to access my files in Finder like I'm on the network and I want to be able to access other machines on my network.  Also all of the computers are password protected and firewalled.  I mean I understand this could pose a security risk, but I've taken steps to secure as much as possible.  Plus loads of companies do this.  I know people whose VPN access into their respective companies allow them to see every file, computer, print on the company network.

---

### Post by The Cog on 2009-04-24
From [http://openvpn.net/howto.html:](http://openvpn.net/howto.html:)
> # If enabled, this directive will configure
# all clients to redirect their default
# network gateway through the VPN, causing
# all IP traffic such as web browsing and
# and DNS lookups to go through the VPN
# (The OpenVPN server machine may need to NAT
# the TUN/TAP interface to the internet in
# order for this to work properly).
# CAVEAT: May break client's network config if
# client's local DHCP server packets get routed
# through the tunnel.  Solution: make sure
# client's local DHCP server is reachable via
# a more specific route than the default route
# of 0.0.0.0/0.0.0.0.
;push "redirect-gateway"

Which may be your problem. The setting is in the server config file, probably in /etc/openvpn.

---

### Post by wmgries on 2009-04-24
> **The Cog said:**
> From [http://openvpn.net/howto.html:](http://openvpn.net/howto.html:)

Which may be your problem. The setting is in the server config file, probably in /etc/openvpn.

I assume that the ';' is a comment character so yes I have that setting in my configuration file, uncommented.

---

### Post by mykrob on 2009-04-24
> **wmgries said:**
> I assume that the ';' is a comment character so yes I have that setting in my configuration file, uncommented.

Where is the file you're looking at?

If anyone gets this working ,please let me know what you did.

I tried it on a Windows laptop using the client config file generated by the server. Distributed the key to the laptop, logged into the VPN, and was able to access internal resources as well as the internet. I would assume that if the VPN has access to the internet, by my logic, when connected to the VPN, you would have the same access as you would if you were in the building. In other words, If he has internet access when he is at the church, he should have internet access when connected to the VPN from home.

Thanks,
-myk

---

### Post by wmgries on 2009-04-24
> **mykrob said:**
> Where is the file you're looking at?

If anyone gets this working ,please let me know what you did.

I tried it on a Windows laptop using the client config file generated by the server. Distributed the key to the laptop, logged into the VPN, and was able to access internal resources as well as the internet. I would assume that if the VPN has access to the internet, by my logic, when connected to the VPN, you would have the same access as you would if you were in the building. In other words, If he has internet access when he is at the church, he should have internet access when connected to the VPN from home.

Thanks,
-myk

/etc/openvpn/server.conf

---

### Post by mykrob on 2009-04-25
I dont have this file

```

myk@mobileOne:~$ cd /etc/openvpn/
myk@mobileOne:/etc/openvpn$ ls
update-resolv-conf
myk@mobileOne:/etc/openvpn$ 

```

granted this is from the client machine, not the server. But i can assume the server is properly configured, because I distribute the key to a windows machine, and it works as expected.

Thanks,
-myk

---

### Post by The Cog on 2009-04-25
Sorry, I shluld have been clearer.
That configuration item:
> push "redirect-gateway"
is a configuration item on the server, not the client. It tells the server to push a redirect-gateway directive to the clients as they connect, which makes them use the VPN for all their internet access instead of their local internet connection. You can comment it out by putting a semicolon ';' or a hash '#' at the beginning of the line, in which case the line is ignored and the option is not enabled. 

You have to restart the OpenVPN server after changing the configuration file. The file is normally found in /etc/openvpn/*.conf but this is dependent on how it was installed and configured. You can normally reatart the server with the command:
> sudo /etc/init.d/openvpn restart
but again this might be different in a custom installation.

---

### Post by wmgries on 2009-04-26
No, I have that now.  Hopefully I'll have more time to work on this tomorrow.  I'm positive it has something to do with the way the Server is setup.

---

### Post by juan@forum on 2009-04-26
This is a problem with the Network Manager, it sets up the vpn gateway as the default gateway for all the connections. 

When the server is configured to do it, there is no way to stop it. 

But this issue is on the client side using the Network Manager.

---

### Post by The Cog on 2009-04-26
LOL. 
One of the reasons that OpenVPN is so well liked where I work is because it doesn't enforce that kind of behaviour. You can make a VPN connection to a remote office without it breaking all your internet access.

---

### Post by kevdog on 2009-04-26
How is your vpn setup -- tun/tap?  Which means are you running a bridged or routed connection?  I think you probably want a routed connection, however I could be wrong.  I stopped reading the last page of this thread, however openvpn config directives are usually one file on the server and client.  We need to see these files!

---

### Post by wmgries on 2009-04-26
I have a routed connection, setup (dev tun).  Out of curiosity, do I need to change connections on my server in /etc/network/interfaces?

Here is my server configuration:

```
port 1194 # change this to whatever you need it to be
proto udp # tcp or udp, never use both in the same config
dev tun #routed VPN

# Certificates
ca ca.crt
cert server.crt
key server.key # This file should be kept secret
dh dh1024.pem

# Server settings
server 10.8.0.0 255.255.255.0 # Default VPN ip range.
push "redirect-gateway"

# OpenDNS settings
push "dhcp-option DNS 12.207.234.29"
push "dhcp-option DNS 12.207.235.32"

# Allow clients to see eachother
client-to-client

# Reduce the OpenVPN daemon's privileges
user nobody
group nogroup

```

Also, I have a copy of my /etc/network/interfaces file in case that is needed:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
	wireless-essid *omitted* 
	wireless-key *omitted* 

```

---

### Post by jcostom on 2009-04-26
> **wkulecz said:**
> I've no great experience in the VPN world, but this behavior seems the norm in my experience.  Think about it, if the VPN software allows your machine to connect to the internet at large and you get hacked, then your machine via the VPN access would become a tunnel into the other network and your home network bypassing any firewalls.

While this may be what you want, the security implications of allowing it by default need to be carefully thought out, which is why I suspect the default VPN setups don't allow it.


It's not always the norm.  You'll find two primary VPN configurations out there, Enable or Disable Split Tunneling.  Enabling split tunneling means that only traffic destined for the protected network on the other side goes through the VPN tunnel.  If you disable split tunneling, all traffic rides through the VPN.  If the routing on the central site doesn't support routing to the Internet, you're not going to get there.  In general, split tunneling is popular with users, and not with the Info Security staff.

Some VPN products like the popular Juniper Secure Access product expands this to include options like disable split tunneling, but allow access to local subnet.  This is useful for users that need to print to locally attached network printers while they're on a VPN connection.  This type of configuration is becoming more widely available in other VPN products, and is gaining in popularity, as it allows a balance between infosec's desire to lock down the VPN with the users' desire to be able to print while on the VPN.

Sounds like his problem is that he's forcing all traffic through the VPN.  It's a check box in Network Manager.  Uncheck it.

---

### Post by wmgries on 2009-04-26
> **jcostom said:**
> It's not always the norm.  You'll find two primary VPN configurations out there, Enable or Disable Split Tunneling.  Enabling split tunneling means that only traffic destined for the protected network on the other side goes through the VPN tunnel.  If you disable split tunneling, all traffic rides through the VPN.  If the routing on the central site doesn't support routing to the Internet, you're not going to get there.  In general, split tunneling is popular with users, and not with the Info Security staff.

Some VPN products like the popular Juniper Secure Access product expands this to include options like disable split tunneling, but allow access to local subnet.  This is useful for users that need to print to locally attached network printers while they're on a VPN connection.  This type of configuration is becoming more widely available in other VPN products, and is gaining in popularity, as it allows a balance between infosec's desire to lock down the VPN with the users' desire to be able to print while on the VPN.

Sounds like his problem is that he's forcing all traffic through the VPN.  It's a check box in Network Manager.  Uncheck it.

Might help the other guy, but I'm running Ubuntu Server with no DE.  Also, I desire to run all traffic through the VPN.

---

### Post by mykrob on 2009-04-26
Maybe I'm getting confused as to which of these posts is directed toward me, but I still need help. I dont think my server is the issue, i am assuming this because it is a braindead "clicky" setup in Untangle to get it going and it works fine connecting to it from a Windows machine. The VPN part works fine connecting to it form my Ubuntu machine too. I have done nothing in Network Manager except import the files given to me by the server, there is a user certificate, a ca file, and a key, plus the gateway.

My assumption is there is a setting somewhere in Network Manager that I should be focusing on here.

---

### Post by wmgries on 2009-04-26
Ok, it is obvious now these are completely separate problems.  Maybe a mod would come a long and separate?

---

### Post by wmgries on 2009-04-27
bump

---

### Post by noSelf on 2009-05-06
> **juan@forum said:**
> This is a problem with the Network Manager, it sets up the vpn gateway as the default gateway for all the connections. 

When the server is configured to do it, there is no way to stop it. 

But this issue is on the client side using the Network Manager.

For what it's worth, after upgrading from Intrepid to Jaunty with an existing VPN connection configuration, i suddenly had the problem described in the initial message on this thread - i could connect to the VPN fine, but couldn't reach anything other than resources on the LAN i vpn'ed into - no internet. Also, because /etc/resolv.conf is auto-generated, i couldn't hack around in there.

i simply wanted to use the vpn connection for resources on the remote net, and use my "real" connection for everything else (my LAN and internet). After searching & poking i did this via Network Manager:

- select "Configure VPN"
- edit the connection
- select IPv4 Settings tab
- for "Method", choose "Automativ (VPN) addresses only"
- now that it's editable, enter the addresses for the DNS Servers on the remote network
- now that it too is editable, enter the Search Domains for the remote network
- click "Routes"
- check the box labeled "Use this connection only for resources on its network"
- click OK, then Apply

This fixed it for me - no need to add specific routes. Really the only problem with the Jaunty in-place upgrade.

---

### Post by user111970 on 2009-05-06
noSelf, thanks, worked like a charm. You're right, the 9.04 upgrade probably wiped out custom settings which I forgot how to redo.

---

### Post by derxleben on 2009-05-14
Thanks NoSelf - that just saved my life (sanity - I can now browse the internet AND do crap from work on my Ubuntu Laptop) Cheers!

---

### Post by threepwood960 on 2009-05-30
I love these forums! I was fighting with this problem several days ago, and the proposal in here worked!

---

### Post by Mickeysofine1972 on 2009-06-15
Hi

What are the search domains exactly? I have a dns ip but dont really get what I should be putting in the search domains field.

Also. the "Use this connection only for resources on its network" tick box isnt there ! I'm on ibex btw as I cant use jaunty becuase of its rubbish support for Intel video cards.

Mike

> **noSelf said:**
> For what it's worth, after upgrading from Intrepid to Jaunty with an existing VPN connection configuration, i suddenly had the problem described in the initial message on this thread - i could connect to the VPN fine, but couldn't reach anything other than resources on the LAN i vpn'ed into - no internet. Also, because /etc/resolv.conf is auto-generated, i couldn't hack around in there.

i simply wanted to use the vpn connection for resources on the remote net, and use my "real" connection for everything else (my LAN and internet). After searching & poking i did this via Network Manager:

- select "Configure VPN"
- edit the connection
- select IPv4 Settings tab
- for "Method", choose "Automativ (VPN) addresses only"
- now that it's editable, enter the addresses for the DNS Servers on the remote network
- now that it too is editable, enter the Search Domains for the remote network
- click "Routes"
- check the box labeled "Use this connection only for resources on its network"
- click OK, then Apply

This fixed it for me - no need to add specific routes. Really the only problem with the Jaunty in-place upgrade.

---

### Post by Sam inv on 2009-06-30
Hi,

I'm too new to Ubuntu ( well new again used it with Feisty, and had no trouble back then)
Now I can't set up a vpn and use internet at the same time.

For some reason when I have the 'use this connection only for resources on its network" activated I can't reach the host , however network manager says i'm connected.
I can fill in anything from routes, DNS servers,.... internet works but I can't reach the needed app or even ping the server.
When I uncheck that box and leave everything else the same I can reach the app and ping the server, but my internet doesn't work.
What am I doing wrong here?

thx for the help

---

### Post by Eeqmcsq on 2009-07-07
I upgraded from Intrepid to Jaunty, and I have the same problem on my home PC as described by noSelf. My solution is similar to noSelf, except that I left the Method as "Automatic (VPN)". Thus, the only difference for me from Intrepid was to check "Use this connection only for resources on its network".

After that, I was able to surf the Internet while connected to my work VPN server. In fact, Internet surfing (specifically, the http address resolution) while on VPN seemed snappier than back in Intrepid. It was as snappy as though I was not on VPN.

HOWEVER, the new problem is that I am unable to resolve my work PC's name anymore. Here's a summary of my test:

"Use this connection only for resources on its network" is unchecked:
- nslookup my_work_pc (this took a few moments, but it correctly returned my work pc's IP)
- ping my.work.pc.IP (this worked correctly)
- ping 74.125.127.99 (this is google's IP address. this FAILED)

"Use this connection only for resources on its network" is checked:
- nslookup my_work_pc (this FAILED. ** server can't find my_work_pc)
- ping my.work.pc.IP (this worked correctly)
- ping 74.125.127.99 (this worked correctly)

While I can work around the problem by using my work pc's IP instead of its name, the problem still exists. Anyone got any ideas?

---

### Post by noSelf on 2009-07-07
i encountered the same issue - couldn't connect to anything EXCEPT the VPN's local resources when "Use this connection only for resources on its network" is unchecked - couldn't get to the internet at all.

i haven't pursued it further, but need to. As you noticed, you can't resolve hostnames on the VPN's lan. i added a few well-known hosts to my /etc/hosts file, and that helps with getting to some remote resources when programming, but i can't mount Windows shares via SMB from Nautilus, which reduces the VPN's utility substantially.

Seems to be a DNS issue - i think in pre-Jaunty, the VPN automatically used the remote network's DNS for all routing - so my internet trafffic was going through the VPN, not my DSL connection. Probably easy to figure out, i just haven't encountered enough pain to do it yet.

---

### Post by Eeqmcsq on 2009-07-07
I have filed [bug 396387]("https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/396387") about this problem.

---

### Post by joris1977 on 2009-07-09
I guess i have the same problem. My university uses vpn to reach the closed part of the library. Cisco VPN. It used to work nice with network-manager-vpnc but for some reason not anymore. Not sure if it was upgrading to Jaunty that caused it...  I solved it with

sudo apt-get install resolvconf 

suggested in this blog post: [http://www.mattwoodward.com/blog/index.cfm?event=showEntry&entryId=94E5299A-87DD-418A-AC11F9FFC912E1E2](http://www.mattwoodward.com/blog/index.cfm?event=showEntry&entryId=94E5299A-87DD-418A-AC11F9FFC912E1E2) 

I found it after some googling. It solves the problem, but i am not sure this is a good solution.

---

### Post by Eeqmcsq on 2009-11-15
I think I finally figured out the problem. Somehow, /etc/resolv.conf turned out to be a symlink to /etc/resolvconf/run/resolv.conf. If you delete the symlink and reboot, a new resolv.conf text file is generated. The library managing this new text file correctly puts the VPN's DNS servers above the ISP DNS servers.

Here's the entire solution that worked for me:

1. System -> Preferences -> Network Connections -> VPN tab -> Edit (my VPN connection) -> IPv4 Settings tab -> Routes
Make sure "Use this connection only for resources on its network" is checked.
2. Determine if resolv.conf is a symlink. If it is NOT a symlink, then the problem may be something else.
file /etc/resolv.conf
3. If it is a symlink to `/etc/resolvconf/run/resolv.conf', rename it to something else:
sudo mv /etc/resolv.conf /etc/resolv.conf.symlink
4. Reboot.
5. Test and see if you can surf the Internet and connect to your VPN PCs.
6. If test was successful, you can delete /etc/resolv.conf.symlink:
sudo rm /etc/resolv.conf.symlink

---

### Post by noSelf on 2009-11-16
i revisited this after upgrading to Karmic, and discovered that simply adding the DNS servers for the remote network took care of the issue mounting SMB shares.

---

