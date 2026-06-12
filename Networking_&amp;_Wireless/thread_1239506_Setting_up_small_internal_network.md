---
title: "Setting up small internal network"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by thegrilledcheese on 2009-08-13
I have 2 machines.  One is running 9.04 server x64 and the other 9.04 desktop.  My goal is simple I think: to be able to connect to the server from the desktop via OpenSSH as well as setting up some sort of file transfer service.  I currently have a cable internet connection that uses DHCP and in 2 days I am getting converted to business class cable w/ static ip's.  

Currently both machines can access the outside world.  I can connect via ssh to the server using only the internal IP as I can't figure out how to find the outside IP.  I'd like to be able to connect just by hostname.  When I switch to a static IP I am going to point a domain at them so they'll have a domain name to use for the hostname.

I'm a windows convert and am used to a "network neighborhood" type environment where I can see all the different machines on my network.  Is there a similar GUI program for ubuntu?

Any help on how to set this up?  I think there is a config file that I need to edit to add a specific hostname to the internal IP but I don't know which or where it is.

Thanks!

---

### Post by nomarior on 2009-08-13
To be able to address your machines with their hostname you need a way to lookup the (internal) IP address of your machines. You don't have to worry about that when you have public IP addresses (and domain names), because there will be dns servers in the internet which host your dns data. 
I can think of two solutions right now, if you need to do it yourself:
a) setup a dhcp server on your lan <- you learn a lot, and it can be painful as hell
b) configure your network settings to use host files; add hostname IP tuples to that file. <- quick and easy

For only two machines, I would go for b).

To get your public IP address you have also two options: 
1) log into your modem and read the information on your network interfaces
2) browse to a site which does tell you your IP address ( you can quickly google one)

Read some ubuntu specific tutorials on networking. There are a few files which are essential to set up your network (manually). (The files vary from OS to OS slightly so I tend to mix them up, that's why you won't get a step by step guide from me. There are plenty guides out in the net.)

And another piece of advice: learn to use CLI (command line interface). Otherwise you will never see the light ( = the real power of Unix). And if you are at it, get to know manpages, bourne shell and common linux tools (cut grep sed find xargs nawk). Your life will be so much easier.

Cheers

PS: for file transfer, have a look at scp. (ie: man scp)

PPS: on second thought, your modem/router probably does dhcp, that's why you can connect to the internet at all. Your problem will be, that ther is not a guarantee, that the same pc always get's the same IP (the router might store some tables, but after a restart, those tables are gone too). So to have a reliable system, you would need to configure a fixed IP for your machines. To reach your machines by hostname is trivial: 
1) lookup your assigned IP address ( "ifconfig -a" identify the active interface; read the IP)
2) make shure that /etc/nsswitch.conf has a line that CONTAINS "hosts: files dns" and possibly others, but make shure that files comes before dns
3) enter the IP - hostname tuples into /etc/hosts (example: 192.168.1.2 [TAB] hostA) ([TAB] means tabulator
4) test with nsluup / ping

5) adapt IP in hosts file if your dhcp server assignes you a different one

---

### Post by Iowan on 2009-08-13
Several OpenSSH links [here]("http://ubuntuforums.org/showthread.php?t=1233584").

---

### Post by thegrilledcheese on 2009-08-13
Thank you. I followed the tutorials posted by Iowan and was able to get ssh working using key authentication.  I can now log in via SSH fine.  

Next question:

In order to connect to the server, I have to do:

```
ssh username@192.168.0.20
```When I try to use:

```
ssh username@hostname
```I get:

**ssh: Could not resolve hostname <username>: Name or service not known**

I'm sure there is an easy fix and I've read a ton of tutorials but I'm unsure which config and which setting is the right one for me.

Any thoughts?

PS:  Now that I have SSH access I plan on removing the gnome-desktop from the server as I will only connect via SSH and using CLI.

---

### Post by nomarior on 2009-08-14
You need to setup a dns lookup service for your machines, either setting up bind (probably with dhcp server) or with files (recommended).

Read my pervious post, edit /etc/nsswitch.conf if necessary and add 

192.168.0.20 [tabulator] hostname
to your /etc/hosts file.

---

### Post by alphanaut on 2009-08-14
In your case I would use nautilus to transfer files via sftp://<hostname or ipadress>.

---

### Post by thegrilledcheese on 2009-08-15
So editing /etc/hosts.  It currently looks like this:

127.0.0.1    localhost
127.0.1.1    dingle

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I have a static external ip and a subdomain pointed at that ip.  How should I edit host?

IP: 173.160.12.14
subdomain: dingle.example.com

---

### Post by nomarior on 2009-08-17
/etc/hosts of dingle should look something like:

127.0.0.1    localhost
127.0.1.1    dingle
192.168.0.21 hostB

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

/etc/hosts of hostB should look like that:

127.0.0.1    localhost
 127.0.1.1 hostB
 192.168.0.20 dingle
 
 # The following lines are desirable for IPv6 capable hosts
 ::1     localhost ip6-localhost ip6-loopback
 fe00::0 ip6-localnet
 ff00::0 ip6-mcastprefix
 ff02::1 ip6-allnodes
 ff02::2 ip6-allrouters
 ff02::3 ip6-allhosts
------------------

now you can ping your hosts with "ping <hostname>", provided that you entered the correct ip's.

If you want to reach "dingle" from the internet, then you need to forward the ports you will be using on your modem/router to dingle (to dingle's IP to be precise [->192.168.0.20]).

Ssh and scp use port 22. Webtraffic needs port 80 (ssl encrypted traffic port 443).

---

