---
title: "[SOLVED] DNS issue?"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by Don Giovanni on 2009-01-08
*update* figured it out
even though i was certain NetworkManager had been uninstalled long ago somehow in the update my /etc/resolv.conf file got overwritten with a blank file.
added my DNS address back in and good too go :P  Always overlook something silly...
For those of you that might be looking at this for answers of your own. Here is all that is added (the ip is specific to my ISP, just replace with your ISP or OPEN DNS server IP)
/etc/resolv.conf
```

nameserver 142.161.2.155

```


----------------------------------
I have had this system running with a static IP since Feisty.
Currently running 8.10 intrepid ibex.
A few hours ago i installed a bunch of updates and rebooted (among the updates was an new video card driver)

After boot I could no longer access web pages by domain name.

I can ping and run trace routes with IPs just fine and I can even pull up web pages in firfox using IP addresses.

As far as I can tell my configs look fine.

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.300
netmask 255.255.255.0
gateway 192.168.1.1

#iface eth1 inet static
#address 192.168.1.400
#netmask 255.255.255.0
#gateway 192.168.1.1
```
This may or may not be related to the issue but I have two onboard NICs they used to show up as eth0 and eth1 under Network Tools Devices section.  Eth1 no longer shows up and the second nic will not light up when i connect an ethernet cable to it instead, so I thought i would try commenting it out in my interfaces (didn't change anything).

/etc/dhcp3/dhclient.conf
```
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 142.161.2.155, 142.161.130.155;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, domain-search, host-name,
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

I have searched for an answer but had no luck, and was forced to boot into windows for the first time in 2 years.  I tested both NICs with the specified static ip, gateway and DNS info and they work just fine.

Any ideas why i can no longer resolve domains in ubuntu?

---

### Post by shane2peru on 2009-07-01
This has started happening to me after reboot.  When I reboot, the /etc/resolv.conf file is overwritten by a blank file.  This is really annoying.  Does anyone know why this is?  Is this a bug?  Or is it just a fluke?  Did I mess something up?  This is annoying.  

I'm running Ubuntu Jaunty 64bit.

Shane

---

