---
title: "DNS DHCP DDNS with seperate files/subdomain"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by c0mputerking on 2011-02-21
Ok i bit off a more than i can chew with this one hoping for some help here.  I am running Ubuntu 10.04.2 LTS server edition.

I have DNS, and DHCPD setup and working however i would like to get DDNS working so DHCPD can update my DNS records.  However i would like to keep the dynamic records separate from the static ones.  I have tried to do this by creating a separate subnet however i am new to subnets. things are sort of working only the dynamic machines 192.168.2.0 cannot get to the inet, and cannot be pinged or accesses from the LAN or THE WAN. Below is a poorly illustrated diagram of my network as it stands, also a bunch of config and database files. 

 INET X.X.X.X
         I
         I
 eth0 static IP from ISP
         I
Ubuntu server / nat /firewall / dhcp / dns 
         I
 eth1 static IP for LAN
         I
         I
Dumb switch 
         I
         I
Local Network -------- I       
       I                       I
       I                       I
192.168.1.0         192.168.2.0
 solar.lan              dyn.solar.lan
static clients       dynamic clients
inet working       inet not working

##########
Should 192.168.1.1 be able to ping 192.168.2.1 ??? I have inet on 192.168.1.0 why no inet on 192.168.2.0 do i need to add a route ??? or a virtual interface or something ??? I am super confused here !!! maybe i am going about this wrong do i even need the subnet of 192.168.2.0???

PS i get errors permission denied during forward mapping in the logs
##########

#### here is important bits of my /etc/network/interfaces do i need a virtual iface here to change my netmask or route or something
auto eth1
iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0
#       network 192.168.1.0
#       broadcast 192.168.1.255

#### important bits of /etc/dhcp/dhcpd.conf not sure if i need to match up all the stuff in my /etc/network/interfaces better

ddns-domainname "dyn.solar.lan";
option domain-name "solar.lan dyn.solar.lan";
option domain-name-servers 192.168.1.1, 64.59.135.133, 64.59.135.135;
option routers 192.168.1.1;
option broadcast-address 192.168.255.255;
option ntp-servers 192.168.1.1;

subnet 192.168.0.0 netmask 255.255.0.0 {
range 192.168.2.100 192.168.2.150;

# Communication zone??
zone dyn.solar.lan {
  primary 127.0.0.1;
  key dhcpupdate;
}

# DNS zones to update
zone 2.168.192.in-addr.arpa. {
primary 192.168.1.1;
key "dhcpupdate";
}

zone dyn.solar.lan. {
primary 192.168.1.1;
key "dhcpupdate";
}

#### DNS config file named.conf zone files seemed like a bit much ( i can add them here if needed ) however i would like mention that i have this entry in the 192.168.1.hosts file as i read about it in the dns and bind book.

; Interface specific devices
wh1.redwingshoes.lan.           IN      A       192.168.1.1
wh2.redwingshoes.lan.           IN      A       192.168.2.1

# Zone for static hosts
 zone "solar.lan" in {
        type master;
        file "/etc/bind/192.168.1.hosts";
        notify yes;
        };

zone "1.168.192.in-addr.arpa" in {
        type master;
        file "/etc/bind/192.168.1.rev";
        notify yes;
        };

# Seperate zone for dynamic hosts
zone "dyn.solar.lan" in {
        type master;
        file "/var/lib/bind/192.168.2.hosts";
        allow-update { key dhcpupdate; };
        notify yes;
        };

zone "2.168.192.in-addr.arpa" in {
        type master;
        file "/var/lib/bind/192.168.2.rev";
        allow-update { key dhcpupdate; };
        notify yes;
        };

---

