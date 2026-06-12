---
title: "DHCP Address Reservation"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by kdxrider9262 on 2006-06-08
Hello,

After a little bit of help I finally got DHCP working on my server. However I would like to be able to use address reservation for my servers and what not.I do not want to use static addresses on the local machine because somtimes I take my servers places. (i.e. LAN's). Any ideas???

---

### Post by Slim Odds on 2006-06-08
[quote=kdxrider9262]Hello,

After a little bit of help I finally got DHCP working on my server. However I would like to be able to use address reservation for my servers and what not.I do not want to use static addresses on the local machine because somtimes I take my servers places. (i.e. LAN's). Any ideas???[/quote]

I don't fully understand you question, but DHCP servers can be set up to always assign the same IP address to a specific MAC address. Just look at the docs.

---

### Post by kdxrider9262 on 2006-06-08
[QUOTE=Slim Odds]I don't fully understand you question, but DHCP servers can be set up to always assign the same IP address to a specific MAC address. Just look at the docs.[/QUOTE]

I want to use address reservation (bind a IP address to a MAC address) some people might say just assign a static address on the local machine....but i want it to obtain an address that way if i take it somwhere i dont have to reconfigure it to meet the needs of the network. If anyone knows the command that would be great...There is alot of reading to be done in the dhcpd.conf file...Im a bit lazy for that :)

---

### Post by Slim Odds on 2006-06-08
[quote=kdxrider9262]I want to use address reservation (bind a IP address to a MAC address) some people might say just assign a static address on the local machine....but i want it to obtain an address that way if i take it somwhere i dont have to reconfigure it to meet the needs of the network. If anyone knows the command that would be great...There is alot of reading to be done in the dhcpd.conf file...Im a bit lazy for that :)[/quote]
 
 
So you think someone is going to do all the work for you?
 
 
try: man dhcpd.conf

---

### Post by kdxrider9262 on 2006-06-08
No......I just wanted the command for the reservation...When i made my dhcpd.conf file i deleted all of the information contained in it.....so i cant look it up myself :)

---

### Post by Macchi on 2006-06-09
Probably you have already found a solution, but for anyone else here is a suggestion of configuration entries for a dhpc server deamon:

On /etc/dhcpd.conf: 
```
option domain-name "<your domain name>";
option domain-name-servers <IP for your DNS servers>, <IP for your DNS servers>;
option routers 192.168.0.1;
option ntp-servers europe.pool.ntp.org;
option netbios-name-servers 192.168.0.100;
default-lease-time 14400;
ddns-update-style none;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.32 192.168.0.64;
  default-lease-time 14400;
  max-lease-time 172800;
}

host <hostname> {
              hardware ethernet  <MAC address>;
              fixed-address 192.168.0.3;
}
```

---

### Post by kdxrider9262 on 2006-06-09
Thank you very much!!! :))

---

### Post by Macchi on 2006-06-09
I am glad that the information was useful for you!

In my Home&Office network I use dynamic addresses for all clients, but want them to always lease the same IP address from the server.

This is particularly useful when used together with a DNS for the internal zone so that you can simply refer to you computers, firewall and gateway by their hostnames. Some software for DNS servers is integrated with a DHCP server and then you will have a single place to manage the association of hostnames, IP, and MAC addresses.  
Servers may receive fixed addresses outside the range of the Dynamic Host Configuration Protocol. (I have used Dnsmasq, Bind, and intend to test djbdns and tinydns when I move my server from SuSE to Ubuntu)

The control of MAC-addresses can also be used as an extra security feature in order to deny DHCP-leases to anything that has not been previously registered on the server. To keep some flexibility, temporary guests may obtain access through WLAN PC-cards with previously registered Media Access Control (MAC) address.

---

### Post by kdxrider9262 on 2006-06-09
[QUOTE=Macchi]Probably you have already found a solution, but for anyone else here is a suggestion of configuration entries for a dhpc server deamon:

On /etc/dhcpd.conf: 
```
option domain-name "<your domain name>";
option domain-name-servers <IP for your DNS servers>, <IP for your DNS servers>;
option routers 192.168.0.1;
option ntp-servers europe.pool.ntp.org;
option netbios-name-servers 192.168.0.100;
default-lease-time 14400;
ddns-update-style none;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.32 192.168.0.64;
  default-lease-time 14400;
  max-lease-time 172800;
}

host <hostname> {
              hardware ethernet  <MAC address>;
              fixed-address 192.168.0.3;
}
```[/QUOTE]


Quick question a bout this one.......
host <hostname> {
              hardware ethernet  <MAC address>;
              fixed-address 192.168.0.3;

Do I include the <> with the <hostname> i would assume not but I havent gotton it to work properly yet.

---

### Post by ape on 2006-06-10
No, the angle brackets around the hostname and MAC address placeholders should not be used.

---

### Post by kdxrider9262 on 2006-06-10
Ok im sorry i have another question now.... This is how my config looks

 
subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.100 192.168.0.199;
        option subnet-mask 255.255.255.0;
        option routers 192.168.0.1;
        option domain-name-servers 192.168.0.168;
        option domain-name "XXX.XXX.XXX";
        option ip-forwarding on;
        option netbios-node-type 8;
    }

host THE-ARCHITECT {
hardware ethernet 00-50-8D-F9-7C-95;
fixed-address 192.168.0.100;}


now is this correct....DHCP has seemed to stop working after i added this.. :(

---

### Post by Slim Odds on 2006-06-10
[quote=kdxrider9262]
        option domain-name "XXX.XXX.XXX";
 [/quote] 
I don't think that is a valid IP address

---

### Post by kdxrider9262 on 2006-06-10
[QUOTE=Slim Odds]I don't think that is a valid IP address[/QUOTE]

I used XXX.XXX.XXX as a domain name because I did not want to post it to the public :)

---

### Post by Slim Odds on 2006-06-10
[quote=kdxrider9262]I used XXX.XXX.XXX as a domain name because I did not want to post it to the public :)[/quote] 
Ok, but next time you might want to try something like:
**option domain-name "my.private.domain.name";**

That might make it a little more obvious.

---

### Post by ape on 2006-06-10
so I believe that your harware address elements need to be separated by colons (:) rather than dashes as you have them.  I've looked in the man page for dhcpd.conf and don't see any examples with dashes in them.

What error messages are you getting from the dhcp daemon?

--Ape--

---

### Post by kdxrider9262 on 2006-06-10
Im sorry again a appologize for this but i am a n00b.....I do not see any errors upon startup....I also do not see anything about DHCP upon startup....Is there a way to manaully start and restart the DHCP daemon??

---

### Post by Macchi on 2006-06-10
Firstly, terminate any critical operations and save ongoing work on the clients in the network, as a precaution in case things go wrong. Also please read the disclaimer below.

You may then issue a command to restart your DHCP server:
```
sudo  /etc/init.d/dhcpd restart
```
Hopefully this will stop, reload and restart the server. Otherwise you may do it  explicitly using the following options for the /etc/init.d/dhcpd : 
{start|stop|status|try-restart|restart|force-reload|reload|probe|check-syntax} [-v]

Then monitor the /var/lib/dhcp/dhcpd.leases, for instance: 
```
less /var/lib/dhcp/db/dhcpd.leases
```
or any other preferred method.

To obtain more information on your DHCP-server try also: 
```
man dhcpd
```
The manual pages usually contain a lot of information on installed software. You will also find references to other related commands and files to look for, such as:

/etc/dhcpd.conf
/var/lib/dhcp/dhcpd.leases
/var/run/dhcpd.pid
/var/lib/dhcp/dhcpd.leases~.

**Disclaimer: These paths are valid for SuSE 10.0, the filepaths and commands for Ubuntu might be sligthly different! Unfortunately at this moment I do not have an active Ubuntu server running dhcpd to check the exact values.**

(Hope you will get it right. Otherwise just keep in touch.
Later we may try to help you to set a local DNS-server for your network)

---

### Post by kdxrider9262 on 2006-06-10
[QUOTE=Macchi]
(Hope you will get it right. Otherwise just keep in touch.
Later we may try to help you to set a local DNS-server for your network)[/QUOTE]

Thanks, I already have a local DNS running on Server 2k3 x64 :) Im just a complete n00b a linux....Ill give your suggestions a shot thank you!@!

---

