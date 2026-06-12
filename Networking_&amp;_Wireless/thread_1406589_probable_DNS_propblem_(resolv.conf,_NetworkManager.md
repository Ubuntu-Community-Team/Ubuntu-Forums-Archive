---
title: "probable DNS propblem (resolv.conf, NetworkManager)"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by whoisin on 2010-02-14
Hi there,

I am new ubuntu user. I have tried to configure wireless usb adapter on my 9.10 desktop. Adapter did worked fine, but I have problems with wired connection now:

I can ping my router. Skype works fine (don`t need DNS), internet on virtual machine (winXP) works too.

THis is CAT of interfaces:
cat /etc/network/interfaces                                  
# This file describes the network interfaces available on your system          
# and how to activate them. For more information, see interfaces(5).           

# The loopback network interface
auto lo                         
iface lo inet loopback          

# The primary network interface
auto eth0                      
iface eth0 inet static         
        address 192.168.1.2   
        netmask 255.255.255.0  
        network 192.168.1.0   
        broadcast 192.168.1.255
        gateway 192.168.1.1    
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1                                           
        dns-search localdmn


resolf.conf is managed by something named NetworkManager. So I can`t specify DNS there.

Can someone help me to configure my Ubuntu to have an access to internet?

---

### Post by alexfish on 2010-02-14
hi

for the resolv.conf have a look here. 

[http://ubuntuforums.org/showpost.php?p=8664426&postcount=6](http://ubuntuforums.org/showpost.php?p=8664426&postcount=6)

regards

alexfish

---

### Post by Iowan on 2010-02-14
You *should* also be able to set up a static address via Network Manager and let it include the nameservers you specify.

---

