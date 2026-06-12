---
title: "Home network DNS problem"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by Jzz5 on 2011-02-04
Hello all,

I have a strange problem in my home network. I have several machines running several flavours of Debian and Ubuntu, behind a router. The router should act as DNS, but none of the machines can resolve the hostnames of the other machines. For example pinging the hostnames doesn't work. Pinging the IP addresses does, by the way. Most of my machines use DHCP (provided by the router), but some have a static IP (servers).

I think (but I don't know for sure) that the problem lies in the fact that the machines all have a different dnsdomain. Question is, how do I change that? I adapted the /etc/hosts file to suit the domainname, and this works, but to no avail. Furthermore after a reboot, the hosts file is reset, allthough I set the domainname in dhclient.conf.

Or am I in the wrong corner solving this?

Any suggetions?

Jzz

---

### Post by dmizer on 2011-02-04
If

1) Your router handles all DNS queries
2) Your router is set for DHCP
3) Your servers have manually assigned static IP addys on the client side (not in the router)

then

Your router doesn't know that your servers exist and therefore they won't show up in your router's DNS.

However, you indicate that no computers can ping by hostname, and you indicate that not all the computers have the same dnsdomain? Are you talking about DNS domain, or are you talking about NetBIOS? It may help if you give more information about your setup.

---

### Post by Jzz5 on 2011-02-04
> If

1) Your router handles all DNS queries
2) Your router is set for DHCP
3) Your servers have manually assigned static IP addys on the client side (not in the router)

then

Your router doesn't know that your servers exist and therefore they won't show up in your router's DNS.

However, you indicate that no computers can ping by hostname, and you  indicate that not all the computers have the same dnsdomain? Are you  talking about DNS domain, or are you talking about NetBIOS? It may help  if you give more information about your setup.     Ok, that's a quick reply! Thanks.

My setup is supposed to be an ordinary home network, but with a Server acting as fileserver. So I have a few desktops, a few laptops and a server.

I understand what you're saying about the static IP machine not showing up in my router's DNS, but it should be possible to ping the hostname of that machine, or is this impossible? Anyway, I should be able to ping hostnames between DHCP clients, am I right?

I don't exactly know what domain I'm talking about, or how to see that. But my /etc/hosts looks like this:

```
192.168.X.XXX    <hostname>.<domainname> <hostname>    # Added by NetworkManager
127.0.0.1    <hostname>.<domainname> <hostname>    localhost
::1    <hostname>.<domainname>    <hostname>    localhost6

```(Needless to say that this is from a DHCP machine.)

If it helps you. From your answer I get the feeling that I mixed some things up and changed too much, is that right?

When I type 'dnsdomainname', I get <domainname>.
When I type 'hostname -d' I get <domainname>.
When I type 'hostname --fqdn', I get <hostname>.<domainname>

So what is what and what should be what (what?)?

Thanks,
Jzz

---

### Post by dmizer on 2011-02-04
What is the make and model of your router? Have you tried manually entering the router's IP as DNS servers on all of your clients?

It should be possible to ping the hostname of any DHCP client on your LAN, but it would not be possible to ping the hostname of the server, since (to your router) it doesn't actually appear on the LAN.

---

### Post by Jzz5 on 2011-02-04
My router is a Linksys WRT610N, the router's IP address is in /etc/resolv.conf yes, if that's what you mean.

---

### Post by dmizer on 2011-02-04
> **Jzz5 said:**
> My router is a Linksys WRT610N, the router's IP address is in /etc/resolv.conf yes, if that's what you mean.

Well, I had a look at the manual for your router, and what you'll want to do with your file server is to use DHCP instead of static IP addressing. Make sure it gets an IP address directly from the DHCP server of the router. Then go to the router's settings page and add your server to the router's DHCP reservation list. You can find this setting under the "Network Setup" tab. This way, your server will always get the same IP address.

What I mean by "clients" is that you need to make sure that each computer on the network is using the router's IP as it's DNS server (not just the server).

Things should start working once both of the above points have been accomplished.

---

### Post by Jzz5 on 2011-02-04
Ok, understand that 'server' part, but that's not my biggest issue and I will follow your advice. But I have several machines using DHCP and they don't find each other as well. That's the biggest problem right now. As test, I have set my laptop next to my desktop and made sure that both have the same settings (as posted above). But they still don't find each others hostnames. So if I give my server a DHCP address, that is going to have the same problem, right?

edit:
yes, all of my clients have the router's IP address in resolv.conf

---

### Post by dmizer on 2011-02-04
> **Jzz5 said:**
> yes, all of my clients have the router's IP address in resolv.conf

Then you will need to look at the router settings to make sure that the DNS server is set up correctly. These settings should also be under the "Network Setup" section.

---

### Post by Jzz5 on 2011-02-04
Ok, will check that after the break (lunchtime in Holland)!

---

### Post by Jzz5 on 2011-02-04
In my router, I can just setup some IP addresses for external DNS servers, but I cannot set anything up for internal DNS...

Would it be a valid test if I boot 2 clients into Windows and try it from there? If 2 Windows clients can ping their hostnames, will that be a sign that DNS is working or does Windows use another system to resolve host names?

Jzz

EDIT: just found out that I CAN ping the hostname of my router (which is WRT610N). This is resolved to the IP address of the router and replied to. For what it's worth.

---

### Post by dmizer on 2011-02-04
> **Jzz5 said:**
> In my router, I can just setup some IP addresses for external DNS servers, but I cannot set anything up for internal DNS...

Would it be a valid test if I boot 2 clients into Windows and try it from there? If 2 Windows clients can ping their hostnames, will that be a sign that DNS is working or does Windows use another system to resolve host names?

Jzz

EDIT: just found out that I CAN ping the hostname of my router (which is WRT610N). This is resolved to the IP address of the router and replied to. For what it's worth.

In your router settings, you'll need to look for your DHCP client list and make sure that each IP address is given it's correct corresponding name on the network.

Alternatively, you can give permanent IP leases, as described in my earlier post, to all of your client computers (so that no client IP address changes), then you can edit each client's hosts file like so:

Using the following example IP addresses and hostnames:
Computer one = IP 192.168.1.101 hostname -> comp1
Computer two = IP 192.168.1.102 hostname -> comp2
Computer three = IP 192.168.1.103 hostname -> comp3

Your comp1 /etc/hosts file would look like this:
```
127.0.0.1	comp1
192.168.1.102 comp2
192.168.1.103 comp3
```

Your comp2 /etc/hosts file would look like this:
```
127.0.0.1	comp2
192.168.1.101 comp1
192.168.1.103 comp3
```

Your comp3 /etc/hosts file would look like this:
```
127.0.0.1	comp3
192.168.1.101 comp1
192.168.1.102 comp2
```

I would reserve that for a last ditch effort though ...

---

### Post by Jzz5 on 2011-02-04
> I would reserve that for a last ditch effort though ... 	

Yes, me too :p!

In my router, the client list is in good order. All clients are stated there with the given hostnames and given IP addresses. So the router receives the hostnames from the clients allright. This has been the case from the beginning though. What do you make of the fact that I can ping my routers hostname?

jzz

---

### Post by dmizer on 2011-02-04
> **Jzz5 said:**
> In my router, the client list is in good order. All clients are stated there with the given hostnames and given IP addresses. So the router receives the hostnames from the clients allright. This has been the case from the beginning though. What do you make of the fact that I can ping my routers hostname?

jzz

Can you post a screenshot of your router's client list with the hostnames? This information shouldn't be sensitive to post as long as it is not available to WAN access.

---

### Post by Jzz5 on 2011-02-04
[FONT=Arial]this failed, I'll give it another try...[/FONT][FONT=Arial][/FONT]

---

### Post by Jzz5 on 2011-02-04
[IMG]file:///tmp/moz-screenshot.png[/IMG]
that took a lot of trouble! Here it is!
jzz

EDIT:
took my screenshot offline. Feels better when the whole world cannot see my network specs...

---

### Post by dmizer on 2011-02-04
Well, I'm not sure about the android phones (I'd actually edit your phone ID so it's not so long anyway) but you should at least be able to ping desktop64 from laptop like so:
```
ping desktop64
```
or perhaps:
```
desktop64.local
```
Edit:
This may also be possible
```
desktop64.WRT610N
```

---

### Post by Jzz5 on 2011-02-04
I know it should work, but it doesn't. Let's test again, hold on....


...


Hold it!
The joos-desktop64.local runs the show! OMG! Why? Why does it need local and can I get rid of that? Anyway this is already a HUGE step forward, thanks for that!

Jzz

---

### Post by dmizer on 2011-02-04
> **Jzz5 said:**
> I know it should work, but it doesn't. Let's test again, hold on....


...


Hold it!
The joos-desktop64.local runs the show! OMG! Why? Why does it need local and can I get rid of that? Anyway this is already a HUGE step forward, thanks for that!

Jzz

What DNS servers are configured in your router for the WAN side of the connection? It may be that the problem is related to your ISP DNS servers (or OpenDNS if you're using it) forwards unknown DNS queries to a search page as a way of preventing [typo-squatting]("http://en.wikipedia.org/wiki/Typosquatting").

You may be able to complete local DNS queries without the ".local" suffix by changing your router's WAN DNS servers to some that do not have this (actually quite good) safety feature. Otherwise, I suggest just sticking with the .local extension. You'll get used to it pretty quickly.

---

### Post by Jzz5 on 2011-02-04
That makes sense. The DNS servers are the ones provided by my ISP, I never touched these settings. But as I think it over, the .local isn't a problem at all, as you say, I'll get used to it soon enough.

Can't believe it was that simple the whole time. We didn't change anything in the configurations, I'm sure this has worked all the time, I just didn't know about the .local addition... So it's the human factor again!!!

Thanks for the trouble!

Jzz

PS: I'll mark this as solved!

---

### Post by dmizer on 2011-02-04
> **Jzz5 said:**
> That makes sense. The DNS servers are the ones provided by my ISP, I never touched these settings. But as I think it over, the .local isn't a problem at all, as you say, I'll get used to it soon enough.

Can't believe it was that simple the whole time. We didn't change anything in the configurations, I'm sure this has worked all the time, I just didn't know about the .local addition... So it's the human factor again!!!

Thanks for the trouble!

Jzz

PS: I'll mark this as solved!

Always good to reach a resolution, and it's even better when there's learning involved. Glad to have helped. :)

---

