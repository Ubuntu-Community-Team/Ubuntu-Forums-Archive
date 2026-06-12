---
title: "Netgear Router in DHCP Settings"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by intermentals on 2010-01-17
As will be apparent from the following questions I'm obviously new to setting up routers etc 

I'm currently setting up my laptop as a server (9.10), it is not currently connected to any router

I have 2 questions:

in the dhcpd.conf file I have "option routers" set to 192.168.2.13 which is the IP address of the laptop - this was just a guess as I don't have a router installed so is this right for a set up without a router?

What should I set the "option routers" to when I connect the machine to the netgear router that I have?

dhcpd.conf:

authoritative;

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.2.13;
option domain-name-servers 192.168.2.13, 192.168.1.3;

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.200;
}

---

### Post by Iowan on 2010-01-17
The "option routers" should probably point to the next upstream machine - either your router - or the ISP's.

---

### Post by MarkC502 on 2010-01-17
You will need to specify the IP address of the Netgear router on your IPv4 LAN network as the router address on the laptop not the laptops IP. When you setup a PC to work with a router a few things have to be right in the router settings and the PC settings.

THESE ARE SETTING THAT NEED TO BE TRUE ON BOTH PC & ROUTER LAN SETTINGS

In your router you will have LAN & WAN settings LAN is your local network of PC's with IP's like 192.168.0.XX WAN is the internet connection and will have an internet IP never 192.168 anything. Its the router LAN section that needs to match the same rules as the PC you intend to run as a server.

1. They need to be on the same IP scheme ( I.E. the first 3 sets of numbers 192.168.0 for example ) . If router is 192.168.1.1 and your laptop is 192.168.2.100 this would not work.

2. They should be on the same net mask ( almost always 255.255.255.0 ) 

3. For DNS on the laptop you should be able to use the IP of your router as it should be serving up DNS from your ISP already ( if you can connect with a windows pc through this router then I bet all in that your router is serving DNS at its IP 95% do afterall). If you can't connect with other PC's through this router then you should config your dns server addresses in your routers general settings page.

Here are 2 DNS server addresses that work 100% as they are the OpenDNS servers and are free for all to use and have been up for years, if you ever need to test if your current dns server is a problem then you can use these and if it doesn't work with these then look elsewhere for the problem :-)

[B]                 208.67.222.222
                208.67.220.220             [/B]

                                        

Note to access ports you need for your webserver through the router from the internet you will need to foward ports in the router to allow that ( be carefull though as each port you open is another attack vector for inet jerks )


Good Luck

---

### Post by intermentals on 2010-01-17
thank you very much for your time answering this
[COLOR=black]
MarkC502:[/COLOR] 

"THESE ARE SETTING THAT NEED TO BE TRUE ON BOTH PC & ROUTER LAN SETTINGS

In your router you will have LAN & WAN settings LAN is your local network of PC's with IP's like 192.168.0.XX WAN is the internet connection and will have an internet IP never 192.168 anything. Its the router LAN section that needs to match the same rules as the PC you intend to run as a server."

where would I change the settings on server, client and router please? (if there are any client settings that are manually dictated)

also if the dns is coming from the ISP do I put the router IP in twice or once and have the second as one of the free dnses you mentioned?

---

