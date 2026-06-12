---
title: "interfaces config issue"
date: 2012-05-22
forum: Networking &amp; Wireless
---

### Post by bxdobs on 2012-05-22
Can someone please help me resolve a configuration issue with the */etc/network/interfaces* file for both an internet connection and a static address.

UBUNTU 10.04 installed in VMPlayer 3.1 on XP Pro

The */etc/network/interfaces* file defaults to:

*auto eth0* 

While this works great by itself, for whatever reasons UBUNTU keeps changing the IP address ... this is an issue for me because I have both SAMBA and TELNET resources that I want to connect to this OS and these addresses not only change at boot time but they appear to change at random causing loss of telnet and samba connections 

I installed the supporting files for iface and then added the following lines to */etc/network/interfaces*:

[I]iface etho inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1[/I]

While this change provided a static address, something strange is happening:

When I run: *ping google.com*, the google.com IP address is being resolved by a DNS server ... yet ... there are no replies to the ping

I suspect the issue is with this Gateway setting but not sure how to resolve this ... tried the native Windows Gateway for the XP machine but that doesn't work either ... I even tried adding the gateway to the */etc/hosts* file

---

### Post by steeldriver on 2012-05-23
so how did you determine the gateway address?

imho situations like this are MUCH better dealt with using address reservation on the router - that means everything is defined in one place and you don't run the risk of address conflicts / gateway mismatches etc.

if your router supports it I would strongly recommend going that route

---

### Post by chili555 on 2012-05-23
I'm not sure I completely agree with my esteemed colleague. Manual configuration can be done easily. I have three such computers set manually here, including this one. I'd more interested in:```
cat /etc/resolv.conf
route -n
```Is Network Manager running on this machine?

---

### Post by steeldriver on 2012-05-23
chili I have only been here a short while - you are clearly the deity of all things ifconfig and your troubleshooting threads here are the best

as a bear of little brain I like to keep things as automatic as possible on the client side - perhaps it's my age (I tend to forget what configs I've changed on different boxes...)

whatever works for the OP is the best solution, I'm not a zealot about these things

---

### Post by bxdobs on 2012-05-23
I did some backtracking yesterday:

Went back to just *auto eth0* then used *route -n* to determine what this set up for its defaults ... turns out the gateway was *192.168.0.2* ... poking around further I found this was actually set up in */etc/resolv.conf* as the *nameserver* ... once I changed my gateway setting I was good to go. 

Understand this is a Virtual machine so not sure how a router configuration would work for this. 

I am still not clear how the VMNet1 and VMNet8 actually connect to the Windows WLAN adapter. All of my Samba and Telnet connections work from the HOST Window machine to this VM which resides on this HOST however I have been unable to make a connection from remote Window machines on the same local network.

---

### Post by steeldriver on 2012-05-23
> **bxdobs said:**
> 
Understand this is a Virtual machine so not sure how a router configuration would work for this. 


oops I missed that bit - yes it would make it difficult I think  - not sure if even possible (spoofing different MAC addresses for each VM?) - probably far more trouble than the static configs that you are using

<backs out of thread slowly>

---

