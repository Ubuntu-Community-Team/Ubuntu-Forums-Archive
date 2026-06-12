---
title: "Setting up a Static IP in a LAN and DNS configuration"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by mahela007 on 2010-02-13
I want to know how to set up a static IP from Ubuntu...
Secondly, on some of the tutorials I read, there was something about changing the DNS server IP adresses. I do know what a DNS server is (Courtesy of [www.howstuffworks.com](www.howstuffworks.com) ;-) ) but I don't understand why the DNS servers must be changed simply because I chose to use a static IP address.. 
(My PC connects to the internet via a router.. )

---

### Post by x33a on 2010-02-13
You just need to put the required entries in the interfaces file. take a look here:

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

---

### Post by mahela007 on 2010-02-13
That tutorial is one which talks about changing the DNS server. Could you please explain why this need to be done?

Here's what my /etc/network/interfaces file looks like

```
auto lo
iface lo inet loopback

```

---

### Post by x33a on 2010-02-13
I don't think it is necessary. As far as i know, you can keep the dns servers configured with the router itself (when not using dhcp).

While i have never used dhcp myself, i guess you can just try and see if it works or not.

If any problem occurs, just add these entries to /etc/resolv.conf
```
#
# /etc/resolv.conf
#

#search <yourdomain.tld>
#nameserver <ip>

#opendns
#nameserver 208.67.222.222
#nameserver 208.67.220.220

#dns advantage
#nameserver 156.154.70.1
#nameserver 156.154.71.1

#google public dns
nameserver 8.8.8.8
nameserver 8.8.4.4

# End of file
```

Just uncomment the ones you prefer.

---

### Post by mahela007 on 2010-02-13
Thanks. Does that file contain all the DNS servers which can be used?
EDIT: What about my weird file? 
According you your link it should say 
```
iface eth0 inet dhcp
```

but it says 
```
iface lo inet loopbackinstead.
```

---

### Post by x33a on 2010-02-13
> **mahela007 said:**
> Thanks. Does that file contain all the DNS servers which can be used?
EDIT: What about my weird file? 
According you your link it should say 
```
iface eth0 inet dhcp
```

but it says 
```
iface lo inet loopbackinstead.
```

Let the contents of your file remain.

just append the following to the file
```
iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1
```

As for the dns servers, the /etc/resolv.conf is the system-wide dns-configuration file. And the entries above are from my personal resolv.conf, i tend to switch between these everyonce in a while.

Currently, google dns entries are uncommented, so they will work.

You can uncomment any of the entries, and they will be used in the order in which they are listed. you can also add your personal dns servers in that file and remove everything else instead.

---

### Post by Iowan on 2010-02-13
Another option:
Network Manager lets you set up a static address under the IPv4 Settings tab.

---

### Post by mahela007 on 2010-02-13
Ok.. thanks for your help guys..

---

