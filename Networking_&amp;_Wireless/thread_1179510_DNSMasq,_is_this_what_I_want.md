---
title: "DNSMasq, is this what I want?"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by tomsimmons on 2009-06-05
I'm trying to set up a light weight server, which will also be used for some desktop work, so I've installed 9.04 desktop.

The machine is sat behind an ADSL Router that is in standard NAT configuration.  I started with DHCP and BIND9, and tried GAdmin-DHCP/BIND and Webin to configure it, but couldn't find any clear guide that wasn't based around me having the machine as a internet facing DNS unit, ie everything was to commercial.

While trying to find a guide I kept hearing about DNSMasq, but no info on how to install/configure it, well excluding a single page on Ubuntu documentation that seems to suggest that you need to install Network Manager or something because of the same name?!

I'm not sure if this is what I want, some posting seem to suggest it's just for internet sharing others refer to it as a more complete DHCP/DNS/Routing setup (though lighter weight than DHCP/BIND).

Can anyone:

[LIST=1]confirm that it's what I'm looking for[/LIST]
[LIST=1]shed any light on how to install it (do I need to remove Network manager or just install the other bit that listed in Synaptic[/LIST]
[LIST=1]provide any guidance on configuring it, looks like the Webmin module for it is out of date/abandoned[/LIST]

Thanks for any help,


Tom

Edit...
I forgot to mention, I will be adding a mail server, and Samba to this machine - just in case that rules out DNSMasq.

---

### Post by Iowan on 2009-06-05
My router (Freesco) used DNSMasq to provide DHCP and caching DNS server.  It seemed to work pretty well, but because it came installed on the system, I didn't have the need (or opportunity) to get acquainted with it's setup.

---

### Post by tomsimmons on 2009-06-05
Just to clarify what I mean by...

> **tomsimmons said:**
> shed any light on how to install it (do I need to remove Network manager or just install the other bit that listed in Synaptic

[https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

Does this mean I need to remove the dnsmasq-base that is already marked as installed in Synaptic, or do I simply add the dnsmasq that isn't already installed?

Tom

---

### Post by bab1 on 2009-06-06
> **tomsimmons said:**
> Just to clarify what I mean by...



[https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

Does this mean I need to remove the dnsmasq-base that is already marked as installed in Synaptic, or do I simply add the dnsmasq that isn't already installed?

Tom

Add DNSMasq.  The base is just enough to run as an app, but not as a sever.  When you install DNSmasq on earlier versions of Ubuntu it adds the base in too.

FYI -- this is from the description of DNSmasq-base :```
This package contains the dnsmasq executable and documentation, but
not the infrastructure required to run it as a system daemon. For
that, install the dnsmasq package.
```

Edit:  After you do the install, read the [_**man page**_]("http://thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html") for DNSmasq.  It is very easy to read and explains all the config needs.

---

### Post by tomsimmons on 2009-06-06
Thanks for clarifying that, I've now installed the daemon bit.

So to give an over view:

ADSL router is at xxx.xxx.8.1
Ubunutu server at xxx.xxx.8.10
Variety of Windows, Linux and PDA devices using DHCP

The server is fixed IP, it has an entry under Network Connections stating the DNS is at xxx.xxx.8.1, the router.  This allows me to access the web on it.  The server is the machine running DNSMasq.

I've configured the DHCP in DNSMasq, and it has handing out IP's to machines correctly.  However initially they were unable to access the internet.  Using ipconfig under Windows I noticed the default gateway was set at xxx.xxx.8.10 (the server).  Using dhcp-option 3 (router) I specified xxx.xxx.8.1, now internal machines can see the internet.  I assume this was the right thing to do?

I'm now left with one problem, well one that I know of!

I can obviously ping any machine by IP, but the client machines cannot ping the server (called server) by name.  They can ping each other by name, though initially I'm sure they couldn't.  The server is unable to ping anything by name, well other than itself (127.0.0.1).  So it seems my DNS is not working correctly.  From ipconfig I can see that the DNS server is correctly set to xxx.xxx.8.10.

Do I need to set this line in the dnsmasq.conf file...
```
# Add local-only domains here, queries in these domains are answered
# from /etc/hosts or DHCP only.
#local=/localnet/
```

Thanks for your help.


Tom

---

### Post by Aearenda on 2009-06-06
I found that dnsmasq hands out 127.0.0.1 as it's address instead of the external one if configured to use the local hosts file. I separated the hosts file dnsmasq uses and put an entry in there for itself with the correct static address. This is necessary because the address is static (so never registered), and accounts for why your clients can't ping the server by name.
I also found that for the dnsmasq server to itself use dnsmasq, it was necessary to set /etc/resolv.conf pointing at itself. I listed the upstream DNS servers in the dnsmasq config.
The local-only line is useful if your client machines know they belong to a local domain, and prevents delays while the upstream servers are asked about a domain that is not registered.

---

### Post by tomsimmons on 2009-06-06
Thanks

So I modified resolv.conf from
```
nameserver xxx.xxx.8.1
```
to
```
namerserver 127.0.0.1
```

I also modified dnsmasq.conf to have
```
server=xxx.xxx.8.1
```
which is the router (upstream name server).

This all means that there server can now ping clients by name.  However from the window machine I still cannot ping the server by name, and from an Ubuntu client I can ping it by name, but the returned IP is 127.0.1.1.  This value I can see as the second line in my hosts file on the server, the first line being 127.0.0.1.

From the following link...

[http://thekelleys.org.uk/dnsmasq/docs/setup.html](http://thekelleys.org.uk/dnsmasq/docs/setup.html)

I don't understand what they mean about the "Automatic DNS server configuration with DHCP" and the "Integration with DHCP".  My server can see the clients by name, so it would seem this is working?

I don't quite follow what you mean by the local setting I'm afraid.  I have the domain and expand-hosts specified in the dnsmasq.conf, so should I add this domain to local, to stop any internal dns requests being sent further upstream?

Tom

---

### Post by bab1 on 2009-06-06
> **tomsimmons said:**
> ...
I don't understand what they mean about the "Automatic DNS server configuration with DHCP" and the "Integration with DHCP"...

You do not use a static file (/etc/hosts) if you are running DHCP along with DNS services.

I suggest you read the example dnsmasq.conf located [**_here_**]("http://thekelleys.org.uk/dnsmasq/docs/dnsmasq.conf.example").

I would not use the 127.0.0.1 address in any configuration.  This is the loopback (virtual) address and as such is not really part of your network.  It is only for the local host to talk to itself for testing purposes.

---

### Post by tomsimmons on 2009-06-06
> **bab1 said:**
> You do not use a static file (/etc/hosts) if you are running DHCP along with DNS services.

I have not changed the hosts file, this is as it was before I started this.

As for reading the dnsmasq.conf file, I have this is the file I have been modifying, with the aid of people in this thread (again thank you one and all for your help thus far), I have also been using the setup guide provided at thekelleys.  This instructs you to replace the existing upstream name server ip in resolv.conf with 127.0.0.1.  It is the sections after that about automating the updates from DHCP that I do not understand, but suspect I need to change/implement.

I have attached the config files.


Thanks


Tom

---

### Post by Aearenda on 2009-06-06
> This all means that there server can now ping clients by name. However from the window machine I still cannot ping the server by name, and from an Ubuntu client I can ping it by name, but the returned IP is 127.0.1.1. This value I can see as the second line in my hosts file on the server, the first line being 127.0.0.1.
This is because unless you tell it otherwise, dnsmasq DOES use /etc/hosts as well as DNS, and /etc/hosts must contain the loopback address or lots of things will fail.

You need to make a separate file, say /etc/hosts-dnsmasq, which has all the static addresses on your local network in it, but no 127.*.*.* addresses, and tell dnsmasq to use that instead of /etc/hosts.

On my server the /etc/dnsmasq.conf file includes these two lines for this purpose:```
no-hosts
addn-hosts=/etc/hosts-dnsmasq

```

BTW, I wouldn't use Network-manager on a server - /etc/network/interfaces is enough.

> I don't understand what they mean about the "Automatic DNS server configuration with DHCP" and the "Integration with DHCP". My server can see the clients by name, so it would seem this is working?I think they are talking first about getting the upstream DNS server address updated automatically - the ...8.1 address you are using - and then about using DNS to allocate machine names, which is unusual in a Windows network. You should be able to ignore both.

---

### Post by tomsimmons on 2009-06-07
Ok, as you suggested I created a new hosts file, and the only entry in it is
```
192.168.8.10	server
```

then edited dnsmasq.conf like so...
```
# If you don't want dnsmasq to read /etc/hosts, uncomment the
# following line.
no-hosts
# or if you want it to read another file, as well as /etc/hosts, use
# this.
addn-hosts=/etc/hosts-dnsmasq
```

I restarted with
```
/etc/inet.d/dnsmasq restart
```

And the result is...
- The server is unable to ping any client by name
- The Windows client is unable to ping an client by name
- The Ubuntu client can ping all machine by name

I haven't removed Network Manager, this machine isn't a server install, it's desktop, because it will be used that way also.

Thanks

Tom

---

### Post by Aearenda on 2009-06-07
How many clients do you have? Ubuntu clients won't register their names unless their /etc/dhcp3/dhclient.conf includes the uncommented line ```
send host-name "<hostname>";
```I think this is standard in Jaunty but I'm not sure how far back that was so. 
If the Ubuntu clients can ping all clients by name, then the Windows client failure is something Windows-specific. Check the output of 'ipconfig /all' on Windows to make sure it has the correct DNS address.

You did create the new file as /etc/hosts-dnsmasq didn't you? And left the old hosts file there too? (just checking)

I wonder if the names don't get re-established automatically in the DNS cache. You have a long lease time - 24h - so try unplugging a client from the net, then plug it in again (it will renew its lease and register its name) and see if you can ping it by name from another then.

---

### Post by tomsimmons on 2009-06-08
Hi

I shutdown the Windows and Ubuntu client, then changed the DHCP lease time to 10 minutes.  I then shutdown that machine down also for nearly 2 hours.  When I fired it back up, then the clients the Unbuntu client was still able to ping everything correctly, the server still can't ping anything by name nor can the Windows client.  I assume all this is as good as unplugging?!

By using ipconfig /all I can confirm the Windows machine has the correct DNS etc, and could also see that it had received the correct DHCP lease of 10 minutes.

I did create the hosts-dnsmasq in the correct place, and have confirmed the dnsmasq.conf is pointing to the right place.

The dhclient.conf does have that line enabled by default, so that's OK.

I don't think this is a Windows issue as one point during this adventure I was able to ping by name from the Windows machine, and the server is still unable to ping by name.

Thanks

Tom

---

### Post by Aearenda on 2009-06-08
Unfortunately, I've just come across your reply and it's late here. All that you are trying to do works for me, with the exception of running NM on the server, so it should work for you. Some quick thoughts:

1. Network Manager might be mucking with things on the server - especially /etc/resolv.conf.
2. How many Windows and how many Ubuntu clients do you have? (This might help me understand what you are describing better.)
3. Does the Ubuntu client have anything in /etc/hosts other than itself?
4. Dnsmasq logs to /var/log/daemon.log. Does this command yield anything useful?```
grep dnsmasq /var/log/daemon.log
```

---

### Post by tomsimmons on 2009-06-08
Aearenda,

Thanks for all your help on this.

I have a single Vista Home Premium client and a single Ubunut 9.04 UNR client.  The sever is a Ubuntu 9.04 Desktop install.

However this initial server is heading to my parents when finished, where there will be two XP Pro clients, and occasional other (most likely Windows) clients connecting.

One thing I suddenly remembered was that if I right click the network icon by the clock on the server and choose edit, the eth0 DNS Server was still set to 192.168.8.1.  I changed this to xxx.xxx.8.10 and things sort of start working. (see screen shot for clarification)

I say sort because...
1. from any machine to any machine, the ping by name can take a couple of seconds to start.  On Windows it seems it must have a timeout, because sometimes it just gives up
2. the ping times can be slow, 1, 2, 4, 16, 60, 95 ms
3. sometimes they are fine <1ms on Windows .3 to .4 on Linux
4. sometimes it's like it has indigestion, it may start slow, then suddenly speed up, alternativly it will suddenly slow down
5. on the linux machines sometime it will change from 64 bytes from server.<domain> (192.168.8.10)........ to 64 bytes from server.local (192.168.8.10)......

I change the dns server entry mentioned above to have, xxx.xxx.8.10, xxx.xxx.8.1 because the internet seemed a hit or miss, though that might have been in my mind.

As to what's in the dnsmasq.log, I'm afraid it doesn't show much that I would worry about, however I have attached a copy from the point that the machine start up.

The Ubuntu clients hosts is clean, just 127.0.0.1 and 127.0.1.1 (plus IPv6 gumf).


Thanks


Tom

---

### Post by tomsimmons on 2009-06-08
OK, after a full restart of everything I'm not sure where I stand to be honest.

Simply put, resolving of names can be very slow or fail, or it can work fine.  Internet can be there or missing.

Tired and cheesed off


Tom

---

### Post by Aearenda on 2009-06-08
Patience is always useful with this kind of problem!

I still think you are getting mucked around by Network Manager. The log lines > Jun  8 22:33:51 server dnsmasq[2270]: reading /etc/resolv.conf
Jun  8 22:33:51 server dnsmasq[2270]: using nameserver 192.168.8.10#53
Jun  8 22:33:51 server dnsmasq[2270]: using nameserver 192.168.8.1#53Show that it IS changing /etc/resolv.conf, and it seems that dnsmasq is reading them, so dnsmasq is told to use itself as well as the router - that could account for the name resolution delays, and the confusion about domain names.

However, once name resolution is done, ongoing ping delays cannot be accounted for by any of this. If they are not already, I would be using wired networking for testing rather than wireless, to try to figure out where the delays are. If they are already wired, I would be wondering about trying a different switch. 

In dnsmasq.conf, I would uncomment #domain-needed, #bogus-priv, #filterwin2k, #no-resolv, and #dhcp-authoritative. The no-resolv one will fix the problem caused by N-M mucking with /etc/resolv.conf for dnsmasq, but won't prevent the server itself from asking the router about local addresses once N-M has added the router to /etc/resolv.conf. On my server, I also have this set:
```
dhcp-option=6,192.168.8.10
```
It forces the Windows machines to know about the DNS service on the server. I'm not sure whether dnsmasq does this anyway, but it's explicit in my system.

Are you sure DHCP is turned off on the router?

If it still doesn't work after all this, install wireshark on the server and we will try to trace what is happening on the network.

---

### Post by tomsimmons on 2009-06-09
Sadly work has got in the way! :)

I'll try the changes you suggest when I get home tonight.

Thanks for all your help on this.


Tom

---

### Post by Aearenda on 2009-06-09
No worries - of course, it's evening here now!

---

### Post by tomsimmons on 2009-06-10
You're a genius!

I only had a short time to play last night, but it seems that one or more of the last set of suggestion was the solution.  In the time I had it seems all machine can reliably see each other.

Two questions:
1)
If you have a WiFi machine cable connected, both NIC's obviously get a IP, and the cabled get's priority on traffic.  However if you disconnect the cable, while the machine is able to carry on ok, other machines on the network don't seem to lose the DNS entry to the cabled IP.
2)
The Windows machine and the Ubunut client are both on WiFi.  The Windows machine can ping the server and the Ubuntu client with 1-2ms timings.  The server and the Ubuntu client can ping each other with similar timings.  However the server and Ubuntu client both return timings of 15-30ms for pinging the Windows machine.  If you cable the Windows machine, they can both ping it with sub 1ms timings.

Thanks again for all your help.


Tom

---

### Post by Aearenda on 2009-06-10
Happy to help!> If you have a WiFi machine cable connected, both NIC's obviously get a IP, and the cabled get's priority on traffic. However if you disconnect the cable, while the machine is able to carry on ok, other machines on the network don't seem to lose the DNS entry to the cabled IP. The issue here could be that the clients have cached data for the wired address that is now out of date, and it may be that they don't know the alternate wireless IP address. In theory, it should be possible to get them to clear their caches and re-query, but I don't know how to do that. Alternatively, and I think more likely, it could be that the dnsmasq entry for the wired connection persists, and is handed out in preference to the wireless address, because the wire has simply been unplugged so the client had no chance to release its lease. This might be another argument for a short lease time. Some experimentation with disabling the wired interface on Windows before unplugging the cable might prove this. On Ubuntu, it's harder to do this while using Network Manager - but you could try 'ifconfig eth0 down'.

> The Windows machine and the Ubunut client are both on WiFi. The Windows machine can ping the server and the Ubuntu client with 1-2ms timings. The server and the Ubuntu client can ping each other with similar timings. However the server and Ubuntu client both return timings of 15-30ms for pinging the Windows machine. If you cable the Windows machine, they can both ping it with sub 1ms timings.
If this is the time for the first ping, it might be to do with the order of name resolution specified on the hosts line in /etc/nsswitch.conf. I don't really know. If it is an ongoing time, it may be that they are both on wireless so there are two hops involved, rather than one. Actually, it can't be that, since you say it happens from the server too! I think I'd be trying to see what is happening using wireshark for this.

---

### Post by thuerrschmidt on 2009-09-13
I stumbled upon this thread while trying to set up my own dnsmasq configuration
in a server-plus-router environment that is very similar to the one outlined
by the original poster. The information that I found here was extremely helpful,
so a really big thank you goes to everybody who contributed to this thread!

To sum things up, here's a quick write-up of how I got my setup working.

I have a small Ubuntu server working day and night in my closet (literally), acting
primarily as a fileserver and backup server. I also have a cheapo internet router
with built-in ADSL modem and WLAN router. The router's functionality is rather limited,
and its DHCP and DNS features are not as flexible and reliable as I would like them.
So I decided to migrate these functions to my Ubuntu server, using dnsmasq.

First I installed the dnsmasq package and removed dhcp3-client in turn:

```
	sudo apt-get install dnsmasq
	sudo apt-get remove dhcp3-client

```
Then I assigned a static IP address to my server, simply called "theserver"
henceforward, by entering the following into /etc/network/interfaces:

```
	# primary network interface
	auto eth0
	# original dhcp client setup replaced by what follows below
	#iface eth0 inet dhcp
	iface eth0 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.2

```
With this the IP number of theserver becomes 192.168.1.1. The router (let's call
it "therouter") will become 192.168.1.2 later on.

Next, I added theserver in /etc/hosts:

```
	# pre-existing lines
	127.0.0.1       localhost
	127.0.1.1       localhost
	# added by me
	192.168.1.1    theserver

```
Then I opened /etc/resolve.conf and replaced all the settings I found there with these:

```
	nameserver 192.168.1.1
	domain dummy.domain

```
dummy.domain is just what the name says, a dummy domain for my local network.
I guess it's not strictly necessary to define one, but it may be helpful.

In the next step I opened /etc/dnsmasq.conf and de-commented and/or added the
following lines. The default file has lots of example settings with comprehensive
documentation in it, most of which we can ignore here, although it may be a little
difficult to find the relevant settings in between all the other text.

```
	# I want to be a nice boy and uncommented these settings as recommended
	domain-needed
	bogus-priv
	filterwin2k

	# make dnsmasq not read /etc/resolve.conf; it won't find anything
	# of interest there anyway
	no-resolv

	# the upstream DNS servers, in this case those provided by OpenDNS;
	# of course you can also use those provided by your ISP
	server=208.67.222.222
	server=208.67.220.220

	# the dummy domain again; you'll probably never see it again
	local=/dummy.domain/
	domain=dummy.domain

	# make dnsmasq act as an DHCP server with this address range available
	# for clients not listed below
	dhcp-range=192.168.1.80,192.168.1.160,12h

	# MAC addresses, IP numbers and host names of therouter as well as other
	# machines on the (W)LAN
	dhcp-host=00:00:00:00:00:11,192.168.1.2,therouter
	dhcp-host=00:00:00:00:00:22,192.168.1.3,someclient
	dhcp-host=00:00:00:00:00:33,192.168.1.4,anotherclient

	# gateway and ntp server settings transmitted to DHCP clients
	dhcp-option=option:router,192.168.1.2
	dhcp-option=option:ntp-server,192.168.1.1

	# prevent hijacking of invalid domain names by OpenDNS
	bogus-nxdomain=67.215.65.132

```
To apply all the new settings I entered these commands:

```
	sudo /etc/init.d/networking restart
	sudo /etc/init.d/dnsmasq restart

```
Finally I deactivated my router's DHCP server (via the device's web GUI),
refreshed my network connections, and that was basically it.

Or not quite, for I couldn't access the internet at first. It turned out that
my stupid router was to blame. Switching off its DHCP server wouldn't make
it act as a DHCP client, so it didn't receive its IP address from theserver
as it was supposed to. I fixed this by assigning a fixed 192.168.1.2 address in the
router's settings and by adding one more line to /etc/hosts on theserver:

```
	192.168.1.2    therouter

```
And *then* it really worked!

---

