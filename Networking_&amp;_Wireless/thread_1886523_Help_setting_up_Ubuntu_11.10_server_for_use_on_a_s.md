---
title: "Help setting up Ubuntu 11.10 server for use on a small office network"
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by dckirba on 2011-11-25
Hello everyone,

How are you doing?

I am not new to Ubuntu, but I am relatively new to setting up Ubuntu Servers. The only one I've done till date is a simple CUPS server for cross-platform use a couple of years ago.

So please bear with me if my questions seem a bit illiterate :)

This is what I am trying to do:

We have a small office, 7 computers - a mix of Ubuntu laptops, Windows 7 laptops, 1 Vista laptop, 1 XP desktop and 1 Mac Mini running OSX 10.6.

I am trying to set up a computer for use as a server to do the following:
[LIST=1]
[*]To share our internet connection (currently 3G USB dongle, but changing to broadband cable in a month)
[*]Provide IP addresses to all computers on the network using DHCP
[*]Host some web based applications for job tracking, company WIKI, and chat
[*]Share files
[*]Optionally be a DNS caching server (and also have a name other than 192.168.x.x)
[*]The computer has a large second drive and I want to use this for networked backups of selected folders on each computer on the network
[/LIST]

There is no router on our network and all the computers are going to be connected via a 8-port D-Link switch.

I went through the Ubuntu Server guide and came up with this plan of action:[LIST=1]
[*]Set up DHCP first
[*]Configure DNS next
[*]Set up the computer as a gateway
[*]Set up LAMP server
[*]Set up Samba File shares
[*]All the other small stuff
[/LIST]

So far I'm still on step number 1. 


**Setting up DHCP**

The WIKI page I found says to install DHCP3. However, Ubuntu 11.10 comes with ISC-DHCP-SERVER and it says that this supercedes DHCP3.

So I configured /etc/default/isc-dhcp-server to listen on eth0 and I configured /etc/dhcp/dhcpd.conf by uncommenting the 'authoritative' directive in the sample file and adding the following for my network:

```
subnet 192.168.27.0 netmask 255.255.255.0  {
  range 192.168.27.50 192.168.27.200;
  option routers 192.168.27.1;
  option domain-name-servers 192.168.27.1, 8.8.4.4, 8.8.8.8;
```

I've given the server a static IP of 192.168.27.1
I've also set up DNS caching so it forwards to the Google name servers, but that's for when the internet is actually being shared and I haven't gotten there yet.

I restarted the dhcp daemon and I plugged my ubuntu laptop into the switch to see if it received its configuration via DHCP. The network manager icon spins for a while, but no connection happens.

I also tried giving the Ubuntu Laptop a static IP and then pinging the server on 192.168.27.1 but it didn't ping.

So basically, I'm stuck at step 1 of my plan of action and I have had no luck troubleshooting :(

Any advice would be welcome.

Thanks in advance :)

Have a great day,
David K

Update: After a lot of fiddling around and checking things it all boiled down to a faulty cable :( DHCP working fine now :)Moving on to DNS configuration :)

---

