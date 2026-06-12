---
title: "Ubuntu 11,04 DHCP options configuration"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by zym0sis on 2011-08-17
Hi!

After several error messages on my 11.04 DHCP server and after a lot of googling i need to ask the cummunity.

I have a test network with a 11.04 DHCP server (dhcpd), 1 Setup box and 1 Fedora server where the setub box needs to collect its software.

If I have a standard dhcp config I have no problems (dhcp wise) 

 **[FONT=&quot][B]Subnet 192.168.205.0 netmask 255.255.255.0 {**[/FONT][/B]
  **[FONT=&quot][B]                Range 192.168.205.10 192.168.205.20;**[/FONT][/B]
  [B][FONT=&quot][B]}

[/B][/FONT][/B]but I need to give specific data to the setupbox.
the stb sends out a DHCP request including it's vendor class id. this is used to differentiate it's requests from other units in the network.

the DHCP server needs to answer with the IP address of a specific server on it's request but I don't manage to configure the dhcp server in this way. at the start of the dhcpd server he keeps on telling me that he does not know the options declared below... anybody some ideas?

here is a example of what I would like to do in the dhcpd conf
subnet 192.168.205.0 netmask 255.255.255.0 {
        range                           192.168.205.10 192.168.205.20;
        option routers                  192.168.205.1;
        option bootcast-address         "224.2.2.2:22222";
        option STB.bootcast-address "224.2.2.2:22222";
        option STB.firmware-log     "192.168.205.4:19997";
}

---

