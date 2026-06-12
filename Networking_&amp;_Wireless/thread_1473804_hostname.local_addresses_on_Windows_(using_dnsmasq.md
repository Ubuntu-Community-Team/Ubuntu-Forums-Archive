---
title: "hostname.local addresses on Windows (using dnsmasq)"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by undecim on 2010-05-05
I'm trying to get the Windows machines on my network to access hostname.local addresses. I want to do this without setting up extra software or settings on the Windows computers.

I already have dnsmasq on my server handling all DHCP and DNS requests. How can I get dnsmasq to return an IP address for a .local address?

---

### Post by Iowan on 2010-05-05
My */etc/dnsmasq.conf* includes the following lines (although I have a different domain):```
expand-hosts
domain=local

```

---

### Post by redmk2 on 2010-05-05
> **undecim said:**
> I'm trying to get the Windows machines on my network to access hostname.local addresses. I want to do this without setting up extra software or settings on the Windows computers.

I already have dnsmasq on my server handling all DHCP and DNS requests. How can I get dnsmasq to return an IP address for a .local address?

The DNS zone .*local* has more than one meaning now a days.  Do you mean a link local addr like what [**_[COLOR="Red"]Avahi [/COLOR]_**]("http://avahi.org/wiki/AvahiAndUnicastDotLocal")uses?  Or have you set up a DNS zone that uses *.local*, meaning Avahi is not used at all?

---

### Post by undecim on 2010-05-05
> **Iowan said:**
> My */etc/dnsmasq.conf* includes the following lines (although I have a different domain):```
expand-hosts
domain=local

```

I tried this, restarted dnsmasq, and it didn't work.

> **redmk2 said:**
> The DNS zone .*local* has more than one meaning now a days.  Do you mean a link local addr like what [**_[COLOR="Red"]Avahi [/COLOR]_**]("http://avahi.org/wiki/AvahiAndUnicastDotLocal")uses?  Or have you set up a DNS zone that uses *.local*, meaning Avahi is not used at all?

Like avahi uses.

---

### Post by redmk2 on 2010-05-05
> **undecim said:**
> I tried this, restarted dnsmasq, and it didn't work.



Like avahi uses.

DNSMasq is not used for providing Local Link Zeroconf IP addresses (169.254.x.x).  Avahi is complete on its own.  The whole point of it is to provide a valid (but limited) IP address when no DHCP sever is listening on a LAN segment.  This is the essence of  Zeroconf.  Read the link I put in my last post.  See [**_here _**]("http://en.wikipedia.org/wiki/Avahi_(software)")for a Wikipedia explanation.

---

### Post by undecim on 2010-05-09
> **redmk2 said:**
> DNSMasq is not used for providing Local Link Zeroconf IP addresses (169.254.x.x).  Avahi is complete on its own.  The whole point of it is to provide a valid (but limited) IP address when no DHCP sever is listening on a LAN segment.  This is the essence of  Zeroconf.  Read the link I put in my last post.  See [**_here _**]("http://en.wikipedia.org/wiki/Avahi_(software)")for a Wikipedia explanation.

I don't want 169.254.x.x IP addresses. I already have DNSMasq providing 192.168.1.x addresses, and when I need another Linux computer on the network to connect to, for example, my laptop, that computer can use caffeine.local in place of 192.168.1.44 to connect. Is there not some way to make DNSMasq return 192.168.1.44 when a Windows computer looks up caffeine.local?

---

### Post by redmk2 on 2010-05-09
> **undecim said:**
> I don't want 169.254.x.x IP addresses. 
I already have DNSMasq providing 192.168.1.x addresses, and when I need another Linux computer on the network to connect to, for example, my laptop, that computer can use caffeine.local in place of 192.168.1.44 to connect. Is there not some way to make DNSMasq return 192.168.1.44 when a Windows computer looks up caffeine.local?

Sure, but first you have to read (and understand) how Avahi works (so you can suppress it) and configure DNSMasq to provide hostnames with the .local suffix.

Here is the link again to the [**_Avahi _**]("http://avahi.org/wiki/AvahiAndUnicastDotLocal")page you need.  Look for the section *Better workaround* for what to do to stop Avahi using  *.local* as the Zeroconf domain.

Once you have moved Avahi from .*local *to .*alocal * you can configure DNSMasq to provide hostnames as well as IP addresses.  You will find a fully annotated conf file for DNSMasq [**_here_**]("http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq.conf.example").

---

### Post by undecim on 2010-05-11
> **redmk2 said:**
> Sure, but first you have to read (and understand) how Avahi works (so you can suppress it) and configure DNSMasq to provide hostnames with the .local suffix.

Here is the link again to the [**_Avahi _**]("http://avahi.org/wiki/AvahiAndUnicastDotLocal")page you need.  Look for the section *Better workaround* for what to do to stop Avahi using  *.local* as the Zeroconf domain.

Once you have moved Avahi from .*local *to .*alocal * you can configure DNSMasq to provide hostnames as well as IP addresses.  You will find a fully annotated conf file for DNSMasq [**_here_**]("http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq.conf.example").

So I have to add each host manually? I thought that there might be some way to make dnsmasq use avahi to lookup .local addresses. Why is this not possible?

---

### Post by redmk2 on 2010-05-12
> **undecim said:**
> So I have to add each host manually?
Why would you say that?> 
I thought that there might be some way to make dnsmasq use avahi to lookup .local addresses.
I'm not sure what you mean by this. DNSmasq uses the protocols [COLOR="Blue"]**DHCP and DNS**[/COLOR] to provide IP addressing and name services (hostnames) on a LAN.  Avahi uses [COLOR="DarkGreen"]**Multicast DNS on a link local network**[/COLOR] for DNS [COLOR="DarkGreen"]**while suppling it's own IP addressing scheme**[/COLOR].> 
Why is this not possible?
They use different protocols to achieve different goals.  Did you read the 2 links I gave you?

It is important to note that Avahi is not usable outside the local LAN.  It is really only useful for informal non-structured connections such as another peer device (host, printer, etc.).

---

### Post by undecim on 2010-05-12
> **redmk2 said:**
> Why would you say that?

I'm not sure what you mean by this. DNSmasq uses the protocols [COLOR="Blue"]**DHCP and DNS**[/COLOR] to provide IP addressing and name services (hostnames) on a LAN.  Avahi uses [COLOR="DarkGreen"]**Multicast DNS on a link local network**[/COLOR] for DNS [COLOR="DarkGreen"]**while suppling it's own IP addressing scheme**[/COLOR].

They use different protocols to achieve different goals.  Did you read the 2 links I gave you?

It is important to note that Avahi is not usable outside the local LAN.  It is really only useful for informal non-structured connections such as another peer device (host, printer, etc.).

I can use a command like "ping caffeine.local" to ping my laptop, and I see this line: "PING caffeine.local (192.168.1.44) 56(84) bytes of data."

Whenever I use "caffeine.local" on an Ubuntu computer (including the server that is running dnsmasq), that name resolves to 192.168.1.44. If I want to host a network game that will include Windows hosts, I need to find my IP address and give that to any Windows user that wants to connect.

I understand why that is (and please correct me on any point where I am wrong): Avahi is installed on the Ubuntu machines and resolves the address with mDNS. avahi-daemon sends a broadcast packet, which is received by the computer with that host name, and that computer responds with its IP address.

In the case with the Windows host, which does not have Avahi, any address which would otherwise be resolved by Avahi is instead requested from DNSMasq, which queries Google's DNS server (as configured in resolv.conf), which has nothing to show for any .local address.

So how can I get DNSMasq to resolve .local IP addresses with Avahi, like any other application on the system does?

---

### Post by redmk2 on 2010-05-12
> **undecim said:**
> I can use a command like "ping caffeine.local" to ping my laptop, and I see this line: "PING caffeine.local (192.168.1.44) 56(84) bytes of data."

Whenever I use "caffeine.local" on an Ubuntu computer (including the server that is running dnsmasq), that name resolves to 192.168.1.44.

What host is using 192.168.1.44? I assume that DNSMasq is providing the IP address to that host via DHCP.  How have you configured the hostname caffeine and the DNS domain suffix .local?>  

If I want to host a network game that will include Windows hosts, I need to find my IP address and give that to any Windows user that wants to connect.

What is that IP address?  What happens if you use caffeine.local? Is this Windows user on the local LAN?> 

I understand why that is (and please correct me on any point where I am wrong): Avahi is installed on the Ubuntu machines and resolves the address with mDNS. avahi-daemon sends a broadcast packet, which is received by the computer with that host name, and that computer responds with its IP address.

It does?  My understanding is that the Avahi daemon provides IP addresses in the 169.254.0.0/16 network and uses the hostname of the device plus the DNS suffix .local.> 

In the case with the Windows host, which does not have Avahi, any address which would otherwise be resolved by Avahi is instead requested from DNSMasq, which queries Google's DNS server (as configured in resolv.conf), which has nothing to show for any .local address.
DNSmasq does not (if correctly configured) query external DNS servers for the .local DNS domain.  Google's DNS only resolves valid Fully Qualified Domain Names (FQDN) such as: .com, .net, .org, .us, .uk, etc.  If your Windows host is on the LAN then it should resolve local DNS queries via your DNSMasq server only.> 

So how can I get DNSMasq to resolve .local IP addresses with Avahi, like any other application on the system does?

I'm not really sure how to answer your question.  If you are using DNSMasq to provide IP addresses (192.168.1.0/24) then you should setup DNSmasq to resolve the .local domain instead of using Avahi. 

When DNSMasq DHCP is working, Avahi does not provide any services (by design).  I assume that you are using DNSMasq for at least DHCP.  Am I correct?  Avahi does not interact with DNSMasq at all.

---

### Post by undecim on 2010-05-12
> **redmk2 said:**
> What host is using 192.168.1.44? I assume that DNSMasq is providing the IP address to that host via DHCP.  How have you configured the hostname caffeine and the DNS domain suffix .local?

192.168.1.44 is the IP reserved by MAC address for my laptop which is named "caffeine".

.local isn't currently configured. At first, I was trying to configure DNSMasq to use that domain for local addresses like Avahi does, but I know realize that conflicts with Avahi and now have "domain=wake" set in dnsmasq.conf

> **redmk2 said:**
> What is that IP address?  What happens if you use caffeine.local? Is this Windows user on the local LAN?
The IP address is always the same on my laptop, but might not be for someone else's computer. Any Windows host on the local LAN cannot fails to find caffeine.local.

> **redmk2 said:**
> It does?  My understanding is that the Avahi daemon provides IP addresses in the 169.254.0.0/16 network and uses the hostname of the device plus the DNS suffix .local.

If I remove avahi-daemon, .local no longer works. Also, have a look at this:
```
undecim@caffeine ~$ nslookup caffeine.local
Server:		192.168.1.1
Address:	192.168.1.1#53

** server can't find caffeine.local: NXDOMAIN

undecim@caffeine ~$ avahi-resolve-host-name caffeine.local
caffeine.local	192.168.1.44
undecim@caffeine ~$ 

```

clearly, it's Avahi resolving .local addresses.

> **redmk2 said:**
> DNSmasq does not (if correctly configured) query external DNS servers for the .local DNS domain.  Google's DNS only resolves valid Fully Qualified Domain Names (FQDN) such as: .com, .net, .org, .us, .uk, etc.  If your Windows host is on the LAN then it should resolve local DNS queries via your DNSMasq server only.

I have that configured. Currently, the .local addresses resolve only on Ubuntu hosts and .wake addresses don't resolve at all.

> **redmk2 said:**
> I'm not really sure how to answer your question.  If you are using DNSMasq to provide IP addresses (192.168.1.0/24) then you should setup DNSmasq to resolve the .local domain instead of using Avahi.

When DNSMasq DHCP is working, Avahi does not provide any services (by design).  I assume that you are using DNSMasq for at least DHCP.  Am I correct?  Avahi does not interact with DNSMasq at all.

I am currently using DNSMasq for DHCP and DNS, but Avahi is still resolving .local addresses for me. 

Can DNSMasq do something similar to what Avahi is doing, without manually adding hosts to /etc/hosts or dnsmasq.conf?

---

### Post by redmk2 on 2010-05-12
> **undecim said:**
> ...
I am currently using DNSMasq for DHCP and DNS, but Avahi is still resolving .local addresses for me.
Avahi in its default configuration should always resolve .local domain > 

Can DNSMasq do something similar to what Avahi is doing, without manually adding hosts to /etc/hosts or dnsmasq.conf?

Yes it can, but you have to do some configuration and not all of it is documented plainly.  What I mean is: DNSmasq can provide DNS integrated with DHCP.  An overview of what needs to be done is provided in [**_this document_**]("http://www.thekelleys.org.uk/dnsmasq/docs/setup.html").  The man page for DNSmasq provides some insight and you can see it [**_here _**]("http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq-man.html").  There is a fully annotated configuration file [**_here_**]("http://www.thekelleys.org.uk/dnsmasq/docs/dnsmasq.conf.example").

As far as Windows clients are concerned, I believe that all you need is for the COMPUTOR NAME to be configured (Control Panel >> System) and set to "Obtain IP Address Automatically.  The Windows client announces its COMPUTER name which DNSmasq uses as a hostname.

Linux (Ubuntu specifically) is not as easy.  With Ubuntu there are two ways to do this: 
[LIST=1]
[*]Edit the /etc/dhcp3/dhclient.conf file to announce the hostname to the DHCP server
Follow [**_this discussion_**]("http://ubuntuforums.org/archive/index.php/t-367974.html") for an explanation.
  

[*]Edit the /etc/network/interfaces file to announce the hostname to the DHCP server
It should look like this:```
auto eth0
iface eth0 inet dhcp
   hostname myhostname    # hostname to be requested 

```
You can check the man page for more information under options> man interfaces
[/LIST]

Either way, you should make sure that the Ubuntu hostname given the DHCP server matches the name in the /etc/hostname and /etc/hosts files.  if it doesn't then you will have trouble down the road.  X-server will grump about the error and sudo might stop working.

As you say DNSmasq needs to know that .wake is a *local only* domain.  In the conf file find the section listed below.  Change the /localnet/ to /wake/ and uncomment the last line as it is shown.
```
# Add local-only domains here, queries in these domains are answered
# from /etc/hosts or [COLOR="Red"]**DHCP**[/COLOR] only.
local=/wake/

```

When this is done I would reboot the machine.  At that point you should have DNSmasq set up to handle DHCP requests and resolve the .wake domain DNS requests.

---

