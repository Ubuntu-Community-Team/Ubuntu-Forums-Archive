---
title: "Locking /etc/resolv.conf"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by cryptodan on 2009-08-19
How do I go about locking the /etc/resolv.conf file so that my statically assigned name servers are always there, and so that network manager doesn't change it?

---

### Post by movieman on 2009-08-19
You can do it by removing write permission, but you need to do so in such a way that root still can't overwrite the file: there's a special command for that, but I can't remember what it is.

Edit: ah, here it is: chattr +i /etc/resolv.conf

---

### Post by scorp123 on 2009-08-19
> **cryptodan said:**
> How do I go about locking the /etc/resolv.conf file so that my statically assigned name servers are always there, and so that network manager doesn't change it?

Take a look in the **/etc/dhcp3** directory ... There should be a file called **dhclient.conf**

You have to temporarily become "root" to be able to change that. So if you're OK with the shell and e.g. "vi" you'd type this into a terminal:
```
sudo vim /etc/dhcp3/dhclient.conf
``` ... Any other editor such as "nano" should work too.

If you prefer to do this in the GUI:
```
gksudo gedit /etc/dhcp3/dhclient.conf
```

KDE users would have to use this I guess (not sure as I don't use KDE):
```
kdesu kate /etc/dhcp3/dhclient.conf
```


When the file is open it will look something like this --- mine is customized and you'll easily spot the differences (highlighted with colors):

```
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
# prepend domain-name-servers 127.0.0.1;

[B][COLOR="Red"]#
# added by sysadm
#
prepend domain-name-servers 192.168.1.2,192.168.1.3;
[/COLOR][/B]
request subnet-mask, broadcast-address, time-offset, routers,
[COLOR="SeaGreen"]**	domain-name, domain-name-servers, domain-search, host-name,**[/COLOR]
#
# if /etc/resolv.conf still keeps getting the wrong DNS servers
# despite the "prepend" statement above, then uncomment the
# next line and put a '#' in front of the corresponding line above!
#
**[COLOR="Red"]#	domain-name, domain-search, host-name,[/COLOR]**
	netbios-name-servers, netbios-scope, interface-mtu,
	rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

See the coloured stuff above? You can leave out the comments if you like (I personally prefer to keep them so I know who changed what and why ...). But basically you can statically assign your own DNS servers with the ***prepend*** statement above and you can force DHCP to ignore any other DNS servers that it might be informed about (the next coloured section).

Please be aware of the consequences: If you're running a laptop then manipulating **dhclient.conf** in such a way makes little sense. Because even if you move between networks your DHCP client would now default to DNS servers it probably won't be able to reach depending on the network.

On the other hand the manipulations above might make sense if you have a desktop (that's never moving around) and actually will always use the same DNS servers but for some odd reasons NetworkManager keeps getting the DNS servers wrong.

I hope this helped.

---

### Post by cryptodan on 2009-08-19
I have statically assigned my IP via installation, yet it still pulls dns information from the dhclient.conf?

---

### Post by scorp123 on 2009-08-19
> **movieman said:**
> in such a way that root still can't overwrite the file What you suggest is the wrong way to do it.

---

### Post by scorp123 on 2009-08-19
> **cryptodan said:**
> I have statically assigned my IP via installation, yet it still pulls dns information from the dhclient.conf? Only if you run DHCP. If you have a static IP setup then it shouldn't do that. Can you please post your **/etc/network/interfaces** file?

---

### Post by cryptodan on 2009-08-19
> **scorp123 said:**
> Only if you run DHCP. If you have a static IP setup then it shouldn't do that. Can you please post your **/etc/network/interfaces** file?

That is all I have in my interface file.

auto lo
iface lo inet loopback

---

### Post by scorp123 on 2009-08-19
> **cryptodan said:**
> That is all I have in my interface file.

auto lo
iface lo inet loopback You're running DHCP then. If you had static IP's then there would be a section saying so.

Example with static Ethernet interfaces:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
name Ethernet0
address 192.168.20.98
netmask 255.255.255.0
broadcast 192.168.20.255
network 192.168.20.0

auto eth1
iface eth1 inet static
name Ethernet1
address 192.168.24.58
netmask 255.255.255.192
broadcast 192.168.24.63
network 192.168.24.0

```

---

### Post by Iowan on 2009-08-19
It _IS_ possible to set up a static (manual) address via Network Manager.

---

### Post by cryptodan on 2009-08-20
> **scorp123 said:**
> You're running DHCP then. If you had static IP's then there would be a section saying so.

Example with static Ethernet interfaces:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
name Ethernet0
address 192.168.20.98
netmask 255.255.255.0
broadcast 192.168.20.255
network 192.168.20.0

auto eth1
iface eth1 inet static
name Ethernet1
address 192.168.24.58
netmask 255.255.255.192
broadcast 192.168.24.63
network 192.168.24.0

```

Does it matter what I put in for the name?

---

### Post by Iowan on 2009-08-20
> **cryptodan said:**
> Does it matter what I put in for the name?

Name?? eth0, eth1, or wlan0, etc.? Yes, it will. **ifconfig -a** will show which interfaces are available. **lshw -C network** will provide more details.

---

