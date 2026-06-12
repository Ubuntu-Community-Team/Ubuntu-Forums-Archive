---
title: "Ubuntu Desktop Static IP Issues"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by Dejai on 2008-12-26
Hello I am trying to set up a static internal IP for my Ubuntu 8.04 desktop edition(That is to change it from DHCP to a static IP on my network).
 I edited /etc/network/interfaces and added:

```

auto eth0
iface eth0 inet static 
       address 192.168.0.100
       netmask 255.255.255.0
       network 192.168.0.0
       broadcast 192.168.0.255
       gateway 192.168.0.1

```

I then restarted the network. 
```
/etc/init.d/networking restart
```

However when I went to access the internet I couldn't... Now I know I am now meant to edit the DNS server settings but I am confused as to what that actually is and what I have to actually do. It wasn't fully explained to me as how to find the name server with ifconfig -a. 

So to my knowledge I have done the same as manual configuration to network settings on the wired connection as you could do through the network manager but I am not sure what to do now to get my static IP working for outside my lan...

If I change back to DHCP access to the internet works again.  

Two resources I used and I tried both ways were:

[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-desktop-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-desktop-from-dhcp-to-a-static-ip-address/)

and 

[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

If you need any more information just ask. Thanks.:guitar:

---

### Post by namdung on 2008-12-26
Are u able to ping ur gateway and any private ip eg. *74.125.45.100*?

To edit DNS entries

```
sudo gedit /etc/resolv.conf
```

Code:
```
nameserver 192.168.0.1
```

Replace with ur n/w details.

---

### Post by Dejai on 2008-12-26
Yes well thats the thing, the resolv.conf has some stuff in it relating to the network which was determined by the DHCP but when I switch to static ip it just doesn't seem to work. What do I have to replace the DHCP with?

---

### Post by namdung on 2008-12-26
> **Dejai said:**
> Yes well thats the thing, the resolv.conf has some stuff in it relating to the network which was determined by the DHCP but when I switch to static ip it just doesn't seem to work. What do I have to replace the DHCP with?

If you're able to ping a Public IP (74.125.45.100) but not a domain (google.com), that usually means that the DNS server u've specified is not resolving.

Back to basics again. set ur static IP
```
sudo gedit /etc/network/interfaces
```

The code should look like (replace with ur n/w details):
```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.10.52
netmask 255.255.255.0
gateway 192.168.10.1

auto eth0

```

Your DNS entry
```
sudo gedit /etc/resolv.conf
```

Entry should be something like:
```
nameserver 192.168.10.1
```

Now restart the n/w services
```
sudo /etc/init.d/networking restart
```

Chk ur n/w details
```
ifconfig
```

---

