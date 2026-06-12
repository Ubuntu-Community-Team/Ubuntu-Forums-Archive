---
title: "How to set DHCP with static DNS"
date: 2011-08-02
forum: Networking &amp; Wireless
---

### Post by feihu on 2011-08-02
Recently, I have encountered a problem when setting my network configuration.
I want to automatically get an IP address through DHCP at system startup, and this can be done by editing /etc/network/interfaces file, adding
auto eth0
iface eth0 inet dhcp
The problem is that I want to set a static DNS, but DHCP will automatically overwritten /etc/resolv.conf file.
What should I do?

---

### Post by CyberPingU on 2011-08-02
If your dhcp server doesn't pass it, then write the dns into /etc/resolv.conf and then
```

# chattr +i /etc/resolv.conf

```

You won't be able to modify that file untill you will remove the "+i" attribute.

---

### Post by feihu on 2011-08-02
> **CyberPingU said:**
> If your dhcp server doesn't pass it, then write the dns into /etc/resolv.conf and then
```

# chattr +i /etc/resolv.conf

```

You won't be able to modify that file untill you will remove the "+i" attribute.

The problem is that I can get DNS from DHCP, but I don't want that, what I need is static DNS...

---

### Post by NetDoc on 2011-08-02
> **feihu said:**
> The problem is that I can get DNS from DHCP, but I don't want that, what I need is static DNS...Simpy edit your /etc/network/interfaces file. I used **sudo nano /etc/network/interfaces** to get this done. 

This is how mine looks: 
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0 
iface eth0 inet static
        address 209.208.24.242
        netmask 255.255.255.240
        network 209.208.24.240
        broadcast 209.208.24.255
        gateway 209.208.24.241
```

Of course, your IP will be far different (this is a public server), and you can get your info by executing ifconfig from a command line. Be sure to restart networking (**/etc/init.d/networking restart**) for the changes to take effect. Here is how it would look for a private IP range:

```
auto eth0 
iface eth0 inet static
        address 192.168.1.XXX
        netmask 255.255.255.0
        network 192.168.1.1
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

Just replace the XXX with the IP of your choice.

---

### Post by CyberPingU on 2011-08-02
If you do like this, he will set a static IP, that is what he doesn't want to have, since he wants to use dhcp.

Anyhow I don't get what you mean by saying you want a static dns.
Do you want to use an external DNS server that is not the one provided by the dhcp server?
Or do you want to update your internal DNS so every time you get an IP from the dhcp server the DNS is updated automatically so

test.domain.eu

will always point to your PC, whatever your IP is?

---

### Post by NetDoc on 2011-08-02
> **CyberPingU said:**
> If you do like this, he will set a static IP, that is what he doesn't want to have, since he wants to use dhcp.  I see what you mean... you can't have your DHCP and eat it too! :D Or can you? 

You can actually bind multiple IPs to the same device:

```
auto eth0 eth0:1
iface eth0 inet dhcp
iface eth0:1 inet static
        address 192.168.1.XXX
        netmask 255.255.255.0
        network 192.168.1.1
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

Again, don't forget to change the XXX to a numeric value from 2 to 254. Also, make sure that 192.168.1 is within your range.

---

### Post by CyberPingU on 2011-08-02
Yes it's true, but this doesn't appear to have anything to do with a DNS...

---

### Post by feihu on 2011-08-02
> **CyberPingU said:**
> If you do like this, he will set a static IP, that is what he doesn't want to have, since he wants to use dhcp.

Anyhow I don't get what you mean by saying you want a static dns.
Do you want to use an external DNS server that is not the one provided by the dhcp server?
Or do you want to update your internal DNS so every time you get an IP from the dhcp server the DNS is updated automatically so

test.domain.eu

will always point to your PC, whatever your IP is?


For example, I can get a DNS from DHCP such as 192.168.0.1,
but what I want is set DNS to 127.0.0.1.
since DHCP will automatically overwrite /etc/resolv.conf,
this cannot be done by simply edit /etc/resolv.conf.

---

### Post by CyberPingU on 2011-08-02
> **feihu said:**
> For example, I can get a DNS from DHCP such as 192.168.0.1,
but what I want is set DNS to 127.0.0.1.
since DHCP will automatically overwrite /etc/resolv.conf,
this cannot be done by simply edit /etc/resolv.conf.

You have 2 choices:
- passing 127.0.0.1 as parameter of dhcpd if it's a linuxbox that provides it by adding the line

```
	option domain-name-servers		127.0.0.1;
```
in your dhcpd.conf;
- by editing by hand /etc/resolv.conf and using the chattr +i like I said before. If you do like this, on next reboot, your /etc/resolv.conf will NOT be overwritten since you used the "immutable" attribute. Not even root can modify it untill you remove that.

---

### Post by chili555 on 2011-08-02
It is so easy to do with a static IP. Why not?

---

### Post by feihu on 2011-08-02
> **CyberPingU said:**
> You have 2 choices:
- passing 127.0.0.1 as parameter of dhcpd if it's a linuxbox that provides it by adding the line

```
	option domain-name-servers		127.0.0.1;
```
in your dhcpd.conf;
- by editing by hand /etc/resolv.conf and using the chattr +i like I said before. If you do like this, on next reboot, your /etc/resolv.conf will NOT be overwritten since you used the "immutable" attribute. Not even root can modify it untill you remove that.

Problem solved
Thanks a lot.
I'm not using dhcpd since the default DHCP server is not set up by me; or maybe I don't fully understand the first way;
the second way is sufficient to solve the problem.

ps.
Sorry for not understanding your previous reply since I've never heard of such a attribute as immutable

---

### Post by CyberPingU on 2011-08-02
Yup, it's almost forgotten... I used it just a couple of times in 12 years!
That's why I repeated it ;)

---

### Post by NetDoc on 2011-08-02
> **CyberPingU said:**
> You have 2 choices:
- passing 127.0.0.1 as parameter of dhcpd if it's a linuxbox that provides it by adding the line

```
	option domain-name-servers		127.0.0.1;
```
in your dhcpd.conf;
- by editing by hand /etc/resolv.conf and using the chattr +i like I said before. If you do like this, on next reboot, your /etc/resolv.conf will NOT be overwritten since you used the "immutable" attribute. Not even root can modify it untill you remove that.Good info. Thanks.

---

### Post by feihu on 2011-08-02
> **CyberPingU said:**
> You have 2 choices:
- passing 127.0.0.1 as parameter of dhcpd if it's a linuxbox that provides it by adding the line

```
	option domain-name-servers		127.0.0.1;
```
in your dhcpd.conf;
- by editing by hand /etc/resolv.conf and using the chattr +i like I said before. If you do like this, on next reboot, your /etc/resolv.conf will NOT be overwritten since you used the "immutable" attribute. Not even root can modify it untill you remove that.

the second way if I exec /etc/init.d/networking restart
It will return an error as
"cp: cannot create regular file 'resolv.conf': permission denied"
I don't know if this will cause some other trouble.

---

### Post by feihu on 2011-08-02
> **chili555 said:**
> It is so easy to do with a static IP. Why not?

'cause I'm not the network manager in our LAN :)

---

### Post by chili555 on 2011-08-02
> **feihu said:**
> 'cause I'm not the network manager in our LAN :)Unless there is a policy prohibition against static IPs, I'm not sure that's a barrier. Post #2 gets the job done easily; amend /etc/resolv.conf to the nameservers you want and make it -i.

---

### Post by CyberPingU on 2011-08-02
> the second way if I exec /etc/init.d/networking restart
It will return an error as
"cp: cannot create regular file 'resolv.conf': permission denied"
I don't know if this will cause some other trouble.

Actually doesn't put you in any trouble... it just reports that it cannot create the file since it doesn't have permissions to do it. Other things flow flawlessly :)

---

### Post by feihu on 2011-08-02
> **chili555 said:**
> Unless there is a policy prohibition against static IPs, I'm not sure that's a barrier. Post #2 gets the job done easily; amend /etc/resolv.conf to the nameservers you want and make it -i.

All usable IPs are in the dynamic region, if the computer is shutdown and start up again, the IP might be occupied, so .

---

