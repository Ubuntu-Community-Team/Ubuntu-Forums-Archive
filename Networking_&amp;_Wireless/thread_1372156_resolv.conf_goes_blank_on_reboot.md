---
title: "resolv.conf goes blank on reboot"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by Despot Despondency on 2010-01-04
Hi,

I'm having problems with my resolv.conf file. Every time I reboot my computer it goes blank and I have to re-type it before I can get on the network. How do I prevent it from being overwritten? TAI

---

### Post by suseendran.rengabashyam on 2010-01-04
Hi,
 Assuming that you are using Ubuntu-9.10 Desktop and your ip address is being obtained via dhcp the contents of /etc/resolv.conf gets overwritten every time you get an IP lease. To solve you need to go to System->Preferences->Network Connections->Auto ethX->Edit->IPv4 Settings, change the method from "Automatic (DHCP)" to "Automatic (DHCP) addresses only" and then you can enter the DNS address in "DNS servers:" column. Let me know if this solves your problem.

---

### Post by Despot Despondency on 2010-01-04
Hi, thanks for your response. I'm afraid it didn't work though. Any other ideas?

---

### Post by joachimrs on 2010-01-04
You probably want to install the resolvconf package and assign nameservers in the /etc/network/interfaces file like:

auto eth0
iface eth0 inet static
    address 192.168.0.10
    netmask 255.255.255.0
    gateway 192.168.0.1
    dns-nameservers 192.168.0.10 10.10.0.2

See [http://wiki.ubuntuusers.de/interfaces](http://wiki.ubuntuusers.de/interfaces)

Another option would be to have a startup script cp a valid resolv.conf _after_ the interface is up. But that would not solve the problem and rather be a "no so nice" workaround :)

So I'd go with the dns-nameservers line and the resolvconf package.

---

### Post by suseendran.rengabashyam on 2010-01-05
Hi,
An alternative method would be to go to


   	System->Preferences->Network Connections->Auto ethX->Edit->IPv4 Settings


   	Change the Method to "Automatic (DHCP)".


   	Now go ahead and edit your /etc/dhcp3/dhclient.conf, add your DNS servers to the "prepend" line; this will ensure that your DNS servers get entered in /etc/resolv.conf


   	look for the line
   	#prepend domain-name-servers 127.0.0.1;


   	and change it to
   	prepend domain-name-servers <PRIMARY DNS> <SECONDARY DNS>;


   	Now reboot your computer and check whether you can see your DNS Address in /etc/resolv.conf .

---

### Post by x33a on 2010-01-05
> **Despot Despondency said:**
> Hi,

I'm having problems with my resolv.conf file. Every time I reboot my computer it goes blank and I have to re-type it before I can get on the network. How do I prevent it from being overwritten? TAI

try
```
sudo chattr +i /etc/resolv.conf
```

---

### Post by Despot Despondency on 2010-01-06
Hi, thanks for all the replies. I only tried the one from x33a but it worked fine for me. Thanks again.

---

### Post by sunta on 2011-09-30
same here but with 10.04LTS server. there is no desktop where I can adjust DNS

putting it into /etc/network/interfaces gets ignored after reboot.


any hints?

---

