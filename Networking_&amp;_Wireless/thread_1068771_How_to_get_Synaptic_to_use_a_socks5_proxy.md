---
title: "How to get Synaptic to use a socks5 proxy"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by nr91 on 2009-02-13
Hi,

First of all:  I am a newbie to Ubuntu/Linux.

As I am behind a proxy at work I use an ssh tunnel for my traffic to internet.  In Firefox this is no problem as I add a socks5 127.0.0.1:3000 in the settings.  In Synaptic I cannot do this, as I only have http/ftp as options.

Anyone know how I can force Synaptic to use my socks5 ssh tunnel?

cheers,
nr91

---

### Post by kestrel1 on 2009-02-13
If you know the proxy settings i.e. IPaddress: port number
you can add these to the network proxy. If memory serves, this should be under: System -> Preferences -> Network Proxy
Using a different Linux at present, but can check in a little while if that is not correct.
Anyway, if the IP & port are set correctly it should work. Mine does.
You can then set Firefox to use the proxy instead of ssh tunnel

---

### Post by nr91 on 2009-02-13
Hi,

I don't want to use the proxy as they monitor the traffic.  I want my internet traffic to go through my SSH tunnel.  As said, for Firefox (and other programs that can use socks) no problem, but I cannot find a way for Synaptic to do this.

Picture1 is a screenshot of the settings that work with eg Firefox.  Picture2 is a screenshot of the settings of Synaptic and that obviously doesn't work.


cheers,
nr91

---

### Post by nr91 on 2009-02-13
If I put Synaptic on 'Direct connect to the internet', will it be using port80 then?  Is so, I can try to get all traffic over port80 through the sst tunnel.  But I guess I will get the "Privileged ports can only be forwarded by root" error.

Mmm let me try this.

---

### Post by kestrel1 on 2009-02-13
Why is it so bad to use the proxy. Would you get in trouble for using it. So what if they monitor the traffic, are you doing something you shouldn't?
I am a Network Administrator, so I couldn't condone the use of anything that might create a potential security risk.

---

### Post by nr91 on 2009-02-17
The problem is that I get:

 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  

I filled out the proxy ip + authentication credentials.  With the same credentials and proxy, Firefox works.

---

### Post by kestrel1 on 2009-02-17
Did you reboot before trying?
If the proxy & credemtials are filled out set to be system wide it should work, but a reboot may be required just to set everything in place.

---

### Post by quequotion on 2009-03-06
I am having the same problem.

In detail, connecting to the internet through an SSH tunnel which is a Socks5 proxy (on an iPhone but that doesn't really matter).

I tried tsocks, but that won't work as it has no way to get dns. (there was an option for dns through http at compile but that doesn't really do anything useful)

Firefox works with the socks5 proxy because it is able to forward dns requests on its own.

Is there a way to set up Synaptic to not only connect through a socks5 proxy, but forward dns requests as well? Is there a superior way to set the system-wide proxy setting for this? (and get socks unaware applications to use a system-wide socks5 setting)

---

### Post by quequotion on 2009-03-07
I may have found a way.

A program called Proxychains, which does what tsocks claims to do but much better.

[Debs for Intrepid](http://www.getdeb.net/app/Proxychains) (only source is available on [home page](http://proxychains.sourceforge.net/) and repository version is old)

My example:

I route through the sock5 server by ssh (there are many other ways to connect to the proxy):
```
$ ssh -D 1080 -fN root@192.168.1.3
```
(connects 192.168.1.3 shh (port 22) to localhost port 1080 as root; will ask for 192.168.3's password; some may not require user/pass authentication)

I then edit /ect/proxychains.conf at the end like so:
```
[ProxyList]
# add proxy here
# defaults set to "tor"
# socks4        127.0.0.1 9050
socks5 127.0.0.1        1080
```
(connects to 127.0.0.1 port 1080

A good test is to try proxyresolv, included with proxychains, to resolve something like [www.ubuntu.com](www.ubuntu.com).
```
$ proxyresolv www.ubuntu.com
```

If it works, you can start synaptic or anything else through proxychains:
```
$ sudo proxychains synaptic
```
(this is the most important part, the rest may very depending on your setup)

If it doesn't work:
Verify your port settings: the ssh tunnel is normally 22, while the socks5 connection is usually 1080 (it isn't the only option).
Don't use my ip settings: unless you happen to have a very similar setup, you probably need to change the ip to something relevant.

If you're using an iPhone, there's one extra step to get around its contrived protocols: open a webpage in the iPhone's Safari. You may have to periodically repeat this step if the iPhone mysteriously disconnects your socks5 proxy. The ssh tunnel seems to always remain open.

Only partially related:
I am not connecting to the iphone directly from my Ubuntu pc, as much as I'd like to.  The iPhone is connected to a windows XP laptop through a utility called "iTunnel.exe" This program opens a connection between the iPhone's tcp port 22 and the pc's tcp prot 22 **through a usb connection** and I just have no idea how that works.  The effect however, is that port 22 on the pc *is* port 22 on the iphone, so my Ubuntu pc makes a socks5 proxy connection using the pc's IP address and doesn't know the difference.
________________________________________________________
::UPDATE::

i found an "itunnel" for linux and no longer need to connect through a windows pc on the local network (although the old way is more stable)
also, proxychains inexplicitly stopped working one day and never came back.... i didn't change the configuration but i restored it from a back up anyway and nothing happened.. changing it later didn't help either... it's just dead... Fortunately, there's yet ANOTHER socks5 wrapper for linux, "socksify" which works a little better. In all cases this connection is buggy due to the iPhone itself as much as the messy code that itunnel and sockify are made of.

---

