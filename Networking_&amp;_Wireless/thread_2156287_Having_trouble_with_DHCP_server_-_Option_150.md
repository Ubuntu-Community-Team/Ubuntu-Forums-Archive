---
title: "Having trouble with DHCP server - Option 150"
date: 2013-06-21
forum: Networking &amp; Wireless
---

### Post by schoolbox on 2013-06-21
I have to set option 150 for my DHCP server so that my Cisco IP phone can function normally.

Here are my dhcpd.conf config.
[FONT=courier new]
option voip-tftp-server code 150=ip-address;
option voip-tftp-server 10.234.0.10;
default-lease-time 7200;

subnet 10.230.144.0 netmask 255.255.255.0{
    option routers 10.230.144.1;
    option subnet-mask 255.255.255.0;
    option domain-name-server 8.8.8.8, 8.8.4.4;
    pool{
        range 10.230.144.21 10.230.144.230;
    }

}
[/FONT][FONT=arial]
[/FONT]It seems that my device can't connect to tftp server.

after using wireshark to sniff DHCP ACK package, i found out that there are no info. about option 150.

this is the result from wireshark

[IMG]http://img546.imageshack.us/img546/2797/6d2v.png[/IMG]


Need help or advices.

---

### Post by schoolbox on 2013-06-21
SOLVED!!

Finally found out that custom option won't be send,

so I did a little command to force it to send

I add the following 
[COLOR=#000000]
[FONT=courier new][I]if exists dhcp-parameter-request-list {
      option dhcp-parameter-request-list=concat(option dhcp-parameter-request-list,96);
[/I][/FONT][FONT=verdana][FONT=courier new]*}*[/FONT]

Note: 96 is the number of your custom dhcp option in HEXADECIMAL ex. mine is 150 so the number should be 96[/FONT][/COLOR][COLOR=#000000][/COLOR]

---

