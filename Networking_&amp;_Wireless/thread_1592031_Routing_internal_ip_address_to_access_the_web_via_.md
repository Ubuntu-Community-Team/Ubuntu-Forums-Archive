---
title: "Routing internal ip address to access the web via external ip"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by manilodisan on 2010-10-10
Don't know how stupid the title sounds but it's all I could squeeze out.

So I'm having an ubuntu box with 10 external ip addresses on my eth0. I have installed openVPN to allow some of my "road warriors" to connect to it while traveling (tutorial used: [http://www.ossramblings.com/configuring_openvpn_ubuntu_hardy](http://www.ossramblings.com/configuring_openvpn_ubuntu_hardy)). Everything works fine, I can connect to it with the generated keys and certificates, but I need to do one more thing and this one is crucial from some reasons. I want to assign to each of my "road warriors" an external ip from the list of 10 I have on that box. I want to have control over which ip gets assigned to what connected client.

By assigning an external ip I mean...client connects to the VPN, goes to showip.com or whatever else website which lists your current ip and sees the new IP that I've assigned so all of his applications go out on the net using that ip address.

I've successfully managed to assign a fixed internal ip such as 10.8.0.6 to a specific client and, I guess, all I have to do now is figure a way of making that 10.8.0.6 go out on the net using 98.xx.146.11 for example.

Is there a way of making that? Maybe with iptables or something?

Many thanks.

---

### Post by SeijiSensei on 2010-10-10
> **manilodisan said:**
> Is there a way of making that? Maybe with iptables or something?

Yes, but first you'll need to turn on IP forwarding in the kernel if you haven't already done so.  In /etc/sysctl.conf, look for the "net.ipv4.ip_forward" entry and make sure it's set to one.  Then reboot.  You can check whether forwarding is enabled by running

```
sudo cat /proc/sys/net/ipv4/ip_forward
```

If it returns zero, forwarding is disabled (which is the default in most modern distributions like Ubuntu).

Next you'll need to add a couple of lines to your existing iptables firewall.  First, check to make sure the default policy for the FORWARD chain is set to DROP at the beginning of your ruleset.

```
iptables -P FORWARD DROP
```
With forwarding enabled, you need to have a rule like this in iptables to limit forwarding only to those packets you've specifically permitted.  If, however, this box is routing traffic for internal network users as well as the VPN users, you'll need to include these rules as well:

```
iptables -A FORWARD -s w.x.y.z/mask -j ACCEPT
iptables -A FORWARD -d w.x.y.z/mask -j ACCEPT
```

where w.x.y.z/mask should be replaced by the address block of your local network.  Otherwise your local users won't be able to talk with other local devices like servers.

In order to assign each person to a separate external IP (seems like overkill to me), I assume you've set up virtual interfaces on the external interface (let's call it eth0) like this:

```
ifconfig eth0:0 98.xx.146.11
ifconfig eth0:1 98.xx.146.12
[...]
ifconfig eth0:9 98.xx.146.20
```
Now in your iptables rule set, you'll need to have rules like these:

```
# allow traffic from the VPNs
iptables -A INPUT -s 10.8.0.0/24 -j ACCEPT
# forward reply packets in response to requests from us
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

```
Finally, you'll need a set of rules like these, one for each address:

```
iptables -A FORWARD -i tun0 -o eth0:0 -j ACCEPT
iptables -t nat -A POSTROUTING -i tun0 -o eth0:0 -j SNAT --to 98.xx.146.11
```
replacing tun0, eth0:0, and the external IP address for each pairing of VPN addresses and external IPs.

As I said this seems like overkill to me.  Why not simply have all the VPN users share a single outbound address like this?

```
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -j SNAT --to 98.xx.146.11

```
which will map the entire 10.8/24 subnet to a single outbound address?

By the way, if you look around the web, you'll see tutorials on NAT that use the -j MASQUERADE option instead of SNAT.  That works well on routers with a single internal interface and a single external interface.  However it can lead to trouble if you have more than two interfaces because traffic between, say, your road warriors and your local network users will also be masqueraded.  You probably don't want that.  Plus if you really do need to assign each VPN user a separate external IP, you'll need to use SNAT to do the pairings.

---

### Post by manilodisan on 2010-10-10
Thank you for your great help so far. I tried your commands and there are some errors reported:
```

iptables -A FORWARD -i tun0 -o eth0:0 -j ACCEPT
Warning: weird character in interface `eth0:0' (No aliases, :, ! or *).
```

And the following:
```
iptables -t nat -A POSTROUTING -i tun0 -o eth0 -j SNAT --to 98.xx.146.11
iptables v1.4.4: Can't use -i with POSTROUTING

Try `iptables -h' or 'iptables --help' for more information.
```


I must admit I'm a total noob at networking, this was assigned to me so I must do it, pray for help etc.

Also, assigning a dedicated (controlled) ip per client is crucial.

---

### Post by SeijiSensei on 2010-10-10
> **manilodisan said:**
> Thank you for your great help so far. I tried your commands and there are some errors reported:
```

iptables -A FORWARD -i tun0 -o eth0:0 -j ACCEPT
Warning: weird character in interface `eth0:0' (No aliases, :, ! or *).
```

Also, assigning a dedicated (controlled) ip per client is crucial.

Well, I was afraid of that.  I had hoped iptables would let you reference the virtual interfaces, but in the back of my mind I recalled that it might not.  That pretty much rules out pairing VPN and external addresses via interfaces.  

```
iptables -t nat -A POSTROUTING -i tun0 -o eth0 -j SNAT --to 98.xx.146.11
iptables v1.4.4: Can't use -i with POSTROUTING
```

Same as above.  POSTROUTING only works with the output (-o eth0), so again pairing a VPN interface like tun0 can't work.  Something like this might work, though:

```

iptables -A FORWARD -s 10.8.0.0/24 -o eth0 -j ACCEPT
iptables -t nat -A POSTROUTING -s 10.8.0.1 -j SNAT --to 98.xx.146.11
iptables -t nat -A POSTROUTING -s 10.8.0.2 -j SNAT --to 98.xx.146.12
etc.

```

> I must admit I'm a total noob at networking, this was assigned to me so I must do it, pray for help etc.

Makes me wonder about the people in charge at your establishment.  They probably figured you'd just push a button or something, and it would all magically work.  This isn't a easy problem to solve at all.  Let's us know how it's going and good luck!

---

### Post by manilodisan on 2010-10-10
You're my hero today @SeijiSensei haha. That worked! Is there anything I should be aware of when using such methods?
> Makes me wonder about the people in charge at your establishment. They probably figured you'd just push a button or something, and it would all magically work. This isn't a easy problem to solve at all. Let's us know how it's going and good luck!

I'm a PHP programmer myself but this is totally out of my league unfortunately yes.

---

### Post by SeijiSensei on 2010-10-11
Thanks.  I'm happy I could help.  I'll send you my Swiss bank acccount number by PM.  You can deposit US$1,000,000 there :D

On a more serious note, have you tested to make sure the internal/external IP pairing actually works as they're supposed to do?  One simple test is to visit [http://www.whatsmyip.org/](http://www.whatsmyip.org/) from each of the 10/8 addresses and make sure it reports a different external IP each time.

---

### Post by manilodisan on 2010-10-12
> **SeijiSensei said:**
> Thanks.  I'm happy I could help.  I'll send you my Swiss bank acccount number by PM.  You can deposit US$1,000,000 there :D

On a more serious note, have you tested to make sure the internal/external IP pairing actually works as they're supposed to do?  One simple test is to visit [http://www.whatsmyip.org/](http://www.whatsmyip.org/) from each of the 10/8 addresses and make sure it reports a different external IP each time.

Yes, it works fine however, I implemented a user/pass authentication and now it stopped working so I'm back at the beginning.

If you're good with openVPN and networking and want to make some money please PM me so I can get this over my back once and for good. Don't mind sharing some $ from this project.

---

