---
title: "How do I set up a static IP if I have no router?"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by anthony62490 on 2010-11-30
I am trying to set up SSH so that I can edit files on a home server (linux). I know this question has been asked many times before, but none of the answers seem to apply to me.

Here's my setup. I have the modem connected to a switch (wired) that connects 2 PCs to the internet (one desktop, one server, both wired). 

All of the threads I see that discuss static IPs seem to require that I set up a router. Is this necessary? Can I still transfer files through a switch?

---

### Post by redmk2 on 2010-12-01
> **anthony62490 said:**
> I am trying to set up SSH so that I can edit files on a home server (linux). I know this question has been asked many times before, but none of the answers seem to apply to me.

Here's my setup. I have the modem connected to a switch (wired) that connects 2 PCs to the internet (one desktop, one server, both wired). 

All of the threads I see that discuss static IPs seem to require that I set up a router. Is this necessary? Can I still transfer files through a switch?

The thing you are calling a modem is the gateway (router).  if you were truly connected only to a switch you would not have internet connectivity.

If you have a auto configured IP address on either or both of your PC's then they are requesting an IP address from a DHCP server.  Most likely the modem hosts the DHCP server.

You can still manually configure your IP addresses in this network.  There are a few things you need to know:
```

The network side IP address of the modem.

The IP range of the DHCP pool.

Does the modem have the ability to forward TCP ports?

```

Essentially you should configure the host with the SSH server to have an IP address on the same subnet as the modem's gateway interface, but **outside **of the DHCP pool range. On the modem, you need to forward the the TCP port for SSH to the IP address you have assigned to the SSH server.

With this done you should be able to SSH into the server from the outside the local network as long as you know the WAN side IP address.

Does this sound like what you want?

---

### Post by dangerjunkie2002 on 2010-12-01
Hi Anthony,

What is the make and model number of the modem and the switch you've got please? It's almost a certainly that one of these has the router built in. Do you have cable Internet or DSL?

If you right click on the network icon (it will either look like 2 arrows, one up and one down or a radio wave) in the bar at the top of the screen and then left-click "Connection Information" you should see some addresses.

Find the address that says "Default Route" (On my network it's 192.168.1.1). Open Firefox (or your browser of choice) and put that address into the address bar. You should get the a page asking you to log into your router. If you've not done this before and haven't changed it then you will probably find the default password in the documentation that came with the device or on a sticker on the bottom of it. BTW if the password is still the default I would recommend you change it for your security.

If you post the make and model of the device here I'm sure someone will be able to help you work out which addresses are free.

When you say you want to use ssh to edit files on your server, so you mean you want to do this from another machine on your home or do you want to do this from a machine at another location over the Internet?

Cheers,
Paul.

---

### Post by anthony62490 on 2010-12-01
> **redmk2 said:**
> If you have a auto configured IP address on either or both of your PC's then they are requesting an IP address from a DHCP server.  Most likely the modem hosts the DHCP server.

You can still manually configure your IP addresses in this network.  There are a few things you need to know:
```

The network side IP address of the modem.

The IP range of the DHCP pool.

Does the modem have the ability to forward TCP ports?

```

Essentially you should configure the host with the SSH server to have an IP address on the same subnet as the modem's gateway interface, but **outside **of the DHCP pool range. On the modem, you need to forward the the TCP port for SSH to the IP address you have assigned to the SSH server.

With this done you should be able to SSH into the server from the outside the local network as long as you know the WAN side IP address.

Does this sound like what you want?

Yes, this sounds about right. Primarily, I'd like to edit it from the local network, so anything more than that would be a bonus.

```

The network side IP address of the modem.
**192.168.1.254**

The IP range of the DHCP pool.
**I don't know. How do I check this?**

Does the modem have the ability to forward TCP ports?
**Yes. TCP and UDP**

```

[QUOTE=dangerjunkie2002]What is the make and model number of the modem and the switch you've got please?
**The modem/router is a 2WIRE 3800HGV-B and the switch is a Linksys EG005W**

Do you have cable Internet or DSL?
**Since it comes from the phone company, I imagine it must be DSL**[/QUOTE]

---

### Post by dandnsmith on 2010-12-01
> Do you have cable Internet or DSL?
Since it comes from the phone company, I imagine it must be DSL

Unless, perhaps, Verizon supplies phone and internet.
When visiting (from UK) friends in Washington, I found a rather intriguing Verizon setup, which wasn't anything like ADSL in the UK - more like cable in the way it was organised.

---

### Post by bab1 on 2010-12-01
> **dandnsmith said:**
> Unless, perhaps, Verizon supplies phone and internet.
When visiting (from UK) friends in Washington, I found a rather intriguing Verizon setup, which wasn't anything like ADSL in the UK - more like cable in the way it was organised.

Indeed the service can look like DSL or Cable.  It is the method the various subscribers are aggregated at the CO (central office) before routed onto the Internet that describes the difference between DSL and Cable (e.g what type of switch is the WAN side connected to upstream.

Telcos only provide DSL and use a device called a DSLAM (Digital Subscriber Line Access Multiplexer) as a upstream swich. See [**_here _**]("http://en.wikipedia.org/wiki/Digital_Subscriber_Line_Access_Multiplexer")for information.

---

### Post by redmk2 on 2010-12-02
> **anthony62490 said:**
> Yes, this sounds about right. Primarily, I'd like to edit it from the local network, so anything more than that would be a bonus.

The network side IP address of the modem.
**192.168.1.254**

The IP range of the DHCP pool.
**I don't know. How do I check this?**

The default is listed in the manual under "Configuring Advanced settings" page. 24. The pool range is 192.168.1.[COLOR="Red"]**33**[/COLOR] through  192.168.1.[COLOR="red"]**250**[/COLOR]. You can change this later if you want less addresses in the pool (more for static IP addressing)> 

Does the modem have the ability to forward TCP ports?
**Yes. TCP and UDP**

Let's start with getting SSH setup in the LAN and then we can play with the port forwarding.


So we have a network that is:> 1192.168.1.0/24 --> subnet mask = 255.255.255.0

We have IP addresses we can use in this range:
```
192.168.[COLOR="Green"]**1**[/COLOR] to 192.168.1.[COLOR="Green"]**32**[/COLOR]
```

We have a default gateway (routers LAN IP address):```
192.168.1.254
```

This is all you need to set your IP addresses statically in Ubuntu.  You also need to set the DNS servers that you will use on the internet.  These can be he ones supplied by your ISP or you can use the well known Google DNS or OpenDNS adresses if you wish.

I use Google's DNS.  The IP addresses are: ```
8.8.8.8 and 8.8.4.4
```

If you need to access the modems console use this address in your web browser:```
http://gateway.2wire.net/management
```

I'll bet it is really is the same as this:```
http://192.168.1.254/management 
```

Are you using Ubuntu Desktop?  Are you configuring this with Network Manager (NM)?

I would set one of the PC's to :
```

# /etc/network/interfaces
address 192.168.1.**[COLOR="Green"]1[/COLOR]**
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.254

```

The second PC is eaxactly the same except for the line:
```
address 192.168.1.[COLOR="green"]**2**[/COLOR]
```
you should also set the dns server you are going to use like this:
```

# /etc/resolve.conf
nameserver 8.8.8.8
nameserver 8.8.4.4

```

Hope this gets you started.  I have a copy of the manual for your modem so I can confirm anything you need to know. Let me know tomorrow how you are doing.

---

### Post by anthony62490 on 2010-12-04
Let's start with getting SSH setup in the LAN and then we can play with the port forwarding.

So we have a network that is:
```
192.168.1.0/24 --> subnet mask = 255.255.255.0
```

We have IP addresses we can use in this range:
```
192.168.1.[COLOR="Lime"]1[/COLOR] to 192.168.1.[COLOR="Lime"]32[/COLOR]
```

We have a default gateway (routers LAN IP address):
```
192.168.1.254
```

This is all you need to set your IP addresses statically in Ubuntu. You also need to set the DNS servers that you will use on the internet. These can be he ones supplied by your ISP or you can use the well known Google DNS or OpenDNS adresses if you wish.

I use Google's DNS. The IP addresses are:
```
8.8.8.8 and 8.8.4.4
```
**Wait, I need to access my computer through a DNS server? Is that really necessary to access a computer that is literally 3 feet away from me? This step is not mentioned on any SSH setup guide I have managed to find.**

If you need to access the modems console use this address in your web browser:
```
http://gateway.2wire.net/management
```
I'll bet it is really is the same as this:
```
http://192.168.1.254/management
```

**Not quite, but it's similar. [http://192.168.1.254](http://192.168.1.254) will get me to the modem's config pages**

Are you using Ubuntu Desktop? Are you configuring this with Network Manager (NM)?
[B]Not entirely sure what I should be using to configure this, but I kinda figured I could do it from the modem's config page.
Also, 'nm' gives the following error:[/B]
```
[B]anthony@anthony-desktop:~$ nm
nm: 'a.out': No such file[/B]
```


I would set one of the PC's to :
```
# /etc/network/interfaces
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.254
```

The second PC is exactly the same except for the line:
```
address 192.168.1.2
```

**Okay, hold on a second. Should I be using 'nm' for these changes, or will Nano be good for the job? Running "nano /etc/network/interfaces" gives me the following file:**
```

[B]
auto lo
iface lo inet loopback[/B]
```

you should also set the dns server you are going to use like this:
```
# /etc/resolve.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
```

**Again, do I need to be touching these files with Nano, or do I need to be using 'nm'? 'nano /etc/resolv.conf' gives the following file:**
```
[B]
# Generated by NetworkManager
domain gateway.2wire.net
search gateway.2wire.net
nameserver 192.168.1.254[/B]
```
**Also, I'm seeing two 'nameserver' listed there. Is that a multiple choice question, or can I list both of them?**

Hope this gets you started. I have a copy of the manual for your modem so I can confirm anything you need to know. Let me know tomorrow how you are doing.

---

### Post by redmk2 on 2010-12-04
[COLOR="SeaGreen"]****[/COLOR]> **anthony62490 said:**
> 

Let's start with getting SSH setup in the LAN and then we can play with the port forwarding.

So we have a network that is:
```
192.168.1.0/24 --> subnet mask = 255.255.255.0
```

We have IP addresses we can use in this range:
```
192.168.1.[COLOR="Lime"]1[/COLOR] to 192.168.1.[COLOR="Lime"]32[/COLOR]
```

We have a default gateway (routers LAN IP address):
```
192.168.1.254
```

This is all you need to set your IP addresses statically in Ubuntu. You also need to set the DNS servers that you will use on the internet. These can be he ones supplied by your ISP or you can use the well known Google DNS or OpenDNS adresses if you wish.

I use Google's DNS. The IP addresses are:
```
8.8.8.8 and 8.8.4.4
```

> **Wait, I need to access my computer through a DNS server? Is that really necessary to access a computer that is literally 3 feet away from me? This step is not mentioned on any SSH setup guide I have managed to find.**

Where did I say that you *had *to use the services of a DNS server on a LAN?  

I'm helping you configure an interface with a static IP address.  If you are using the host for internet access too, not just ssh conectivity on the LAN, you will need to resolve the FQDN of the Internet site.  You don't go *through *a DNS server. The request resolves FQDN to IP addresses when needed.

I can't see the guide you are referring to so I can't comment on its correctness.  
> 

If you need to access the modems console use this address in your web browser:
```
http://gateway.2wire.net/management
```
I'll bet it is really is the same as this:
```
http://192.168.1.254/management
```

[QUOTE]**Not quite, but it's similar. [http://192.168.1.254](http://192.168.1.254) will get me to the modem's config pages**

Are you using Ubuntu Desktop? Are you configuring this with Network Manager (NM)?

> [B]Not entirely sure what I should be using to configure this, but I kinda figured I could do it from the modem's config page.
Also, 'nm' gives the following error:[/B]
```
[B]anthony@anthony-desktop:~$ nm
nm: 'a.out': No such file[/B]
```
[/QUOTE]
You can't configure the local hosts from the modem's config page.  Those pages are used to configure the modem itself.

Network Manager is one method used to manage the local hosts interfaces (IP addressing).  It is not invoked from the command line normally.  It is a GUI application.  If you disable Nework Manager you can manually configure the interfaces by editing the configuration files.  
> 

I would set one of the PC's to :
```
# /etc/network/interfaces
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.254
```

The second PC is exactly the same except for the line:
```
address 192.168.1.2
```

[QUOTE]**Okay, hold on a second. Should I be using 'nm' for these changes, or will Nano be good for the job? Running "nano /etc/network/interfaces" gives me the following file:**
```

[B]
auto lo
iface lo inet loopback[/B]
```

[/QUOTE]The best thing would be to set Network Manager to *ignore *the statically set settings.  Then you can use a text editor (i.e. Nano) to modify the text files that control the interface settings.  The files we are talking about are:```
/etc/network/interfaces

/etc/resolve.conf
```> 

You should also set the dns server you are going to use like this:
```
# /etc/resolve.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
```

[QUOTE]**Again, do I need to be touching these files with Nano, or do I need to be using 'nm'? **


[/QUOTE]If Network Manager is configured correctly you should be able to mange the configuration from its GUI interface.  If you use Nano whilst ignoring the fact that Network Manager is in control, the changes will not survive a shut down and subsiquent startup.(see my note in red below)> 

nano /etc/resolv.conf' gives the following file:[/B]
```
[B]
# Generated by NetworkManager **[COLOR="Red"]<-- Network Manager is in control[/COLOR]**
domain gateway.2wire.net [COLOR="Red"]<-- what do you suppose this for?[/COLOR]
search gateway.2wire.net [COLOR="red"]And this?[/COLOR]
nameserver 192.168.1.254  [COLOR="green"]**<-- This is the local and forwarding DNS server**[/COLOR][/B]
```

**Also, I'm seeing two 'nameserver' listed there. Is that a multiple choice question, or can I list both of them?**

You can set multiple nameservers.  I see your modem has a DNS server built in.  This should be listed first.

I am no fan of Network Manager.  My Desktops all had the interfaces configured manually when I did the install.  Network Manager is there, but I have never used it.  There is a setting in the conf file for Network Manager to have it ignore a specific interface.

For neatness sake, please learn to wrap quote brackets around text that youar responding to.  You can manually do this using```

[QUOTE] some text here [ /QUOTE]

```
Or you can click on the quote icon at the top of the text box when responding.

---

### Post by anthony62490 on 2010-12-05
Sorry, I don't mean to sound pissy, but when a [guide]("http://www.linuxhelp.net/guides/ssh/") contains the words "Within a few minutes, I had ssh up and running", it sure does seem like there is some speck of understanding that I can't quite reach.

Okay, so on Desktop, I have modified the following files like so:
```
# /etc/network/interfaces
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.254
```
```
#/etc/resolv.conf
# Generated by NetworkManager
domain gateway.2wire.net
search gateway.2wire.net
nameserver 192.168.1.254
nameserver 8.8.8.8
```

And on Server, the files look like this:
```
#/etc/network/inferfaces
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.254
```
```
#/etc/resolv.conf
domain gateway.2wire.net
search gateway.2wire.net
nameserver 192.168.1.254
nameserver 8.8.8.8
```

Assuming that I set this up right, is there anything else that needs to be done?

By the way, I really appreciate you taking time out of your day to help me out with this. I owe you one.

---

### Post by redmk2 on 2010-12-06
> **anthony62490 said:**
> ...it sure does seem like there is some speck of understanding that I can't quite reach.

I believe this might be so.  Did you happen to see the date of this tutorial?  Like ancient history: December 29th, 1999.

I would not use anything that did not pertain directly to the distro and version of Linux you are working with.  First, there have been a ton of updates since 1999.  Second, not all distros are the same.  Debian and Ubuntu are similar enough, but Redhat, Fedora, CentOS and SUSE are different.  Most  guides will only cover one flavor.  In this case I am sure that the latest Ubuntu versions are different enough that you will certainly have problems with that old guide. 

I think you will be better served with [**_[COLOR="Blue"]this guide[/COLOR]_**]("https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html") if you are using Ubuntu [COLOR="Blue"]10.10[/COLOR] or [COLOR="DarkRed"]10.04 [/COLOR]use  [**_[COLOR="DarkRed"]this guide [/COLOR]_**]("https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html")or if [COLOR="DarkGreen"]9.10[/COLOR] then [**_[COLOR="DarkGreen"]this guide[/COLOR]_**]("https://help.ubuntu.com/9.10/serverguide/C/openssh-server.html") is what you should use.  Yes there are differences.  :D> 

Okay, so on Desktop, I have modified the following files like so:
```
# /etc/network/interfaces
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.254
```
```
#/etc/resolv.conf
# Generated by NetworkManager
domain gateway.2wire.net
search gateway.2wire.net
nameserver 192.168.1.254
nameserver 8.8.8.8
```

And on Server, the files look like this:
```
#/etc/network/inferfaces
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.254
```
```
#/etc/resolv.conf
domain gateway.2wire.net
search gateway.2wire.net
nameserver 192.168.1.254
nameserver 8.8.8.8
```

Assuming that I set this up right, is there anything else that needs to be done?
The configuration looks correct.  At this point I assume you have network connectivity.  Is this correct?  Can you ping each host by IP address?  Do you have Internet connectivity?  Can you surf the web? 

If the the hosts perform correctly, the only thing left is to confirm that the configuration survives a reboot.  Do the the hosts still have the correct configuration?  you can check the basic configuration on each of the two hosts with this CLI command:```
ifconfig -a
```

---

