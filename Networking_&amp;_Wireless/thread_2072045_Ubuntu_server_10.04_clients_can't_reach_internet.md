---
title: "Ubuntu server 10.04 clients can't reach internet"
date: 2012-10-16
forum: Networking &amp; Wireless
---

### Post by hawaiiman on 2012-10-16
10.04 LTS 64bit server plus gnome.
internet--adsl modem/router--eth0(WAN)--server--eth1(LAN)--switch--wired windows clients
dhcp and dns via dnsmasq
ufw installed but not enabled (yet)
auto eth0
iface eth0 dhcp
 
auto eth1
iface eth1 static
address 10.10.0.1
netmask 255.255.255.0
 
network range defined in dnsmasq  `range 10.10.0.10, 10.10.0.150'
 
client shows "unidentified network no Internet access"
ipconfig /all :
Ethernet adapter Local Area Connection:
 Connection-specific DNS Suffix .:
 Description..................: Intel(R) 82577LC Gigabit Network Connection
 Physical Address...........: 00-23-18-E4-5E-92
 DHCP Enabled..............: Yes
 Autoconfiguration Enabled: Yes
 Link-local IPv6 Address....: fe80::41e1:a900:bd66:7385%10(Preferred)
 IPv4 Address..................: 10.10.0.34(Preferred)
 Subnet Mask.................: 255.255.255.0
 Lease Obtained..............: Wednesday, October 17, 2012 9:02:55 AM
 Lease Expires................. Wednesday, October 17, 2012 5:02:55 PM
 Default Gateway.............: 192.168.1.1
 DHCP Server...................: 10.10.0.1
 DHCPv6 IAID...................: 234890008
 DHCPv6 Client DVID.........: 00-01-00-01-14-56-41-72-00-23-18-E4-5E-92
 
 DNS Servers...................: 10.10.0.1
 Netbios over Tcpip..........: Enabled
 
ping to 192.168.1.6 (current eth0) "request timed out, sent=4, received=2, lost=2 "
ping to 127.0.01 "(0% loss) Average time=0ms
ping to 10.10.0.1 "(0% loss) Average time=0ms
 
/etc/default/ufw `DEFAULT_FORWARD_POLICY="ACCEPT"
 
/etc/ufw/sysctl.conf `net/ipv4/ip_forward=1' (uncommented)
 
Win clients can't get on the net. What did I do wrong?

---

### Post by darkod on 2012-10-17
In the ipconfig /all look at the Default Gateway value, it's 192.168.1.1.

It should be 10.10.0.1 because in that setup for the machines on the LAn the gateway is the eth1 interface of the server. I don't know how it works in dnsmasq but you have to find a way to configure that the dnsmasq info provided to the clients tells them that the gateway is 10.10.0.1.

Or if dnsmasq is limited and can't do this, you will have to use the ubuntu dhcp server.

---

### Post by darkod on 2012-10-17
By reading the dnsmasq man page, it seems you need to add in /etc/dnsmasq.conf the following line:
```
--dhcp-option=option:router,10.10.0.1
```

That should tell the clients that the router (gateway) is 10.10.0.1. After you change that and restart the server, don't forget to do on the windows clients:
ipconfig /renew

to get the new lease options.

---

### Post by hawaiiman on 2012-10-17
Ok, Thanks I'll try it.
I'm using a dnsmasq tutorial  [http://www.dickson.me.uk/2012/03/26/setting-up-dnsmasq-with-ubuntu-10-04-for-home-networking/](http://www.dickson.me.uk/2012/03/26/setting-up-dnsmasq-with-ubuntu-10-04-for-home-networking/)
 
which is for a topolgy like mine. He suggests it on line 59. The line number is different in dnsmasq.
 BTW in past setups like this that are fully up, the clients can ping through to the router and even to google .com. That's why I assumed it wasn't a problem. I just assumed it was a forwarding issue.

---

### Post by darkod on 2012-10-17
Yes, but in that tutorial he is working with only one range, 192.168.1.x.

Not with two ranges like you have, 192.168.1.x and 10.10.0.x. So you have to be careful and separate them. The topology is not exactly the same.

You say pinging google.com works, but that would be very strange. With the current setup, without adding the router option in dnsmasq, can you ping 192.168.1.1 from the windows clients? You shouldn't be able to, they are in completely different subnet 10.10.0.x and don't have the gateway set correctly.

Also, the server eth0 interface is connected directly to the router, right? Without any switch or anything?

---

### Post by hawaiiman on 2012-10-17
Ok, let me clarify. The topology is as shown in th op. A strait line through the server from the modem/router to server then switch then clients.
I commented out the line we are discussing in dnsmasq. The only changes: the client report shows gateway as 10.10.0.1, still getting a lease and a dhcp ip number 10.10.0.34.Client can now ping to eth0's ip 192.168.1.6, but not to 192.168.1.1(router). No internet access

---

### Post by hawaiiman on 2012-10-17
There is some mention in the tutorial of adding recursive dns server to resolv.conf. I carefully did so, but after a re-boot the only one that stays is 192.168.1.1. Not really a concern for me. I am on a different adsl isp than at school. In either case speed of dns response hasn't been a huge concern. Usually in a range from 64ms-22ms, which I planned on improving with a dns cache in dnsmasq, which doesn't seem to work, BTW.

---

### Post by darkod on 2012-10-17
OK, step forward, the gateway should be 10.10.0.1 as it is now.

I think I figured out what is missing. Since you said ufw is not enabled yet, and the POSTROUTING rule is part of ufw, there is nothing to do the masquerade part. That is needed for correct internet access.

So, first double check that the ip_forward is still active in /etc/sysctl.conf (I think that was the correct name of the file). The line was something like:
/etc/net/ipv4/ip_forward=1

You already mentioned you know how to do it, now just check if it's done.

Next, without activating ufw, you can do a quick test with one iptables rule:
```
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

After that try if the clients have internet access.

Don't forget, the POSTROUTING rule is part of the setup that forwards the traffic through the server. Without it, the traffic doesn't flow.

---

### Post by hawaiiman on 2012-10-17
> **hawaiiman said:**
> 10.04 LTS 64bit server plus gnome.
internet--adsl modem/router--eth0(WAN)--server--eth1(LAN)--switch--wired windows clients
* snip
 
/etc/default/ufw `DEFAULT_FORWARD_POLICY="ACCEPT"
 
/etc/ufw/sysctl.conf `net/ipv4/ip_forward=1' (uncommented)
 
Win clients can't get on the net. What did I do wrong?
 The line your quoting is from here, and appears as in op quoted.
In /etc/sysctl.conf  the line is also uncommented  ` net.ipv4.ip_forward=1'

---

### Post by darkod on 2012-10-17
> **hawaiiman said:**
> The line your quoting is from here, and appears as in op quoted.
In /etc/sysctl.conf  the line is also uncommented  ` net.ipv4.ip_forward=1'

OK, but you still need the POSTROUTING. Did you try it?

---

### Post by hawaiiman on 2012-10-17
Ineresting. The temp solution worked. I now have client internet access. From the client I can now ping 192.168.1.1 as well as google .com. Now to make it permanent...

---

### Post by darkod on 2012-10-17
Making it permanent depends on how you plan to proceed with the firewall. Since the server is behind a router, you can also use the router's firewall and not activate any firewall on the server.

If you decide to use firewall on the server and you use ufw, you will simply need to put the POSTROUTING statement in /etc/ufw/before.rules for example, as we already discussed on other threads.

If you decide to use iptables directly, then you will need to use iptables also for the firewall, not ufw.

---

### Post by hawaiiman on 2012-10-17
I don't have any way to make a firewall on the home modem router. It's been hardwired by the isp. So, the easiest way to go , since I plan to use ufw for firewall is to put the above forwarding statement just below the header in before.rules (?). Since it isn't an option and I'm not appending to the forwarding chain, should it not just go at the top just as given by you here?
I saw a rule elsewhere
# nat Table rules
* nat
: POSTROUTING ACCEPT [0:0]
-A POSTROUTING -o etho -j MASQUERADE
COMMIT
 
Does that look ok, I believe the format is from that tutorial. Do I need the -t in the front?

---

### Post by darkod on 2012-10-17
That is correct, you don't need the -t nat option when you use it inside before.rules since the *nat line does the same.

---

### Post by hawaiiman on 2012-10-17
Hmm, something about the forwarding isn't working with this approach. I read that ufw is enabled by default, but the firewall portion is not enabled, so forwarding there should work. I did `service ufw stop' then `service ufw start` which looked ok, then re-booted, re-booted the client, and now the client connection shows the name of the server and all the info in` ipconfig /all' reports just the same, I can't ping past 192.168.1.6(eth0) to the router, and no internet access.

---

### Post by darkod on 2012-10-17
No, ufw is not active by default. You do it with:
sudo ufw enable

That will activate it and also make it active on boot.

Note that you will need to configure the OUTPUT and FORWARD chains as ACCEPT in ufw so that outgoing and forwarded traffic is allowed. I think this was in /etc/default/ufw.

You can leave the INPUT as DROP for now.

PS. If you don't have physical access to the server be careful when activating ufw. You need to configure ssh rules first to let you in after you activate it. If you are in front of the server and typing on it, you can leave configuring the ssh rules for later.

---

### Post by hawaiiman on 2012-10-17
no internet access. ufw policy rules you mentioned were already"ACCEPT"

---

### Post by darkod on 2012-10-17
Then the firewall is blocking it somehow. This is a firewall issue now.

---

### Post by hawaiiman on 2012-10-17
Ok, I have added gufw and it shows firewall not enabled. Just for fun, I ran the iptables line, without changing anything, and got immediate internet, without a re-boot of either machine. Does this imply if I followed the forwarding instructions for iptables it might be the cure? The command for that is 
`iptables -t nat -A POSTROUTING -s 10.10.0.0/24 -o eth0 -j MASQUERADE'
added to `[FONT=Courier New]/etc/rc.local'[/FONT]

---

### Post by darkod on 2012-10-17
Yes and no. It should work, but it also depends what you plan to do with ufw, to use it or not. Because when ufw is enabled, on boot it flushes the iptables rules and establishes its own rules from the config files.

I am not sure if that can flush the POSTROUTING rule too. That's why I said, it's best to use only iptables, or only ufw, but not both. Which one you use is your choice. But mixing them can lead to unpredicted behavior.

If GUWF said that ufw is disabled, then you didn't have it enabled even if you thought you did. That might have been the reason it wasn't working since the POSTROUTING was inside before.rules. If ufw is not enabled, before.rules is not loaded.

Personally I would use iptables. ufw just looks simpler, but in reality will make things more complicated down the road.

But there is another important question that you didn't mention so far. The server is behind the ISP router. These routers usually have a firewall built-in. It doesn't matter whether you can control it or not, if it exists and is enabled, there already is a firewall between the internet and your setup.
Enabling a firewall on the server (whether iptables or ufw) will not do any good in that case. It can only complicate things. So, if you already have a firewall on the router, forget all about ufw, disable it, and just use that single iptables line to enable the forwarding. And that's it.

So, do you have a firewall in the router or not? Usually no ISP would leave you wide open, you would have had attacks by now surely if you were running without a firewall.

---

### Post by hawaiiman on 2012-10-17
I tried the iptables line in rc.local and immediately got things going even after a reboot. Yes, the first time i used gufw to enable the firewall, all internet was blocked, despite being set to allow all out and port 80 inbound. 
You are right about ufw making a mess. Right about the router too, I think. The router at school is very nice, a TENDA 300w which has a wireless "n" router also. It isn't hard wired, and has a fair amount of QOS functions available too. When we changed to the Tenda all the staff were pleased with the throughput.
OK, hey thanks so much for your help and especially patience.
I'm going to start with Samba file server tomorrow.

---

### Post by hawaiiman on 2012-10-17
Sorry, one other question, off topic. As this server is receiving dhcp, does that mean I won't be able to ssh to it without a service like no-ip?

---

### Post by darkod on 2012-10-17
On eth0 it's best the server to have a static IP outside of the ISP router dhcp range. This is so that the server IP on eth0 never changes.

If your ISP is giving you only dynamic public IP, yes, you will have to use a service like no-ip or dyndns so that you can reach the server from outside regardless of the public IP in that moment.

And on the router you will have to forward the ssh port to the server IP.

---

### Post by hawaiiman on 2012-10-17
That's what I thought. No chance of a static ip right now (expensive). I'll get something from one of the services. I already have the school router forwarding for ssh.

---

