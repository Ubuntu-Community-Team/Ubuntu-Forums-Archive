---
title: "ssh gives message &quot;network is unreachable&quot;"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by bananabob on 2010-07-12
I have recently installed 10.04 on an old box I have sitting around and wanted to include it in my home network. After struggling with Network Manager I went in and set up the files manually.

/etc/hosts reads:
127.0.0.1 localhost
10.0.0.01 one.network one
10.0.0.02 two.network two
10.0.0.03 three.network three
10.0.0.04 four.network four

then the IPv6 stuff

/etc/network/interfaces reads:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.0.03
netmask 255.255.255.0
gateway 10.0.0.04
dns-nameservers xxx.xx.xxx.xx xxx. (etc)


/etc/hostname reads: three

/etc/resolv.conf reads:
domain network
search network
nameserver (blah)same as in /etc/network/interfaces
nameserver (blah)same as in /etc/network/interfaces


Now I can access the internet from this machine, but when I attempt to ssh to another machine in the network I get the message "Port 22 network is unreachable"

Checking with google I found that there  should be some ssh config files. I have one ssh_config but no sshd_config. I don't know if this is relevant.

Also "network" is not the name of my network. Changed for anonymity. 

By the way I am pretty much a newbie when it comes to this stuff.

Cheers
James

---

### Post by andrewc6l on 2010-07-13
You pretty much figured it out: you've got the client, but no ssh server on your machines, I'd guess.

Try:
```

sudo aptitude install openssh-server

```

You'll need to do this on all the machines you want to ssh into. To start with, just try it on one machine and ssh user@127.0.0.1 to verify it's working.

Here's a good link: [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by gombadi on 2010-07-13
> 
I get the message "Port 22 network is unreachable"


Generally network unreachable indicates a routing issue. You would be getting "Connection refused" if the server was not installed. Could still be a problem as well of course.

> 
auto eth0
iface eth0 inet static
address 10.0.0.03
netmask 255.255.255.0
gateway 10.0.0.04


Change all your ip addresses so the last part does not have a zero in it - i.e 10.0.0.04 to 10.0.0.4 and see how that goes.

---

### Post by dmizer on 2010-07-13
I assume you are also unable to browse the internet on this machine?

You will need to uninstall network-manager before this method of connecting to the internet will work.

However, if network-manager is not working, then there may be something else at fault. The wired networking stack in Ubuntu is reliable for the most part. There could be a cable problem, a loose connection, or the network card itself may be shot. Are the lights on the network card indicating that there is a connection and/or that traffic is being passed?

---

### Post by bananabob on 2010-07-14
Thanks guys for your help. But I must admit to the problem being a typo in the /etc/network/interfaces file. I had network where I should have had netmask. Only found this after the Internet stopped working.

---

