---
title: "IP address is wrong? /etc/hosts not working"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by HyperHacker on 2011-01-02
Something is definitely odd here:
> [rena@mercury:~ 500]
$ hostname
mercury
[rena@mercury:~ 501]
$ cat /etc/hosts
127.0.0.1	mercury	localhost.localdomain	localhost
::1	mercury	localhost6.localdomain6	localhost6
#127.0.1.1	mercury.home	mercury
#192.168.0.128	mercury.home	mercury
#192.168.0.129	rei.home	rei
192.168.1.210	mercury.home	mercury
192.168.1.211	rei.home	rei
192.168.1.212	konata.home	konata

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
[rena@mercury:~ 502]
$ host mercury
mercury has address 192.168.1.65
[rena@mercury:~ 504]
$ traceroute mercury
traceroute to mercury (127.0.0.1), 30 hops max, 60 byte packets
 1  mercury (127.0.0.1)  0.034 ms  0.007 ms  0.007 ms
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:fc:9b:38:72  
          inet addr:192.168.1.210  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fe9b:3872/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2581438 (2.5 MB)  TX bytes:765379 (765.3 KB)
          Interrupt:16 Base address:0xd400
...so am I 192.168.1.210 (as I wanted and as ifconfig claims), 192.168.1.65 (as host claims), or 127.0.0.1 (as traceroute claims)? :confused:

---

### Post by bab1 on 2011-01-02
> **HyperHacker said:**
> Something is definitely odd here:

...so am I 192.168.1.[COLOR="DarkGreen"]**210 **[/COLOR](as I wanted and as ifconfig claims), 192.168.1.[COLOR="Magenta"]**65**[/COLOR] (as host claims), or 127.0.0.1 (as traceroute claims)? :confused:

The IP address 192.168.1.[COLOR="DarkGreen"]**210**[/COLOR] is the IP address you assigned to eth0.  It can be mapped in to the hostname of your choice.  This can be in the /etc/hosts file or in a DNS server.

My guess is that the ***host ***command ( which is a simple DNS lookup utility) is ***not ***looking at your host file as you think it is.  The entry you have shows this```
192.168.1.210	mercury.home	mercury
```
This is does ***not ***have the hostname: mercury as you might think.  The entry shows the domain name (e.g. mercury.home ) and then an alias (which is the real hostname).  The utility host looks *only *for the first name listed and since it can't fine the hostname mercury it looks at a listing somewhere else that maps the 192.168.1.[COLOR="Magenta"]**65**[/COLOR] IP address to the hostname ***mercury***.

The way to have the hostname lookup resolve correctly is like this```
192.168.1.210	mercury   mercury.home
```

My preference is to never add FQDN to the /etc/hosts file.  This is not what it was intended for.  You could add```
search home
```as a domain in the /etc/resolv.conf file

Read the descriptions in the following man pages```
man host
man hosts # the description of /etc/hosts
man resolv.conf
```

---

### Post by HyperHacker on 2011-01-02
OK, well I removed the mercury.home alias and it's still showing .65. It seems like what's happening here is it's going to a router (which I can't reboot at the moment) and asking it for mercury, and the router is saying .65; I can see this in its config page. The question then is why it's not looking at /etc/hosts first?

This is the very same hosts file I was using in 10.04 which worked fine...```
$ stat /etc/hosts
  File: `/etc/hosts'
  Size: 499       	Blocks: 8          IO Block: 4096   regular file
Device: fc01h/64513d	Inode: 8653466     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2011-01-02 13:43:02.437156000 -0700
Modify: 2011-01-02 13:43:02.325156006 -0700
Change: 2011-01-02 13:43:02.429156003 -0700
```Nothing wrong with that?

---

### Post by bab1 on 2011-01-02
> **HyperHacker said:**
> OK, well I removed the mercury.home alias and it's still showing .65. It seems like what's happening here is it's going to a router (which I can't reboot at the moment) and asking it for mercury, and the router is saying .65; I can see this in its config page. The question then is why it's not looking at /etc/hosts first?
...


The command host looks to the DNS server referenced in your /etc/resolv.conf file.  This is by design.

See the output of ```
host -v mercury
```

You will have to reset the listing in the router for it to successfully resolve to the correct hostname.

---

### Post by HyperHacker on 2011-01-07
OK, so I rebooted all of the routers and power-cycled all of the machines. Now it's not working at all:> $ host -v mercury
Trying "mercury"
Host mercury not found: 3(NXDOMAIN)
Received 25 bytes from 192.168.1.200#53 in 1 ms

$ cat /etc/hosts
#127.0.0.1	mercury	localhost.localdomain	localhost
#127.0.0.1	mercury	localhost.localdomain	localhost
127.0.0.1	mercury	localhost.localdomain	localhost
::1	mercury	localhost6.localdomain6	localhost6
#127.0.1.1	mercury.home	mercury
#192.168.0.128	mercury.home	mercury
#192.168.0.129	rei.home	rei
192.168.1.210	mercury
192.168.1.211	rei
192.168.1.212	konata

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allroutersProbably doesn't help that something keeps adding that first line back at startup, but shouldn't it still return 127.0.0.1 then?

This is the exact same setup I had in 10.04 and everything I've been told about /etc/hosts says that it's the first place the system looks to resolve names, before asking any other systems - so why has it stopped doing that?

---

### Post by bab1 on 2011-01-07
> **HyperHacker said:**
> OK, so I rebooted all of the routers and power-cycled all of the machines. Now it's not working at all:
```
$ host -v mercury
Trying "mercury"
Host mercury not found: 3(NXDOMAIN)
Received 25 bytes from 192.168.1.200#53 in 1 ms

$ cat /etc/hosts
#127.0.0.1	mercury	localhost.localdomain	localhost
#127.0.0.1	mercury	localhost.localdomain	localhost
[COLOR="Red"]**127.0.0.1	mercury**[/COLOR]	localhost.localdomain	localhost
::1	mercury	localhost6.localdomain6	localhost6
#127.0.1.1	mercury.home	mercury
#192.168.0.128	mercury.home	mercury
#192.168.0.129	rei.home	rei
[COLOR="red"]**192.168.1.210	mercury**[/COLOR]
192.168.1.211	rei
192.168.1.212	konata

# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Probably doesn't help that something keeps adding that first line back at startup, but shouldn't it still return 127.0.0.1 then?

No it sure doesn't help.  If you have something that overwrites the /etc/host file then you have no control at all.

Does this host use Network Manager (NM) for interface configuration?  How do you get DNS resolution?  Are you using DHCP to assign IP addresses?

The host name to IP address mapping should be unique.  See the entries above in [COLOR="Red"]**red**[/COLOR].  You have the hostname mercury mapped to 2 interfaces  
> 

This is the exact same setup I had in 10.04 
The setup may be the same, but the OS may have changes.   :-( > 

and everything I've been told about /etc/hosts says that it's the first place the system looks to resolve names, before asking any other systems - so why has it stopped doing that?

The /etc/nsswitch.conf file controls which data source (files, DNS) is used and in what order.  See [**_here_**]("http://linuxservertutorials.blogspot.com/2008/11/ubuntu-nsswitchconf-guide.html").

When you use a specific tool (i.e. host) it may not use the services of the /etc/nsswitch.conf file.

---

### Post by HyperHacker on 2011-01-08
I have the Xfce network manager set to manual addressing (address 192.168.1.210, gateway 192.168.1.200, DNS server 192.168.1.200), which would be my guess for what's messing with my hosts file, but I don't see a way to stop it. :| nsswitch.conf looks fine:```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```'files' for the first entry should mean /etc/hosts is the first place to look? Even if I edit out that extra line (which seems to reappear every startup) it doesn't find the other and seems to just go straight to DNS.

---

### Post by bab1 on 2011-01-08
> **HyperHacker said:**
> I have the Xfce network manager set to manual addressing (address 192.168.1.210, gateway 192.168.1.200, DNS server 192.168.1.200), which would be my guess for what's messing with my hosts file, but I don't see a way to stop it. :|

Network Manager generally has a reputation of breaking standard Linux/Unix practices.  I manually configure the interfaces (/etc/network/interfaces, /etc/resolv.conf, and /etc/hosts) on all my machines. 
> 
nsswitch.conf looks fine:```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```'files' for the first entry should mean /etc/hosts is the first place to look?

Even if I edit out that extra line (which seems to reappear every startup) it doesn't find the other and seems to just go straight to DNS.

You would think so, but there is no reason that you can't write code that breaks conventional methods.

Short of removing Network Manager I don't see any resolution.  This seems to be a known problem.  See [**_here_**]("http://us.generation-nt.com/answer/bug-567411-network-manager-rewrites-hosts-help-169017791.html").  This does not appear to be an isolated incident, see [**_here_**]("http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=Xfce+network+manager#hl=en&expIds=25657,27955&sugexp=ldymls&xhr=t&q=%22network+manager%22+%2B/etc/hosts&cp=29&qe=Im5ldHdvcmsgbWFuYWdlciIgKy9ldGMvaG9zdHM&qesig=WixCE3CxtcJz3B_O96DC4Q&pkc=AFgZ2tmy5m1i2-0uK-OxPk0iHV9MAfHJHERN9DUcogxREhU8dzl0wFpUmdY-o3U2XSp9xI-vsnCADucyD9IWaZiunOmvXg9jow&pf=p&sclient=psy&aq=f&aqi=&aql=&oq=%22network+manager%22+%2B/etc/hosts&gs_rfai=&pbx=1&fp=ca05a7bb65e82229").

---

### Post by HyperHacker on 2011-01-08
So it's a known issue with network-manager? Can I safely remove that? (I'm not using wifi, so it's usually just sitting in the tray anyway.)

I still don't quite understand though why manually fixing the hosts file doesn't help...

---

### Post by bab1 on 2011-01-08
> **HyperHacker said:**
> So it's a known issue with network-manager? Can I safely remove that? (I'm not using wifi, so it's usually just sitting in the tray anyway.)

You do not need Network Manager to successfully configure the interfaces on a Ubuntu host.  I have a desktop that is manually configured.  You can still configure DHCP or you can use a static IP addressing (via configuration files).  I also have a Ubuntu Server.  This does not have a GUI and therefore has no Network Manager installed.  You have to configure the system manually with configuration files.

This [**_article _**]("http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html")shows basically how you make the changes I'm talking about.  This is for an older version of Ubuntu so there are some instructions that could be different.
  

What do you mean by *"sitting in the tray anyway"*?
> 

I still don't quite understand though why manually fixing the hosts file doesn't help...
Network Manager modifies the /etc/hosts file when you first boot up.

---

### Post by HyperHacker on 2011-01-08
I meant since I'm not using wireless networking, network-manager doesn't seem to be doing me any good anyway - just an icon in my notification tray taking up space. (That would be where I'd go to select a wireless network...)

I followed those instructions and got an interesting error:> $ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth0=eth0.

---

### Post by bab1 on 2011-01-08
> **HyperHacker said:**
> I meant since I'm not using wireless networking, network-manager doesn't seem to be doing me any good anyway - just an icon in my notification tray taking up space. (That would be where I'd go to select a wireless network...)

I followed those instructions and got an interesting error:
```
$ sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth0=eth0.
```

It appears you are still trying to start the networking through Network Manager.  See [**_here _**]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/663352").  Did you actually remove the Network Manager package?

Normally you would remove the package with this command```
sudo apt-get purge network-manager
```

You can also just use the Synaptics package manager.  Mark for complete removal when you do this.  

Can you post the content of the 3 files you directly modified?

---

### Post by HyperHacker on 2011-01-09
Well, the article didn't mention removing network-manager entirely (only update-rc removing its startup entry), but I tried that and restarted and that completely disabled networking until I managed to get the package from another machine and reinstall it.

The only file I've modified is /etc/hosts, posted above.

---

### Post by cariboo on 2011-01-09
Why do you have 127.0.1.1 commented out? Remove the hash mark, and things should work.

---

### Post by bab1 on 2011-01-09
> **cariboo907 said:**
> Why do you have 127.0.1.1 commented out? Remove the hash mark, and things should work.

The OP does have a legit loopback address in the /etc/hosts file.  See in green below:
```

#127.0.0.1	mercury	localhost.localdomain	localhost
#127.0.0.1	mercury	localhost.localdomain	localhost
[COLOR="DarkGreen"]**127.0.0.1	mercury	localhost.localdomain	localhost**[/COLOR]

```

---

### Post by bab1 on 2011-01-09
> **HyperHacker said:**
> Well, the article didn't mention removing network-manager entirely (only update-rc removing its startup entry), but I tried that and restarted and that completely disabled networking until I managed to get the package from another machine and reinstall it.

The only file I've modified is /etc/hosts, posted above.

It is okay if you just want to disable Network Manager, rather than removing it. You then need to manually configure the interfaces.

You can manually configure the IP addressing by editing the **/etc/network/interfaces** file.  You also need to configure the IP addresses of the DNS server(s) you are going to use by manually editing the **/etc/resolv.conf** file.  Once you have done this you will want to map host names to IP addresses with the **/etc/hosts **file.

When you have done the configuring the interfaces you can cycle the interfaces with this ```
ifdown -a
ifup -a
```

This will down the interfaces listed in /etc./network/interfaces and then bring them up again with the new configuration.

[**_Here _**]("http://www.jonathanmoeller.com/screed/?p=2305")is a similar explanation.

If you have questions, ask before you modify the files.  Once again: If you post the outputs of those 3 files I will give you working examples.

---

