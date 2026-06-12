---
title: "how to add routes from the command line"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by davidmaxwaterman on 2009-08-10
Hi,

I have several routes added and I have been using the network manager to add them, but it would be much more convenient if I could add them from the command line - the tool used to add/edit the routes is not very convenient.

Can someone tell me where they are stored and if it is a simple matter of adding them with some cut&paste from one of the other connections?

Thanks,

Max.
(9.04)

---

### Post by dandnsmith on 2009-08-10
Have a look at the man pages for route, where there is quite a good description of the stuff you need, including how to see the existing routes, how to add/delete routes, and how to make them persistent.

---

### Post by davidmaxwaterman on 2009-08-10
> **dandnsmith said:**
> Have a look at the man pages for route, where there is quite a good description of the stuff you need, including how to see the existing routes, how to add/delete routes, and how to make them persistent.

Yes, route would work, but it's not quite what I'm looking for. I am trying to add the routes to the network manager from the command line, instead of adding them by clicking lots of times. I am fairly sure the man page for the route command doesn't have anything concerning the network manager. I will check the next time I'm on my linux system though (using my Nokia E90 atm).

Any idea where/how network manager stores the routes?

Max.

---

### Post by yota on 2009-08-10
The network manager stores routes in a file inside /etc/NetworkManager/system-connections.
There is a file for each connection which is structured like this:
> 
[connection]
id=Connection name
uuid=aaaaa-bbbbb-ccccc-ddddd-eeeeeeeee
type=802-3-ethernet
autoconnect=true
timestamp=0

[ipv4]
method=manual
dns=1.2.3.4;4.5.6.7;
dns-search=domain;otherdomain
addresses1=10.0.0.1;22;10.0.0.254;
[B]routes1=192.168.0.4;32;192.168.0.1;0;
routes2=192.168.0.5;28;192.168.0.1;0;[/B]
ignore-auto-routes=false
ignore-auto-dns=false
never-default=false

[802-3-ethernet]
speed=0
duplex=full
auto-negotiate=true
mac-address=aa:bb:cc:dd:ee:ff
mtu=0


the lines containing the routes information are in bold.

Hope this helps!

---

### Post by davidmaxwaterman on 2009-08-11
> **yota said:**
> The network manager stores routes in a file inside /etc/NetworkManager/system-connections.
There is a file for each connection which is structured like this:


the lines containing the routes information are in bold.

Hope this helps!

Well, it sounds very promising, but when I look in that directory, I don't find any files at all, despite already having set up several routes for several connections. It seems like it doesn't store them there.

Am I missing something?

Max.

---

### Post by yota on 2009-08-12
Maybe it was my fault, I took for granted that the connection was system-wide.

If instead it was per-user then NetworkManager stores it in gconf (see the attachment) which, on the filesystem, is a tree of xml files under the .gconf directory under the user's home directory.

The path is "~/.gconf/system/networking/connections/" where there is a %gconf.xml describing all connections and, in the appropriate one, there's a section like this for the routes:
> 
<entry name="routes" mtime="1250063996" type="list" ltype="int">
                <li type="int" value="67305985"/>
                <li type="int" value="32"/>
                <li type="int" value="0"/>
                <li type="int" value="0"/>
        </entry>

From the command line, instead of directly editing the file, you should use the gconftool (or gconftool-2) command. Have a look at man for details.

---

### Post by davidmaxwaterman on 2009-08-13
> **yota said:**
> Maybe it was my fault, I took for granted that the connection was system-wide.

If instead it was per-user then NetworkManager stores it in gconf (see the attachment) which, on the filesystem, is a tree of xml files under the .gconf directory under the user's home directory.

The path is "~/.gconf/system/networking/connections/" where there is a %gconf.xml describing all connections and, in the appropriate one, there's a section like this for the routes:

From the command line, instead of directly editing the file, you should use the gconftool (or gconftool-2) command. Have a look at man for details.

ok! nice one.

although, it didn't work :/

By that I mean that I did manage to add the routes, and my 'new' connection now seems like it has the same routes as my other ones, but the routing doesn't work.

I guess this issue is now a different one, but since you've been so helpful, I wonder if you would 'bring this baby home' so to speak.

I think I've seen this before, but I don't know how I solved it before.[1]

Basically, I want to add routes to certain hosts and nets through my wlan0 if, so that when I add a vpn connection on top, the hosts/nets I've added still go through the raw wlan0 if, rather than the vpn.

For example, when I bring up the wlan0 without any additional routes, I get :

```
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
```

and with an added host, I get :

```
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
66.111.4.51     0.0.0.0         255.255.255.255 UH        0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0
```

After this, I would enable the VPN and get some more routes, but the above would remain and cause those routes to not go through the VPN.

However, at this point (without the VPN), I would expect to be able to connect to 66.111.4.51, and yet, no :

```
$ telnet mail.messagingengine.com imap
Trying 66.111.4.51...
Trying 66.111.4.52...
telnet: Unable to connect to remote host: No route to host

```

If I :

```
sudo route del -host 66.111.4.51
```

then I can :

```
$ telnet mail.messagingengine.com imap
Trying 66.111.4.52...
Trying 66.111.4.51...
Connected to mail.messagingengine.com.
Escape character is '^]'.
* OK IMAP4 ready
^]

telnet> quit
Connection closed.

```

(yes, I have .52 rerouted too)

What I'm trying to do works fine for the other connections, but not for this one. I don't have access to the other networks at the moment, so I can't tell what the difference might be.

Any ideas why the routing isn't working in this case?

Max.
[1] I think it was something to do with using the gw address to route rather than the device, but that was when I wasn't able to add them using network manager and I was doing it manually with a script.

---

### Post by yota on 2009-08-13
Mhhh...
I suppose the problem is that
```

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
66.111.4.51     0.0.0.0         255.255.255.255 UH        0 0          0 wlan0

```
means that you should find 66.111.4.51 directly on link in the same subnet of wlan0 (which is not the case...)

If I've understood correctly what you are trying to accompish probably you should instead add:
```

route add 66.111.4.51 **gw 192.168.1.1** wlan0

```

Let me know if it works!

---

### Post by davidmaxwaterman on 2009-08-13
> **yota said:**
> Mhhh...
I suppose the problem is that
```

Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
66.111.4.51     0.0.0.0         255.255.255.255 UH        0 0          0 wlan0

```
means that you should find 66.111.4.51 directly on link in the same subnet of wlan0 (which is not the case...)


I think think that can be right because it does actually work on other WLANs, and that IP address is for a mail server somewhere in New York City (iirc).

> 
If I've understood correctly what you are trying to accompish probably you should instead add:
```

route add 66.111.4.51 **gw 192.168.1.1** wlan0

```


...on the other hand, that line does indeed 'ring a bell' as something that did work on problem WLANs. Unfortunately, this solution wouldn't work for the ones that were working just using the device, and, at the time, I was looking for a general solution that would work from a script.

> Let me know if it works!

However, now, since I can 'easily' add these routes using Network Manager, perhaps it is a more viable solution :) I'll give it a try later.

Thanks!

Max.

---

### Post by davidmaxwaterman on 2009-08-13
> **davidmaxwaterman said:**
> 
However, now, since I can 'easily' add these routes using Network Manager, perhaps it is a more viable solution :) I'll give it a try later.


Indeed, this does work; but I don't know why.

When I added the other routes I did it using the Network Manager (since I didn't know how to do it any other way).

To add the routes, I had to enter '0.0.0.0' as the gw, which was the only way I could find to make it 'stick'. I didn't see how I could enter a gateway, since I didn't know what it would be until the DHCP server had set it. If I have control over the access point and DHCP server, then I can be fairly sure the gateway address won't change; but this isn't true of all the access points I use, so specifying a gateway address would introduce a point of unreliability.

This is all a little academic at this point, but I'd like to understand the issues. If you have time to answer them, I'd love to know :)

In any case, thanks for solving the immediate problem :)

Actually...now I'm thinking of doing this 'the other way around'. IE, instead of specifying what routes I want don't want to go through the VPN, perhaps I should try to specify the networks for which I need to use the VPN. I can probably get these networks from the proxy.pac file. Hrmmm...perhaps I'll give that a try at some point.

Max.

---

### Post by yota on 2009-08-14
> **davidmaxwaterman said:**
> Indeed, this does work; but I don't know why.

Well I don't see any mistery here: as you said 66.111.4.51 is "somewhere in New York City" and not in the same network segment of wlan0, so it can be reached only by going through the gateway...
> 
In any case, thanks for solving the immediate problem :)

You're welcome! :)
> 
Actually...now I'm thinking of doing this 'the other way around'. IE, instead of specifying what routes I want don't want to go through the VPN, perhaps I should try to specify the networks for which I need to use the VPN.

I agree that this can be the best approach, you can even set hosts to be routed through VPN independently of which specific connection you are using at a specific time.
What are you using VPN for? Are the hosts you plan to reach via VPN a well defined and limited list?

---

### Post by davidmaxwaterman on 2009-08-14
> **yota said:**
> Well I don't see any mistery here: as you said 66.111.4.51 is "somewhere in New York City" and not in the same network segment of wlan0, so it can be reached only by going through the gateway...


I guess I should have said that I don't know how it works when I just route through the device...on other wlans...but on this one I need to specify the gateway.

For example, my old script used to do this when the there's a VPN :

```
route add -net 66.111.4.0/24 gw $wlanIP
```

where $wlanIP is the gateway address

and when there's no VPN (ie I'm using the network at the other end of the VPN directly via eth0) :

```
route add -net 66.111.4.0/24 dev wlan0
```

> 
I agree that this can be the best approach, you can even set hosts to be routed through VPN independently of which specific connection you are using at a specific time.
What are you using VPN for? Are the hosts you plan to reach via VPN a well defined and limited list?

I'm not sure you could say 'well defined', and they could change outside of my control.

---

