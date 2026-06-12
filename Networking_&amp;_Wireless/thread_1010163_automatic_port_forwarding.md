---
title: "automatic port forwarding?"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by gnarf on 2008-12-13
I am running ubuntu server as a homeserver/webserver. I have my router setup to forward all ports from wan to my server. This works fine, I was wondering if there was a way to automatically have ubuntu make the rules for the router like Azureus can do. Sometimes I've lost power and when I do I tend to not turn on my linux box first, so the first computer I turn on gets dynamic ip of 192.168.1.100, then 101 etc. So if my rule were to make the linux box 192.168.1.100 and I turn it on second I need to manually forward the port to the new local IP. 

These are the rules that my router shows
```

        Action  	Name  	Source  	Destination  	Protocol

	Allow	to linux	WAN,*(ports)	LAN,192.168.1.100	(protocol)*,*(ports)
	Allow	Azureus UPnP 52282 UDP	LAN,192.168.1.100	WAN,*	UDP,52282
	Allow	Azureus UPnP 52282 TCP	LAN,192.168.1.100	WAN,*	TCP,52282
	Allow	Azureus UPnP 52282 UDP	WAN,*	LAN,192.168.1.100	UDP,52282
	Allow	Azureus UPnP 52282 TCP	WAN,*	LAN,192.168.1.100	TCP,52282

```
The Azureus ones are all automatic.

I don't want to just assign it a static local IP since sometimes I move to different locations temporarily and need a dynamic IP.

---

### Post by albinootje on 2008-12-13
Why don't you give your Linux-box a static ip-address ?
That sounds to me like the easiest and fastest solution.

---

### Post by gnarf on 2008-12-13
because sometimes I'm on a network that uses 192.168.1.x and sometimes is .0.x so a static IP doesn't always work

---

### Post by jrusso2 on 2008-12-13
You need UPNP and I don't think Linux does this but I am not sure if that changed.

---

### Post by sloggerkhan on 2008-12-13
I still don't see why your router can't get its address from the ISP via dhcp while the local network is static.

---

### Post by gnarf on 2009-01-03
let me try to explain this a different way, I'd like to have upnp request specific ports directed to my server, thus I don't need to open them all since it would be a pain in the butt to manually reconfigure them all, I travel to other locations where it would be handy to have upnp since automatic port configuration beats setting up routers which I'm not entirely familiar with, or may not have admin access to. I know upnp works with ubuntu since azureus requests ports just fine. Something where I can configure the specific ports I want, (ie 22,80 etc).

EDIT: doing some searching I found [_upnplib_](http://www.sbbi.net/site/upnp/index.html) I'll try that unless someone else has other ideas

---

### Post by gnarf on 2009-01-06
just because I hate finding results for problems I have but nobody bothered to give a solution.

I used [_MiniUPnP client_](http://miniupnp.free.fr/files/) 

I just used upnpc -r {port} {protocol} just upnpc will display the list of commands. seems to work well my only gripe so far is that the name on my rule list is "libminiupnpc" for every port. it'd be nice to be able to change them individually. (not even sure if I can do that though, only been up and running with this for a few minutes)

good luck to all who have this desire to use upnp to forward specific ports from your linux box without having to change router settings or mess with static IPs (though it isn't much of a mess)

---

### Post by ClockworkAvian on 2009-02-12
Thanks gnarf! I've been searching for this for a while, and dismissed miniupnp as a library, with no real commands. I'm glad you proved me wrong. :-)

I'm playing with VM's, and dealing with all the port forwarding is annoying, as I much prefer straight dhcp and upnp. Having this command enables me to have a machine nmap itself, and forward ports for services it offers, all nice and automated.

In case anyone is interested, but scared off by compiling, I'm attaching a deb file, compiled on Intrepid.

---

### Post by ClockworkAvian on 2009-02-12
Well, following up, a couple handy little scripts if anyone else is trying to forward all available ports. Note, requires nmap to be installed

To forward all active ports, you can use this command:
```
nmap $(hostname)|awk '/tcp|udp/,sub("/"," ") {print "sudo upnpc -r " $1 " " $2}'|bash -e;
```

To view the forwards, use 
```
upnpc -l
```

Finally, to remove the forwards,
```
nmap $(hostname)|awk '/tcp|udp/,sub("/"," ") {print "sudo upnpc -d " $1 " " $2}'|bash -e;
```

The "sudo" bit is only needed if you are trying to forward privileged ports (anything below port 1000, i think).
If you want to continuously scan, and NOT forward a particular port, throwing in ```
grep -v port
``` before bash should do it. 

Also note: If doing this kind of setup, make sure you nmap it's ip or hostname to find open morts: using localhost will forward non-public facing services (mysql, dns resolution, etc) that won't be accessible anyway.

---

