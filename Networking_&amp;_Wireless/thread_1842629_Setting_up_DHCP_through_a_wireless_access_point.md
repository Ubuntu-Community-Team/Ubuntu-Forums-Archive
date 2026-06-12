---
title: "Setting up DHCP through a wireless access point"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by grizdog on 2011-09-11
Hi,

I found my way to the perfect thread for my problem, posted a query, and then discovered it was in a dormant forum - or at least appeared to be.  I know posting the same message to two different fora is a no-no, I am only doing it because I honestly believe the other forum gets very little traffic, if any.

The wiki I refer to is [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing).  Here is the post:

I've looked at the wiki and read the thread, but it didn't seem to help - I think I am almost there, but not quite.

I have my Ubuntu (lynx) connected to the internet through eth1.  I have  eth0 connected to a Linksys WAP53G.  This is nothing more than a  wireless access point - it is not a router at all.  The idea is to have a  wireless network in my house that makes use of the firewall and other  security features of my desktop computer.

I followed the dirctions in the wiki, and most things seems to work.   The default address of the WAP is 192.168.1.245, so I let it stay at  that, and the default gateway that the WAP uses is 192.168.1.1, so I  used that as the address of eth0 (ifconfig eth0 192.168.1.1).  I can  ping those two addresses from my desktop machine, and a ping for any  other address in 192.168.1 gets lost, so that appears to be working.  I  have dhcp3 set up and running on my computer, is the config file:

     Code:
     INTERFACES = "eth0";
# option definitions common to all supported networks...

default-lease-time 6000;
max-lease-time 72000;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
#log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.1;
option domain-name-servers 192.168.1.1, 192.168.1.2;
option domain-name "alexfeldman.org";

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.1 192.168.1.250;
} 
Should I have not left my domain in there?  Oh well.

No errors, or at least obvious errors, appear in the logfiles.  It just  seems like the dhcp signal isn't getting out there, and that's why my  laptop isn't finding a signal.

Any ideas?

Thanks.

---

### Post by Dangertux on 2011-09-12
To be honest your dhcpd.conf looks a little wonky not sure if it's causing the problem but... You might try this.

```

INTERFACES = "eth0";
# option definitions common to all supported networks...

default-lease-time 6000;
max-lease-time 72000;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
#log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

subnet 192.168.1.0 netmask 255.255.255.0 {
      range 192.168.1.1 192.168.1.250;
      option broadcast-address 192.168.1.255;
      option routers 192.168.1.1;
      option domain-name-servers 192.168.1.1, 192.168.1.2;
      option domain-name "alexfeldman.org";

}


```Verify that dhcpd3 starts with no errors


That may fix your issue. Assuming your iptables configuration is correct.

P.S. I really enjoyed your paper about encryption.

---

### Post by grizdog on 2011-09-12
Thanks for the help, and for the kind words.

Your dhcpd.conf code looks better, but didn't seem to have an effect.  There was as before nothing in the messages log and just one line in syslog, saying dhcpd successfully wrote 1 lease.  But the laptop still couldn't find a network.

Here are the relevant lines from the iptables config file:

```
  
iptables -A FORWARD -o eth1 -i eth0 -s 192.168.1.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE 


```and they are the last rules iptables gets, so nothing else could be interfering with them.

Thanks.

---

### Post by Dangertux on 2011-09-12
Just to rule this out, the WAP is functional correct?

Also, is there an option to set the WAP to receive an ip via dhcp as opposed to it being static?

EDIT : Something else I thought of, the tutorial you are mentioning says to uncomment the following line in /etc/sysctl.conf

```

net.ipv4.ip_forward=1

```

However by default if you are running ufw (honestly I wouldn't in this case I would manage everything with iptables to avoid conflicts. you Also need to uncomment it in /etc/ufw/sysctl.conf

---

### Post by grizdog on 2011-09-13
I'm afraid the WAP is a bit of a black box to me.  It is possible to assign it an address by DHCP rather than statically, I found a PDF document on the web ages ago that recommends that you not do that, although I expect you may have been asking that as a way of testing?

For what it is worth, when I boot my computer, the "link" light on the WAP is off, but then when I enter
"ifconfig eth0 192.168.1.1" the link light goes on.  So something is going on.  I can also ping 192.168.1.1 and 192.168.1.245, but no other address on that subnet.  

I had not uncommented that line in /etc/ufw/sysctl.conf - but now that I have, it made no difference.  Actually the line I uncommented was 
```
net/ipv4/ip_forward=1
```not
```

net.ipv4.ipforward=1

```as it was in the other file, but all the lines in that file looked like that.  I don't know how that file works, or really how ufw works.  I never turned it on, or off, I just went straight to iptables.  A quick ps doesn't show anything called ufw running.

Thanks for all the help

---

### Post by Dangertux on 2011-09-13
> **grizdog said:**
> I'm afraid the WAP is a bit of a black box to me.  It is possible to assign it an address by DHCP rather than statically, I found a PDF document on the web ages ago that recommends that you not do that, although I expect you may have been asking that as a way of testing?

For what it is worth, when I boot my computer, the "link" light on the WAP is off, but then when I enter
"ifconfig eth0 192.168.1.1" the link light goes on.  So something is going on.  I can also ping 192.168.1.1 and 192.168.1.245, but no other address on that subnet.  

I had not uncommented that line in /etc/ufw/sysctl.conf - but now that I have, it made no difference.  Actually the line I uncommented was 
```
net/ipv4/ip_forward=1
```not
```

net.ipv4.ipforward=1

```as it was in the other file, but all the lines in that file looked like that.  I don't know how that file works, or really how ufw works.  I never turned it on, or off, I just went straight to iptables.  A quick ps doesn't show anything called ufw running.

Thanks for all the help

UFW doesn't do anything particularly special, it is actually a configuration tool for iptables. However, sometimes if it is enabled it will pass kernel options out of it's own settings and become a royal pain in the behind :-P

If you have a hub or switch can you try connecting it to the interface that should be your "internal" interface and hooking up the laptop to the switch in a wired manner. Just to make sure it is in fact obtaining a lease from the DHCP server. That way we can rule out dhcp configuration issues. 

I'm still working on getting the equipment to test out the wiki page's tutorial. (I don't have access to a WAP that isn't a router). So I might have to fake it a little by using a laptop with wired interface and wireless interface. But I really think it shouldn't be that difficult to figure out.

Things to double check if you're stumped.

-- Verify your iptables rules
-- Verify that ufw is disabled 
```

sudo ufw status

``` 

if it isn't 

```

sudo ufw disable

```

-- Verify that the WAP is working if possible (we know it at least powers on and the link light turns on)

-- Is the interface the WAP is connecting to auto-correcting? And if it's not are you using the right type of network cable (it should be crossover or connected to an uplink port on the WAP)

Just some thoughts off the top of my head

---

### Post by grizdog on 2011-09-13
Boy that response from gillgill was kind of strange.  Did I attract a bot?

ufw was inactive

I plugged the ethernet cable that was plugged into the WAP into my laptop, and it worked.  Well, mostly - no nameservice, but I typed the  IP address of google into firefox and got Google's web page.  So that would seem to indicate that both the port forwarding in iptables is working, as is DHCP.

I must admit I don't quite understand the iptables rules.  I know what the switches mean, like -o and -i but I don't know why some of the others are necessary.  I used to have different ones, similar, but different.  One difference that appears major to me is my old rules specifically mentioned the ip address of the server, now it's not in there.  But since I did make a connection to my laptop, I figure that is not the problem.

There is very little to configure on the WAP itself.  I'm just using the factory defaults, which seems like it ought to be enough for this application.

Thanks.

---

### Post by grizdog on 2011-09-14
It works!  I told my laptop to look for a hidden network, and it found it.  I have no idea what was going on, but I'll take it.

Thanks to all.

---

