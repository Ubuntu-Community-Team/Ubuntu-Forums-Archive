---
title: "pppoatm problem..."
date: 2005-12-24
forum: Networking &amp; Wireless
---

### Post by Ruskie on 2005-12-24
Hello everybody,
Got this problem I don't know how to solve.

Short version:
pon script gives me "error connect(8.35): unknown device" or something like that.

Detailed version:
I had a smooth working connection to my ISP that used PPP over Ethernet. I used pppoeconf, hacking to face some of its bug, and then pon dsl-provider and poff. All fine. Now I switched ISP, and this one uses PPP over ATM. I updated the router firmware and configured it to use the right protocol, which it does because in windows it now runs perfectly.
Then I tried to update Linux configuration, but couldn't make it work. Here is what I did:

replaced pppoe.so with pppoatm.so in /etc/modules (in which I didn't put the extension of course)
run update-modules

Changed dsl-provider script with the following:

noipdefault
defaultroute
user "myuser"
noauth
updetach
usepeerdns
plugin pppoatm.so
8.35

This script I got from a Speedtouch howto, but I believed they were hardware independent.
I double checked, and I am absolutely sure that 8 and 35 are my VPI/VCI numbers respectively.

Now when I run pon dsl-provider with root permissions (either being root, or sudoing) I get the error I mentioned "error connect(8.35): unknown device".
If I remove the line 8.35 I start getting weird carachter on the shell line and I have to close the shell to gain control.

What am I missing, and how may I configure pppd to use my Internet connection? Isn't there some pppoeconf-alike tool?

---

### Post by Ruskie on 2005-12-25
Just a quick note to tell that I've been unable to find anything but speedtouch configuration threads, nothing specific to setting up pppoatm, and I still can figure out how to make it work... Has anybody a clue?

Thank you very much in advance
Marco

---

### Post by mips on 2005-12-26
Ruskie,

Who is your ISP and what router brand/model do you use, web links to these please ?

If you have a router let it handle the PPPoA stuff so there is no need to run PPPoA stuff on the PC.

---

### Post by Ruskie on 2005-12-26
My provider is Tiscali ([www.tiscali.it](www.tiscali.it)) and my router is one I got bundled with my previous provider ADSL kit... It's called Siemens Gigaset, I believe, and its manufacturer should be dynalink ([http://www.dynalink.co.nz/]("http://www.dynalink.co.nz/")).

However, I already correctly configured the router to use pppoatm, infact I now go on internet in Windows... But I don't know how to tell Linux to use it... In particular, I should tell Linux two things: to use the address leased by the router (usually it's 192.168.1.1, but I want it to discover it by querying the dhcp server), and to use DNS servers provider by the provider, but I don't know how to do it.
Moreover I think (I will post the correction if mistaking) that pinging 192.168.1.0 (router's address) won't return results in Linux, so I don't know what to do...

Marco

---

### Post by Ruskie on 2005-12-26
Okay, I am almost done but there is something I still can't get.
I deleted pppoatm froum /etc/modules (not needed I think), configured the network interface via Control Panel in KDE to get manual address 192.168.1.2 (or dhcp, and it ends to this very same address).
Now I can "see" the router and log into its configuration tables. I still can't get outside, however. Is it enough to put router address into resolv.conf, or is there any other step to be taken?

Thank you very much
Marco

---

### Post by mips on 2005-12-28
Your **/etc/network/interfaces** file should contain these lines:
```
iface eth1 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1  ### Router address
```

Your **/etc/resolv.conf** file should contain these lines:
```
nameserver xxx.xxx.xxx.xxx   ### IP Address of Tiscal Italy DNS/Name server1
nameserver yyy.yyy.yyy.yyy   ### IP Address of Tiscal Italy DNS/Name server2
```

What output does the **route -n** command display ?

---

### Post by Ruskie on 2005-12-29
Hello Mips,
First of all, thanks for caring.
Strangely enough, I did nothing of what you said, yet network started working (I'm on Linux now).
Last attempt I did, when I wrote last message, was to configure the network card via KDE control panel, it  saw the router but didn't go out in the Internet.
I  set it to use DHCP, and put router's address both as gateway and as default nameserver.

Now that I rebooted, it started working. Can you tell me WHY???
My resolv.conf has:
```

search home
nameserver 192.168.1.1
```

My interfaces has
```

mapping hotplug
script  grep
map etho
...
...
auto eth0
iface eth0 inet dhcp

```

All in all, it seems "almost" as you said. I used dhcp, so no need to set explicit address and netmask. But does dhcp also automagically sets gateway too?
And, setting nameserver to my router, can't it be that it receives the query and automatically pass it to its real dns?

route -n output:
```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

---

### Post by mips on 2006-01-03
[QUOTE=Ruskie]...
Now that I rebooted, it started working. Can you tell me WHY???[/QUOTE]

I honestly dont know why. Maybe the network services needed a restart. Maybe it just needed a bit more time. I've noticed that if the cable going to the telco is unplugged from my router and I plug it back in it takes a while for my connection to be re-established.

[QUOTE=Ruskie]
All in all, it seems "almost" as you said. I used dhcp, so no need to set explicit address and netmask. But does dhcp also automagically sets gateway too?
And, setting nameserver to my router, can't it be that it receives the query and automatically pass it to its real dns?
[/QUOTE]

Yes, the DHCP server provides IP Address, Netmask, Default Gateway, Lease Time and whatever other information that is part of the scope.
Yes to your DNS question as well. On my machine I only have my loopback interface in my resolv.conf file. The problem is that some home broadband routers dont seem to gel well when it comes to a Linux box & DNS, for some odd reason they work happily with Win but not Linux so I usually suggest the individual just add them manually. You can add your routers address if it gets the DNS info dynamically from the ISP, you can also add the DNS server addresses from your ISP manually to your resolv.conf.

Like they say, many ways to skin a cat....

[http://www.dhcp.org/](http://www.dhcp.org/)
[http://www.dhcp-handbook.com/dhcp_faq.html](http://www.dhcp-handbook.com/dhcp_faq.html)
[http://www.quepublishing.com/content/images/0789728494/webresources/A010802.html](http://www.quepublishing.com/content/images/0789728494/webresources/A010802.html)
[http://www.rhyshaden.com/dhcp.htm](http://www.rhyshaden.com/dhcp.htm)

---

### Post by Ruskie on 2006-01-04
Well, many thanks for your help then! My system now is perfect. :)

Thanks
Marco

---

