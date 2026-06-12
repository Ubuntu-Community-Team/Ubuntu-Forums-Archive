---
title: "Force ubuntu to use certain DNS"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by baltazar3 on 2010-01-05
I have a VPN tunnel set up, and would like Ubuntu to only do DNS lookups via the VPN provider. I tried to do this:

Set up static ip, by setting /etc/network/interfaces to this:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.1.0
broadcast 192.168.1.255
```Doing sudo /etc/init.d/networking restart

Then setting /etc/resolv.conf to 
```
nameserver [dnsserver1]
```Problem is, after a couple of hours resolv.conf get rewritten to:
```
domain lan
search lan
nameserver 192.168.1.1
```And then all DNS queries get sent to my router. What process is changing my DNS settings, and what should I do to set up static DNS?

Im using Ubuntu 9.04 server.

---

### Post by prshah on 2010-01-05
> **baltazar3 said:**
> would like Ubuntu to only do DNS lookups via the VPN provider

You can edit your /etc/dhcp3/dhclient.conf, and add the VPN's DNS servers to the "prepend" line; this will ensure that the VPN's DNS servers are used everytime.

From a terminal:
```
sudo nano /etc/dhcp3/dhclient.conf
```

look for a line like ```
#prepend domain-name-servers 127.0.0.1;
``` and change it to read```
prepend domain-name-servers [color=red]208.67.220.220 208.67.222.222[/color];
``` (Remember to remove the "#" commenting out the line in the beginning, or there will be no effect). Please change the server addresses in [color=red]red[/color] to reflect the DNS servers you want. Multiple addresses are separated with spaces, and the line ends with a ";" semicolon.

To test, you can either restart, or relogin, or just give the command```
sudo /etc/init.d/networking restart
```

---

### Post by baltazar3 on 2010-01-05
> **prshah said:**
> You can edit your /etc/dhcp3/dhclient.conf, and add the VPN's DNS servers to the "prepend" line; this will ensure that the VPN's DNS servers are used everytime.

That was the first thing I tried. I set the prepend directive and also removed domain-name-servers from request line in the same file. But resolv.conf got changed anyway. That's why I thougt that I should use static instead of dhcp.

It may be something that happens when the vpn line goes down then up again, but I dont know what scripts etc gets called when this happens.

Edit: Forgot to add that Im using openvpn as a client.

---

### Post by slakkie on 2010-01-05
You can also set dns-* options in your interfaces file. Or change the hooks on openvpn so it writes the correct DNS entries.

```

    dns-domain euronet.nl
    dns-search  euronet.nl wanadoo.nl online.nl
    dns-nameservers 194.134.5.5 194.134.0.97

```

This makes sure my DNS entries are always correct :)

---

### Post by suseendran.rengabashyam on 2010-01-05
Hi,

   I think it would be nice if you look at the "supersede domain-name-servers x.x.x.x;" 

option in /etc/dhcp3/dhclient.conf .


     Further details are there in the following link


     [http://ubuntuforums.org/archive/index.php/t-191239.html](http://ubuntuforums.org/archive/index.php/t-191239.html)
                   [URL="http://10.10.43.151:3000/issues/show/44#"]
[/URL]

---

### Post by prshah on 2010-01-05
> **suseendran.rengabashyam said:**
> 
"supersede domain-name-servers x.x.x.x;" 


supercede and prepend do _mostly_ the same thing; the primary difference between the two is that the prepend option will ensure that your supplied servers are contacted _first_ for DNS resolution, and then it will fallback to the servers supplied by a DHCP negotiation.

supercede will not have any fallback; it will always use the supplied DNS servers.

I don't know how valid it will be when you try to use a non-VPN connection; eg a mobile Internet connection or so.

---

### Post by baltazar3 on 2010-01-05
Ok trying with supersede now.

Am I supposed to use dhcp client at all though when the network interface is configured to be static? 

Its a bit difficult to test as resolv.conf only gets overwritten once every few hours. Is there any way to provoke the dhcp client to try to rewrite resolv.conf? Restarting the network with /etc/init.d/networking restart dosent overwrite it.

---

### Post by baltazar3 on 2010-01-05
I added 
```
supersede domain-name-servers [vpn providers dns]
```to /etc/dhcp3/dhclient.conf

But resolv.conf still gets overwritten.

---

### Post by suseendran.rengabashyam on 2010-01-06
Hi,
   I stumbled upon the following link


   	[http://www.subvs.co.uk/openvpn_resolvconf](http://www.subvs.co.uk/openvpn_resolvconf)
[URL="http://www.subvs.co.uk/openvpn_resolvconf"]
[/URL]
   	Let me know if this helps you.

---

### Post by Iowan on 2010-01-06
I saw one thread that solved a similar problem by installing **resolvconf** and another that solved the same symptoms by removing it.

---

### Post by baltazar3 on 2010-01-07
I solved the problem by following the advice in comment #31 of this thread: [http://www.debian-administration.org/article/An_introduction_to_Debian_networking_setup](http://www.debian-administration.org/article/An_introduction_to_Debian_networking_setup)

Basically the problem was that editing /etc/network/interfaces then doing /etc/init.d/network restart isnt enough to shutdown the dhcp client. Instead I started from a dynamic network configuration and then run:
/etc/init.d/networking stop
changed /etc/network/interfaces to static 
/etc/init.d/networking start

Then checked that dhcp client was really stopped with ps -e | grep dhc.

---

### Post by papibe on 2010-03-29
I just wanted to let you know that while trying so solve the same problem, I learned (by trial and error) the correct syntax of the supersede option on the dhclient.conf file.

You have 2 options:

```
supersede domain-name-servers 208.67.222.222;
append    domain-name-servers 208.67.220.220;
```

or

```
supersede domain-name-servers 208.67.222.222, 208.67.220.220;
```

[SIZE="1"][INDENT](Note the comma. If you just separate the addresses by space or use quotation marks [FONT="Arial Black"][COLOR="DarkRed"]DOES NOT[/COLOR][/FONT] work).[/INDENT][/SIZE]

This way I successfully replace my slow and unreliable ISP's DNS by one that has been working OK for me (OpenDNS) ;).  

Regards,

---

