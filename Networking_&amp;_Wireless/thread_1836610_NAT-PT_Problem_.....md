---
title: "NAT-PT Problem ...."
date: 2011-08-31
forum: Networking &amp; Wireless
---

### Post by dashang.trivedi on 2011-08-31
My objective :
internal network of ipv4 reach   IPv6 nodes on the Internet....
i don't  have Cisco device...so i m trying with  [http://tomicki.net](http://tomicki.net)   naptd-0.4.2.tar.gz....
i have install naptd....now for configuration.....

```
[root@manage newroot]# usr/sbin/naptd-confmaker 
Ataga IPv4/IPv6 NAPT Configuration Maker
(c) 2005 by Lukasz Tomicki <tomicki@o2.pl>

Do you want to create a new configuration? [Y/n]

Do you want IPv4 addresses from the outside interfaces to be automatically used as part of the NAT pool? [Y/n]

Do you want to configure additional address as part of your NAT pool? [y/N]

Do you want to create a pool of public IPv4 addresses that will allow incoming connections to be dynamically mapped to appropriate IPv6 addresses? [y/N]

Do you want to create static mappings of public IPv4 addresses that will allow incoming connections to reach IPv6 hosts? [y/N]

Enter the name of the first inside (IPv6) interface that you want NAT-PT to listen on.
interface (eth0 eth1 eth2 eth3 eth4 eth5 eth6 eth7 eth8 eth9 eth10 eth11): eth7

Do you want to enter more interfaces? [y/N]
n
Enter the name of the first outside (IPv4) interface that you want NAT-PT to listen on.
interface (eth0 eth1 eth2 eth3 eth4 eth5 eth6 eth7 eth8 eth9 eth10 eth11): eth5

Do you want to enter more interfaces? [y/N]
n
Enter the TCP translation timeout in seconds [86400]: 
Enter the UDP translation timeout in seconds [3600]: 
Enter the ICMP translation timeout in seconds [30]: 

Enter the IPv6 prefix that will be used as the destination for translations.
prefix [2000:ffff::]: 

Please enter the IPv4 address of the DNS server you are currently using.
IPv4 DNS server: 10.104.1.1

You can configure hosts for automatic DNS translation by using the DNS server below.
IPv6 DNS Server: 2000:ffff::a68:101

Thank you for choosing Ataga as you IPv4/IPv6 NAT-PT solution.
Setup is now complete. Type 'naptd' to start NAT-PT.


```

Now hows its done.......

My eth5 ipv6 is  2000:470:1f01:115::4/64

eth7  which is ipv4  is 10.10.7.1......... and connected pc with this ip PC-1 ---> 10.10.7.2



[b]Now as per the concept if i ping from  PC-1 to any other machin...so in that machin it should be dispaly IPV6 in tcpdump...But NATING is not working perfectly.....
please suggest me how to done NATING in IPV6 case....[/b]


sorry for english..

---

