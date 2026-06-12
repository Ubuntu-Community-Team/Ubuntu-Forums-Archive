---
title: "change dns server with Intrepid dhcp"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by shane2peru on 2009-03-04
Ok, I have done this in the past, however intrepid has changed the way that it works with the Network manager.  So my question is simple. How do I permanently change my dns to always use OpenDNS?  I used to edit /etc/resolv.conf or another file, however now that always gets overwritten.  I have ddclient installed, and that keeps my ever changing (wireless roaming laptop) ip address up to date with OpenDNS, however, my laptop doesn't use their dns numbers, so ddclient is null and void.  How do I get my laptop to always use Opendns numbers even with dhcp enabled?  Is this possible?

Shane

---

### Post by albandy on 2009-03-04
Modify your /etc/dhcp3/dhclient.conf
activate "prepend  domain-name-servers 127.0.0.1" and modify 127.0.0.1 to your dns servers 
then delete domain-name-servers from the request line
```


# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
[COLOR="DarkRed"]prepend domain-name-servers 192.168.1.1 192.168.1.2; #here is the line you have to modify and activate[/COLOR]
[COLOR="DarkRed"]request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu[/COLOR];  #here is the line you should remove domain-name-servers
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

---

### Post by Iowan on 2009-03-04
The "prepend'ed" nameservers should be at the top of the list, whether you remove the request line or not... but it's cleaner the suggested way.

---

### Post by shane2peru on 2009-03-04
Thanks guys!!!  I did that and I think it is working.  I will have to check later.  Much appreciated.  

Shane

---

### Post by shane2peru on 2009-03-18
ok, I did this, and it seems as though it still doesn't default to using the dns that I have put in there.  When I click on the connection in the beside the clock and click on "connection information" it shows my ip address as the dns odd.  Here is my file:

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

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
[COLOR="Red"]prepend domain-name-servers 208.67.220.220 208.67.222.222; #I edited this line to open DNS servers[/COLOR]
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-search, host-name, #removed domain-name-servers
	netbios-name-servers, netbios-scope, interface-mtu;
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

If you see anything I would appreciate the help!  I marked in red what I added.  Thanks guys!

Shane

---

### Post by helgman on 2009-03-18
There is an option in the NetworkManager that let's you use DHCP with your own predefined DNS-server. Just edit your setting and change IPv4 settings to "Automatic (DHCP) addresses only" and then put in the wanted IP for DNS-servers. Worked last time I tried it.

Regards,
Helgman

---

### Post by shane2peru on 2009-03-18
> **helgman said:**
> There is an option in the NetworkManager that let's you use DHCP with your own predefined DNS-server. Just edit your setting and change IPv4 settings to "Automatic (DHCP) addresses only" and then put in the wanted IP for DNS-servers. Worked last time I tried it.

Regards,
Helgman

Helgman,

Thanks!!!  Yes, this seems to be the answer.  Matter of fact here is the how to:  [https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)   Thanks for the reply.  Does anyone know how to automate this process for every wireless network?  Or do I have to set it up for every single wireless network?  When you are with a laptop and traveling, you connect to a lot of wireless networks.

Shane

---

