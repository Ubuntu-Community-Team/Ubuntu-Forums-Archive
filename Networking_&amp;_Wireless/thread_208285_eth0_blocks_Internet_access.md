---
title: "eth0 blocks Internet access"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by RichardR on 2006-07-03
I've searched and can't find a thread addressing this issue. If you can point to a thread it would be appreciated.

The NIC (eth0) works, because I can ping a LAN computer, thru a router, in either direction. 

But, as long as eth0 is active Firefox can't access the Internet because it can't find the url. Evolution returns an error message that it can't resolve the ISP address.

Netstat -rn shows the IP's are all properly set:
destination 192.168.1.0
sub-mask 255.255.255.0 
gateway 192.168.1.1 (router address) (ubuntu makes eth0 the default gateway by default?)

ubuntu = 192.168.1.100 (static and DCPH)

I've tried both static and DCPH to no avail. 

The firewall was tried both active and disabled with no affect.

Also I can ping my ISP if eth0 is active, but as stated above Firefox access is blocked.

Also tried manual configuration with ifconf. (This configuration of eth0 was lost when I rebooted.) Which begs the question can eth0 be set to activate on booting? A separate issue.

---

### Post by tonyr on 2006-07-03
Other questions to answer:
[LIST]
[*]are you sure your ISP is up?
[*]what are you using for DNS? ISP Supplied?
[*]Does your ISP require manual setup for internet access?
[/LIST]

---

### Post by RichardR on 2006-07-03
* are you sure your ISP is up?

Yes, Firefox finds any url. If eth0 is activated Firefox is is blocked. Also I can ping my ISP and get a response.

    * what are you using for DNS? ISP Supplied?
Yes.

    * Does your ISP require manual setup for internet access?
Question isn't relevant since I can use Firefox, if eth0 isn't activated.

One further point I'm using Dial-up, not DSL.

---

### Post by tonyr on 2006-07-03
[QUOTE=RichardR]
Yes, Firefox finds any url. If eth0 is activated Firefox is is blocked. Also I can ping my ISP and get a response.
...
One further point I'm using Dial-up, not DSL.[/QUOTE]

This is a little confusing.  Firefox can find the world w/o eth0, but doesn't if eth0 is
up?  I have to assume that your dial-up is through serial modem, so you have
two channels to the outside world, or what?  eth0 for LAN and serial modem for
ISP?

It sounds like Firefox is preferring eth0 as it's connection to the outside world over
PPP.  I'm not sure how to resolve that.

---

### Post by RichardR on 2006-07-03
Originally Posted by TonyR:
"I have to assume that your dial-up is through serial modem,..."

Correct

Posted by TonyR:
"two channels to the outside world, or what? eth0 for LAN and serial modem for ISP?"

One channel to WWW using serial modem, and one channel to eth0 for LAN, correct. They will not both work at the same time in ubuntu. I have no problem using windows 2K, both work fine at the same time.

---

### Post by tonyr on 2006-07-03
Here is something to try.  Type **about:config** into the Firefox URL bar.  I should
take you to a long list of configuration settings.  Scroll down to the one that says
```

network.dns.disableIPv6

```
and select that line.  If the **Value** is **false** right-click on that line to show a drop-down menu with some
selections.  Choose **Toggle[/B, which will set the [B]Value** to true.  I can't swear
that this will work for you, but it has fixed similar problems for others.  Yours may be
a more complex Network configuration problem.

Have you tried any other applications that require dns resolution?
What does this do?
```

dig +qr <your isp url> 

```  
and what is in the file **/etc/resolve.conf**?

---

### Post by RichardR on 2006-07-03
Tony:

1. I tried network.dns.disableIPv6, no help.

2. dns resolution, and what's in it. 

It all depends on the circumstances at any given moment. 

When I activate etho it rewrites the resolv.conf file. It deletes the dns addresses provided by my ISP 63.71.176.250 and 63.71.176.245. In place of these 2 addresses    eth0 substitutes 192.168.1.1 the gateway address of my router. At this point Firefox or Evolution can't resolve addresses.

Now when I use pon or wvdial to connect to the ISP both rewrite the resolv.conf file using  63.71.176.250 and 63.71.176.245 dns addresses. 

If eth0 is active and then disabled, I have to reboot. When I reboot and redial with pon or wvdial they both rewrite resaolv.conf and I can access the Internet with Firefox.

So the problem is pon/wvdial and eth0 are playing ping pong with my resolv.conf file.

---

### Post by tonyr on 2006-07-03
Make sure you are not still using DHCP on eth0 for IP address assignment, and look in
the file **/etc/network/interfaces** to see if there are any **dns** related lines
in the eth0 section, especially **dns-nameservers** and **dns-search**.

---

### Post by RichardR on 2006-07-03
Tony:

Here's what's in the interfaces file. The eth1 and eth2 don't make sense since I only have one NIC:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
_ _ _ _ _ _ _ _ _ _ _ _

That's all for the night. Have a good evening.

Richard

---

### Post by tonyr on 2006-07-03
I suspect that eth1 and eth2 are causing your problems, since they are invoking dhcp.

You can see if they are active and what their settings are by doing
```

sudo ifconfig -a

```

If eth1 and eth2 show up, you can probably avoid activation at boot from
**System->Networking**, or **System->Networking Tools**, or directly by editting 
**/etc/network/interfaces** and commenting out the eth1 and eth2 lines there 
(**#** as first character).

---

### Post by RichardR on 2006-07-04
Tony:

New twist but the same problem.

Using Knoppix and ubuntu live cd's I can't access the Internet with a browser, Firefox or otherwise. Further the problem extends to my second computer. On my second machine I also have SuSe 10.1 installed (HD), and the same problem. Can't access the Internet with a browser. 

So I went into the BIOS and disabled the eth0 (it's built into the mother board). As a side note my second machine is identical as to motherboard, except it has a PCI NIC. I can now access the Internet with a browser using both Knoppix and ubuntu live cd's.

I was reading a debain paper which stated that resolution can be achieved using either the hosts or the resolv.conf file. So the question is why is eth0 insisting on using the resolv.conf when the hosts file is available for LAN dns resolution? One answer is DSL, in my mind access to the internet  using DSL means:

route = eth0 to router to DSL modem, to internet to use ISP DNS servers stored in resolv.conf.

Disabling the NIC in the bios creates a problem with windows 2K pro because I lose my LAN connect which works fine.

As to your comment concerning ifconf -a, when connected to the ISP eth0 and ppp both appear with the proper addressess. I'll send the data if you want.

Richard

---

### Post by quert on 2006-07-04
Hi everybody,
I've got the same problem with my new installation. There was no respond from ff so I used my brain and checked MTU settings, and after changing to 1492 (was 1500), occured problem with "strage use of DNS" - some pages are found normaly others can be only acessed by digital ip adress :/
Under my old winxp the same DNS were working properly.

I'm using "something" like DSL connection through d-link router. My eth0 is runnig static ip adress.

---

### Post by alexus_fs on 2006-07-22
Maybe the problem is in the router.
It seems do not work properly with DDNS.
See:
[http://www.ubuntuforums.org/showpost.php?p=1286987&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1286987&postcount=1)

---

### Post by Matchless on 2006-07-22
Hi,
   This is a problem that has caused many headaches and the solution is to ensure that on a dialup PC both the eth0 and the dialler i.e. Kppp is properly set up. If a setting on eth0 is not correct then Kppp can fail to log in or you can log in but not open any web sites. There are different settings required if it is a standalone PC of if you have eth0 connected to another PC. 
The diagram here [http://ubuntuforums.org/showthread.php?t=215870](http://ubuntuforums.org/showthread.php?t=215870) should give you a guide as to the settings on both the dialler and eth0 and should get you on the air.

---

### Post by mips on 2006-07-24
You can't access the internet because you have a default route via eth0.

Show us your routing table with both connections running. You will probably have to add an addition route (not a default route).

route -n output please

From what I understand the Eth0 is your local LAN without internet and the dialup gives you internet access ???

If this is the case then the default route should point to your dialup connection and you will have to add anormal route for the LAN and remove that default route.

---

### Post by kaumochan on 2006-07-24
hv been facing similar problem. still not able to fix or know the actual problem.
However interestingly I am able to access internet when i open firefox as root or ping as root. Also as normal user, i can connect to websites if i put ip address instead of the www. name 

is this to do with permissions to drivers or devices?

---

