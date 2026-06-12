---
title: "2 Nics, 2 domains, DNS setup help"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by Damned1 on 2012-01-12
I have a server that sits between 2 completely separate domains. One is our internet facing, the other is our secure side. The server that sits in between is our backup server running Bacula. This backup server has 2 NICs. one assigned to each domain. I would like to have this backup server check names against each domain's DNS. I am very new to Linux and have been getting by on tutorials and what not, but I can not seem to find anything on this. If I just add them to resolve.conf, then all of the requests go through the default NIC instead of checking both of them. I may just have it setup wrong as well. 

Would someone mind posting an example of how I would accomplish this?

---

### Post by jonobr on 2012-01-12
Hello

Does Putting in
```

nameserver <ipaddress network A>
nameserver <ipaddress networks B>
```

in resolv.conf not work?
I thought that when you look up based on name
It would try nameserver A fail and then try B.

I dont know if this would somehow have security implications but I guessing it could work.

I think a better way may be to host your own DNS and have name resolution that way ?

---

### Post by Damned1 on 2012-01-12
I went back and looked at my resolv.conf and it appears that network manager is removing any changes I make to it. Something new to puzzle over. I'll try to get teh changes to stick.

---

### Post by Damned1 on 2012-01-12
So what happens is, when I restart the network-manager server after I have manually entered in each NICs info, it send all of the DNS requests through the default NIC instead of sending it out through both of the NICs. So only the default NIC's DNS is getting quarried. 

One NIC IP address 192.*.*.* cannot talk to our secure side 10.*.*.*  so I guess what I need to know is how to have Ubuntu send the DNS request out on one NIC then the other or both at once instead of tunneling all of the traffic through the default NIC which would not be able to contact the DNS server on the other domain.

---

### Post by jonobr on 2012-01-12
Hello

If your using nm applet it will always overwrite entries in the /etc/resolv.conf file, A lot of people (including me) just disable nm and configure files by hand,

If you put in the second entry in the nm applet it should write to the resolv.conf file.

if your first dns is in the 192 network it should route to the first nic and same for the second dns.

Again assuming you have two dns in the two different subnets,

If thats not working there, I think you need to look at your routing table to see why its not doing that.

using the route command

---

### Post by Damned1 on 2012-01-12
```

admistrator@ubunback:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.128.50.0     *               255.255.255.192 U     1      0        0 eth1
192.9.200.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         sonicwall.offic 0.0.0.0         UG    0      0        0 eth0

```I ended up just adding my secure pcs in my host file. All of the dns requests ran through eth0 which is my default nic, so everything on my unsecured side would resolve just fine. every time I would ping a short name for anything that resides on eth1, it would come back saying unknown host. My guess is because eth0 is the default, it is sending all dns requests through eth0 and not eth0 and eth1. I can ping IPs on either side just fine, it is just a problem with short names. Adding everything on eth1 to /etc/hosts works fine, just not quite what I was hoping for.

Anyways, thanks for your time.

---

### Post by jonobr on 2012-01-12
Yep, thats too bulky and will be a gotcha for any new admin.

The first part I expected,

The dns resolution would go from the box to the nameserver no matter the query.

I figured the two addresses in the resolv.conf would mean it would go out the first one (your eth0) lookup, fail and then maybe go to the second.

After doing some reading, thats not what will happen.

It will go out to the first, fail resolution and thats it.

It will only go to the second one if the first times out.

Its a sad day you dont learn something.

Anyway, I am thinking the best way forward is probably your won dns hosted on that machine.. a lot of effort if your not used to DNS , but more streamline

---

### Post by chrisguk on 2013-01-18
Hi,

I realise you found a solution but the hosts find method is not really required.

If you have a server it would be right to assume that it needs a static IP, naturally.  Therefore the following packages are not required and can be safely removed;

```


sudo apt-get remove network-manager network-manager-gnome resolvconf


```

Once you have done this update your /etc/interfaces with the same format as below:

```


auto eth0
iface eth0 inet static
        address 192.168.178.130  
        netmask 255.255.255.0 
        network 192.168.178.0 
        broadcast 192.168.178.255
        gateway 192.168.178.1 

        # dns-* options are implemented by the resolvconf package, if installed
        dns-search domain.com.
        dns-nameservers 192.168.178.130

auto eth1
iface eth1 inet static
        address 192.168.178.20
        netmask 255.255.255.0
        network 192.168.178.0
        broadcast 192.168.178.255
        gateway 192.168.178.1

        # dns-* options are implemented by the resolvconf   package, if installed
       dns-search seconddomain.com.
       dns-nameservers 192.168.178.20


```

Then update your resolv.conf with the required syntax, which should be:

search  yourdomain.com
nameservers xxx.xxx.xxx.xxx

I have that setup and it works fine

---

### Post by jdthood on 2013-01-19
> **jonobr said:**
> 
Does Putting in
```

nameserver <ipaddress network A>
nameserver <ipaddress networks B>
```

in resolv.conf not work?

No, that won't do what he wants.

---

### Post by jdthood on 2013-01-19
> **jonobr said:**
> If you put in the second entry in the nm applet it should write to the resolv.conf file.

if your first dns is in the 192 network it should route to the first nic and same for the second dns.

The OS will route 192* traffic to the 192* NIC and 10* traffic to the 10* NIC, but the resolver will not route requests to 192* or 10* depending on the domain name.

---

### Post by jdthood on 2013-01-19
> **chrisguk said:**
> Therefore the following packages are not required and can be safely removed;

```

sudo apt-get remove network-manager network-manager-gnome resolvconf

```

Once you have done this update your /etc/interfaces with the same format as below:

```


auto eth0
iface eth0 inet static
        address 192.168.178.130  
        netmask 255.255.255.0 
        network 192.168.178.0 
        broadcast 192.168.178.255
        gateway 192.168.178.1 

        # dns-* options are implemented by the resolvconf package, if installed
        dns-search domain.com.
        dns-nameservers 192.168.178.130

```


If you have removed the resolvconf package then you can also remove the dns-* options from /etc/network/interfaces since those options are implemented by the resolvconf package.

Having said this, it is not advisable to remove the resolvconf package. Resolvconf is part of the base install of Ubuntu Desktop *and* Server since version 12.04.

When resolvconf is installed and a dns-nameservers option is included for an interface in /e/n/i, the addresses listed after 'dns-nameservers' are added to resolv.conf when the interface is brought up and removed when the interface is taken down.

Even if you really want /etc/resolv.conf to be a static file, it is best to leave the resolvconf package installed. The reason is that the presence of the resolvconf package causes various other packages not to futz with /etc/resolv.conf. Just remove the symbolic link at /etc/resolv.conf and put a static file there. The resolvconf package won't touch it (unless you do "sudo dpkg-reconfigure resolvconf").

---

### Post by jdthood on 2013-01-19
> **Damned1 said:**
> My guess is because eth0 is the default, it is sending all dns requests through eth0 and not eth0 and eth1.

That is right. The resolver can't route DNS requests by domain name suffix.

There is a way to achieve what you want without entering all your  private domain names into /etc/hosts. The dnsmasq nameserver is capable of routing DNS requests by domain name suffix. With, for example, the options
```

    --server=8.8.8.8 --server=/internal/1.2.3.4

```
dnsmasq will look up *internal names in the nameserver at 1.2.3.4 and all others in the nameserver at 8.8.8.8.

---

