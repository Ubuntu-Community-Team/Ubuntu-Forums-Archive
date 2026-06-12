---
title: "VM network bridge: Why Lookup see different IP than router?"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by UranUtan on 2009-02-25
Hi,

Using Ubuntu 8.10 x32, system up to date.
VirtualBox 2.14
2 VM running simultaneously, guest OS = Windows 2008
all machines (Ubuntu host and the two VM) acquire IP via DHCP of the router.

My network subnet is 192.168.1.x. Each machine works OK. Acquires dynamic IP, Internet, VirtualBox Shared folder, etc.

Ping works only if I specify an IP (example: ping 192.168.1.110). Each machine can ping the other OK.

However it doesn't work if I ping by computer name (ping from within VM, Win 2008):
```

ping MyHostName

Pinging MyHostName.MyRouter2 [208.67.217.132] with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
Request timed out.
```

Note: MyRouter2 is the domain name I set in the router.

[COLOR="Red"]**Q1.**[/COLOR] Where does the 208.67.217.132 IP come from?

Using network Tools of the Ubuntu host, Lookup utility. I specify the name of the VM (example: MyVM2) and hit the "Lookup" button, the results displayed is:

Name: MYVM2.MyRouter2
TTL: 0
Address Type: IN
Record Type: A
Address: 208.67.217.132

Strangely enough the 208.67.217.132 IP appears again. And this time from a different machine.

[COLOR="Red"]**Q2.**[/COLOR] How come ping or Lookup cannot see the 192.168.1.x subnet?

Thanks in advance for any help.

---

### Post by UranUtan on 2009-02-26
Please any network expert can help?

Router DHCP serves IP in the 192.168.1.x, all the OS (host or guest in VM) resolve the other machines name (located in the same subnet) with 208.67.217.132

There should be an obvious technical reason somewhere, can you please give me some leads so I can dig in further documentation / reading?

---

### Post by capscrew on 2009-02-26
Its not resolving the address at all.  The address is for one of the OpenDNS servers.  The 208.67.217.132 address has been setup as the address to forward all DNS requests that can't be resolved locally.

If I try to resolve a unknown name I have the same response as you did.  Note that I use a different DNS server.  See below:```
capscrew@lathe~$ ping differentname
PING differentname (63.251.179.13) 56(84) bytes of data.
 Request timed out.
 Request timed out.
 Request timed out.
 Request timed out.
--- differentname ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms

```

---

### Post by UranUtan on 2009-02-26
Ah ok make sense. However, what is the reason the machines within the same subnet cannot see each other by name ?

---

### Post by capscrew on 2009-02-26
> **UranUtan said:**
> Ah ok make sense. However, what is the reason the machines within the same subnet cannot see each other by name ?

No LOCAL name resolution.

You could use the DNS server in your router (if it has one) to resolve LOCAL addresses, but you can also resolve DNS on the Ubuntu server with the /etc/hosts file. You would need this file on each host in your network if you wanted to resolve names from them all.  Here is an example of an /etc/hosts file.
```

# Manually configured local hosts
127.0.0.1 localhost
# router and Wireless AP 
192.168.1.1 rtr
192.168.1.2 wap

# local computers
192.168.1.12 lathe
192.168.1.20 mill
192.168.1.22 drill

# Networked LJ Printer
192.168.1.200 printer

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

As you can see, the format is:
```
IP Address hostname
```

In addition there is a great lightweight DNS sever named DNSmasq that I like. It uses an /etc/host file too.  The advantage is you only need it on the host with DNSmasq. 

The heavy duty DNS sever is BIND, but I believe that is overkill for your situation.

---

### Post by UranUtan on 2009-02-26
> **capscrew said:**
> No LOCAL name resolution.
Oh really? When I installed Windows machines at home in a workgroup, they see each other by the ComputerName. May be Windows does something extra behind the scene.

Thanks for the info you provided. Just curious, if local name cannot be resolved, and I use dynamic IP. The hosts file is not guaranteed to be always accurate. I can of course set the machine to use static IP. Generally for people who use dynamic IP, is there anyway to resolve local computer names?

BTW in Ubuntu how to set the network interface to use static IP? Disable Roaming mode and set the IP + Gateway directly?

---

### Post by capscrew on 2009-02-26
> **UranUtan said:**
> Oh really? When I installed Windows machines at home in a workgroup, they see each other by the ComputerName. May be Windows does something extra behind the scene.

Yes really. A Windows workgroup defines a browsing domain not a naming domain.  Windows can use Netbios (WINS) for resolving computer names.  My windows hosts use use DNS for naming, but can use WINS.  I have no WINS server in my network. 

> 
Thanks for the info you provided. Just curious, if local name cannot be resolved, and I use dynamic IP. The hosts file is not guaranteed to be always accurate. 

This is true.  You didn't specify DHCP. [COLOR="Red"]Edit:  i just reread and saw your reference to DHCP -- ooops.  [/COLOR] If you need to use DHCP then I would reserve the address for the host by MAC address.  This will allow you to have a permanently assigned (consistent) IP address and use the host file. 
> 
I can of course set the machine to use static IP. Generally for people who use dynamic IP, is there anyway to resolve local computer names?

There are other ways to resolve hostnames dynamically.  Active directory does can do it.  so can BIND, but it's a real pain. 
> 

BTW in Ubuntu how to set the network interface to use static IP? Disable Roaming mode and set the IP + Gateway directly?

I have never used NM or GUi interfaces.  The NIC (eth0) is setup with the /etc/network/interfaces file (IP + Gateway) and the DNS is setup with the /etc/resolv.conf file.  i have heard that folks need to remove NM to be able to permanently configure the IP addressing manually.

---

