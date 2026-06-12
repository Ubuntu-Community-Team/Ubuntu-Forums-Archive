---
title: "[SOLVED] is there a prob using a static ip with router dhcp?"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by walter_j on 2008-12-10
I want to ssh to a ubuntu server and so apparently must use a static ip on this computer. Must i also change the router and all other pc's to static ip's, or can i let the router assign ip's to other (xp) pcs?

thanks

---

### Post by dragos_iliescu_2005 on 2008-12-10
Normally you need static address. But is possible that your provider not allow static address. You must check this first. 
In case when this is the case, then there is a solution called free DNS hosting. A rapid google on the subject I expect you will find a free DNS. My self I use DynDNS.

---

### Post by walter_j on 2008-12-11
> **dragos_iliescu_2005 said:**
> Normally you need static address. But is possible that your provider not allow static address. You must check this first. 
In case when this is the case, then there is a solution called free DNS hosting. A rapid google on the subject I expect you will find a free DNS. My self I use DynDNS.

I must use a static ip for the router (radio connection), but the xp boxes were getting dynamic ip from router. can i use a static ip in the ubuntu server and allow the router to continue assigning ips to the xp boxes?

I tried setting a static ip in /etc/network/interfaces, but i'm having issues and am not sure if the static ip is the problem, or some other issue with the samba config. I had to update the router firmware and now can nolonger see the ubuntu server on the net. the xp boxes are not having any problems seeing each other. the only change was the firmware update and static ip.

the server is ubuntu 8.04 server. router is linksys wrt54gs (I don't reccommend this router! slow internet sharing)


Walter
Walter

---

### Post by dragos_iliescu_2005 on 2008-12-11
You must to access the router configuration interface, navigate to the dhcp server and add in "address reservation" (name can be different) the MAC address of the machine you need to have static IP and the IP you want. After reboot the router, machine described by MAC address will have all the time same address.

Method describe is ok for inside LAN. If you want to access the Ubuntu Server from outside world, then go search for DNS hosting

---

### Post by superprash2003 on 2008-12-11
you could leave DHCP ON in the router.. and allow other pcs to get ip via DHCP.. and manually set static ip for ubntu

---

### Post by rickyjones on 2008-12-11
> **walter_j said:**
> I want to ssh to a ubuntu server and so apparently must use a static ip on this computer. Must i also change the router and all other pc's to static ip's, or can i let the router assign ip's to other (xp) pcs?

thanks

No - you can leave DHCP configured and allow the other computers to operate as such.

Generally your router will have a predefined DHCP range. For example, my router has it from 10.0.0.2 - 10.0.0.50. Therefore in my case I would assign static IPs from a range higher than 10.0.0.50.

If you can determine the range then you can assign an IP that is out of the range. No need to configure DHCP reservations or exceptions.

Thanks,
Richard

---

### Post by walter_j on 2008-12-19
I didn't change the router settings but i had to change the static ip address to match the ip format to the router's ie 192.168.1.101 not 192.168.0.101. I also discovered the network ip is the router ip. thanks everyone.

Walter

---

