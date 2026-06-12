---
title: "Exclude SSH from a VPN set as default interface"
date: 2012-12-02
forum: Networking &amp; Wireless
---

### Post by Luke Loughead on 2012-12-02
So I joined up with a VPN service for privacy and freedom's sake and I set it up using OpenVPN and network manager. I found, to my delight, that all traffic goes through the OpenVPN connection by default when it's turned on. COOL!

PROBLEM: I can no longer SSH into my computer. I normally SSH into my box by way of my regular net connection, since my dynamic DNS client runs on my router.

I have port forwarding set up on my router to send SSH traffic (on standard port 22) to my computer's static LAN IP. This used to work before I had OpenVPN turned on, now it doesn't.

I guess the problem is that the SSH traffic is being forwarded to my computer from my gateway, then trying to go from my computer to its Internet destination by way of tun0 (the OpenVPN device) since it's the default.

I've been puzzling with iptables and SNAT POSTROUTING rules but I can't figure it out. Last thing I tried was this:

```
root@host# iptables -t nat -A POSTROUTING -j SNAT -p tcp --dport 22 --to 192.168.5.1
```

I was attempting to just send any traffic on port 22 back to the gateway at 192.168.5.1, since LAN traffic seems to be excluded by default from the VPN connection. It didn't work.

So, I'm stumped. Anyone out there have any ideas as to how to solve this problem?

---

### Post by ahallubuntu on 2012-12-02
It's not clear exactly what you are trying to do.

Are you connecting to the VPN from INSIDE your home network (where the ssh server also lives)?  In that case, port forwarding isn't relevant and neither is a dynamic DNS, since you are trying to get to your local server without even going through the gateway.

Or are you trying to connect to your ssh machine remotely from the internet, where Dynamic DNS + port forwarding would apply?  Then the local iptables stuff is not relevant, but perhaps your VPN provider is then blocking port 22?

---

### Post by Luke Loughead on 2012-12-03
The latter. I am trying to connect to my home computer via SSH from the Internet.

The VPN service I use, ([BTGuard]("http://btguard.com/")), gives me a 10.x.x.x address, so it turns out I'm on their private subnet. This is why I feel like it's a NATing problem, not a blocked port, but I could be wrong. I had tried setting up ddclient on my computer itself but the IP address DynDNS got for my computer was one of BTGuard's gateways. I tried connecting via SSH and got a host that was definitely not mine.

Since my VPN service doesn't give me a public IP, I want to SSH directly from the Internet to my home computer through my regular ISP connection, but let all other traffic use the VPN. Would it be possible to do that?

---

### Post by ahallubuntu on 2012-12-03
If your Dyanmic DNS host isn't resolving to the correct IP when you are on the VPN, then it sounds like a DNS caching issue at the VPN provider.  Let's assume your ISP doesn't change your IP very often - twice a day at most?  Then you should be able to look up your DNS name without the VPN, then with the VPN, then (disconnect from VPN) without again.  Try "nslookup" .

Further, you can try the ssh just using your Dynamic IP, right?  I know it will change but again, probably not that often right?  By luck you should be able to ssh to it by IP before it changes again.  Can you do that when connected to their VPN?

I guess you could try using your own DNS (or say Google's) instead of the VPN provider's, when connected, if it turns out to be a DNS caching issue.

---

### Post by ahallubuntu on 2012-12-03
Oh, and I assume the reason you're not running your own OpenVPN server at home (in your router?) is because you want to block your IP?  That's the "privacy" you are concerned about?

---

### Post by Luke Loughead on 2012-12-03
Not specifically, but any improvement to privacy is welcome in an age of digital surveillance.

I believe the fact that the VPN service gives me an IP on 10.0.0.0/24 means that I would have to ask them to forward me a port for SSH, which I doubt is a favour they would do for one customer of many - at least not without paying a premium.

My goal is to be able to SSH tunnel from the Internet into my otherwise VPNed box. I feel like a technician who is better versed than I in networking, specifically with IPtables, would be able to do that, but the solution is out of my grasp at the moment. That's why I came to the Ubuntu community seeking help.

Does it feel like an achievable goal to you, ahallubuntu? Do you have any clues as to how to solve this puzzle?

---

### Post by Luke Loughead on 2012-12-03
> **ahallubuntu said:**
> If your Dyanmic DNS host isn't resolving to the correct IP when you are on the VPN, then it sounds like a DNS caching issue at the VPN provider.  Let's assume your ISP doesn't change your IP very often - twice a day at most?  Then you should be able to look up your DNS name without the VPN, then with the VPN, then (disconnect from VPN) without again.  Try "nslookup" .

Further, you can try the ssh just using your Dynamic IP, right?  I know it will change but again, probably not that often right?  By luck you should be able to ssh to it by IP before it changes again.  Can you do that when connected to their VPN?

I guess you could try using your own DNS (or say Google's) instead of the VPN provider's, when connected, if it turns out to be a DNS caching issue.

Sorry, missed this previous one. Yes, I'm subscribed to a VPN service. I'm trying to VPN from my home computer to their gateway, and they don't seem to give me my own public IPV4 address (understandable these days). My public IP shows up as one of their few end points (see: [https://btguard.com/support_vpn#question1](https://btguard.com/support_vpn#question1)).

I'm trying to set it up so I can switch on the VPN connection on my home computer when I want privacy, but leave it on and still get to it by SSH. I figure the best way to do that is to SSH through my home router instead of trying to in through BTGuard's end point. I know there are workarounds (e.g., set up an aliased IP and block all but port 22 on that, then set up routing rules and forwarding for that IP instead, set up a little VM for SSH, etc.) but they all seem like hacky ways to achieve something I'm pretty sure can be achieved directly. There's just something I'm missing here, and I thought it might be that the IPTables rule was wrong.

---

### Post by aeg1s on 2012-12-03
I have this EXACT same problem...  I've been trying to find a solution for weeks and have been on Freenode's #openvpn trying to get suggestions.  Nothing has worked so far though.

---

### Post by aeg1s on 2012-12-03
So I'm doing the same thing... trying to get to ssh into a machine on my network running OpenVPN client to a vpn service.  I found all the same problems you did... Activating the client cuts all my ssh connections from outside the network.  I did manage to get any machine on the LAN to be able to SSH into the machine, but not from outside.  While talking to folks on IRC in #openvpn on freenode I got a few different suggestions.  One was to source nat the traffic from the router so it all looked like it came from the router (on the same LAN).  I didn't like that solution and never really got that far with it.  The other was using -j MARK to mark certain packets in -t nat PREROUTING or mangle...  That's where I am stuck though...  I also thought about just opening up an ssh port in a VM as well or even on the router, but like you I think there has to be a better way to make this work.

---

### Post by Luke Loughead on 2012-12-03
Aha! Thanks, aeg1s! Good to know I'm not alone, at least.

I looked at marking the packets, too. I'd rather not have to do it that way. My router does run DD-WRT, and thus could do it with iptables, but I've had bad luck so far making any scripts work on that thing and I am currently thinking of changing the firmware on it anyway (current version is the VPN version because I originally wanted to use an OpenVPN client on the router itself, also with zero luck).

Anyway, I was thinking it should be possible to use iptables on the local machine to just send all traffic from port 22 back through the LAN's gateway instead of the OpenVPN tun device. Doesn't it seem like something that should, in principle, be simple to do?

Sometimes IPtables makes me feel like a gorilla trying to program a VCR.

---

### Post by aeg1s on 2012-12-04
Luke,

Same here...  I feel like I'm stabbing in the dark with iptables sometimes.  I switched from DD-WRT to OpenWRT earlier this year.  I ran DD-WRT for years.  OpenWRT starts to pay dividends when you have a USB on the router and can hang a large drive off of it.

Please let me know how you make out with this problem.  If I find any additional info I will be sure to post it on this thread.

---

### Post by aeg1s on 2012-12-09
Bump.

---

### Post by Luke Loughead on 2012-12-09
No luck thus far, and in fact all my messing around tangled up my network connections so bad I had to completely reset my IPtables setup.

Here's what I think is happening:

0. SSH traffic on port 22 comes into my home router from wherever I am on the Internet.

1. My router forwards the traffic to my computer.

2. Traffic back out goes through the primary gateway, which is set up to use my VPN connection (which is what I want normally, but not for SSH)

So, all I have to do is figure out how to send just the SSH traffic through my home router via eth0 and not the network on tun0.

Do I have that right?

---

### Post by aeg1s on 2012-12-11
For some reason it's not that easy as saying ignore port 22 and route it to eth0...

When I talk to people on #networking and #iptables in IRC they give me pretty complex examples of dual routed ISP's.

---

### Post by puyanera on 2013-04-08
Did you ever find a solution to this? I'm having the exact same problem.

This is the closest I could find that might answer it. I'll have a go when I get home and see if it works.
[http://superuser.com/questions/347534/ssh-server-cant-be-connected-to-when-vpn-is-turned-on](http://superuser.com/questions/347534/ssh-server-cant-be-connected-to-when-vpn-is-turned-on)

---

### Post by SeijiSensei on 2013-04-08
This isn't an iptables problem, it's a routing issue.

Suppose the remote SSH server is at 172.16.16.16, and your client is connected to an upstream router with address 192.168.1.1.  Add the following entry to the routing table:

```
/sbin/ip route add 172.16.16.16/32 via 192.168.1.1
```

Now traffic for the SSH server will be handed directly to your router and sent out over the Internet to the remote SSH server.

---

### Post by puyanera on 2013-04-08
Thanks for that SeijiSensei,

A couple of question though if you can as i'm fairly inexperienced with these things:

1) The ip address you mention 172.16.16.16, which ip address is that? Is that the external ip address that is assigned by the VPN service? Or some other ip address. Where would I find it? Also the /32 where does that come from?

2) If I apply this and it doesn't work is there a way to reverse the changes?

3) I also found this possible solution:
[https://bbs.archlinux.org/viewtopic.php?id=151870](https://bbs.archlinux.org/viewtopic.php?id=151870)

Which seems very similar to yours. Any comments on this solution? pros/cons differences?

Thanks

---

### Post by SeijiSensei on 2013-04-08
172.16.16.16 is just a placeholder for the public Internet address of the remote SSH server to which you would like to connect.  If you are trying to connect to a known SSH server, you should be able to determine its address.  If you only know its hostname and not its IP address, use the command "host host.example.com" replacing "host.example.com" with the name of the remote server.  For instance the command "host www.ubuntuforums.com" returns "www.ubuntuforums.com has address 91.189.94.12."

Basically we are creating a route specifically to reach that machine outside the tunnel.  When the VPN tunnel is active, the "default gateway" for your traffic usually becomes the remote end of the tunnel.  To reach the remote server with SSH you need to have a separate route so that traffic for that server is not pushed through the tunnel.

The /32 is a "[CIDR]("http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing#CIDR_notation")" address mask.  It's equivalent to the all-ones "netmask" 255.255.255.255.  Any individual host has a /32 mask.  A network subnet address like 192.168.1.0/24 has a mask of 255.255.255.0 (in binary, 24 ones followed by eight zeroes) and refers to all addresses between 192.168.1.0 and 192.168.1.255.

You can remove the route simply by running the identical command replacing "add" with "del".

The comments at Arch seem fairly similar to what I suggest here, yes.

---

### Post by puyanera on 2013-04-08
Thanks again for the help. So because my SSH Server is behind a server I used the comments on ARCH specifically:

```

ip rule add from 192.168.1.11 table 128
ip route add table 128 to 192.168.1.0/24 dev eth0
ip route add table 128 default via 192.168.1.1

``` 

That seems to have fixed the issue and now my box is connected to the 3rd part VPN server through which all the internet traffic flows but i'm finally able to SSH to the box from a remote location. Phew.

---

