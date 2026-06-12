---
title: "Changing virtual machine ip"
date: 2013-01-09
forum: Networking &amp; Wireless
---

### Post by Raafat1991 on 2013-01-09
Hi guys.....

i have virtual machine has 192.168.122.94  ip (ubntu server) how can i change its ip to 192.162.1.x  because i can't connect to it with that ip
thanks....

---

### Post by ivicks on 2013-01-09
Are you using virtualbox? If so you can change to Networking type to Bridged this will allow the VM to get a DHCP address from your router then  you can change it over to static if you want.

---

### Post by Raafat1991 on 2013-01-10
> **ivicks said:**
> Are you using virtualbox? If so you can change to Networking type to Bridged this will allow the VM to get a DHCP address from your router then  you can change it over to static if you want.

Yes i'm using VM , please more explanation about what you said  to me .

---

### Post by ivicks on 2013-01-12
If your VM is already running go ahead and power it off. Once you at the main VirtuaBox user interface click on the 'Network' section. You will choose 'Bridged Adaptor' this will make your VM appear to be a standalone computer to the network (ie it's own IP address) once you power it back on.
 [IMG]http://vicks.me/guides/img/vb/vb_ui3.jpg[/IMG]

Since this is a server you will probably want to give it a static ip, so once it is back up type in 'ifconfig' and write down the information the server received from your router. Next *sudo vi /etc/network/interfaces* and change *auto eth0 iface eth0 inet dhcp* to *auto eth0 iface eth0 inet static* then add *address 192.162.1.x netmask 255.255.255.0 network 192.162.1.0 broadcast 192.162.1.255 gateway 192.162.1.x* below then exit and write to disk. After writing the changes you will want to edit the following file for DNS *sudo vi /etc/resolv.conf* where is says 'name server xxx.xxx.xxx.xxx' changed 'x' to the dns server you use, write the changes and restart networking with *sudo /etc/init.d/networking restart*. If you have any issues google 'ubuntu server static IP' which could help you out.

---

### Post by Raafat1991 on 2013-01-12
> **ivicks said:**
> If your VM is already running go ahead and power it off. Once you at the main VirtuaBox user interface click on the 'Network' section. You will choose 'Bridged Adaptor' this will make your VM appear to be a standalone computer to the network (ie it's own IP address) once you power it back on.
 [IMG]http://vicks.me/guides/img/vb/vb_ui3.jpg[/IMG]

Since this is a server you will probably want to give it a static ip, so once it is back up type in 'ifconfig' and write down the information the server received from your router. Next *sudo vi /etc/network/interfaces* and change *auto eth0 iface eth0 inet dhcp* to *auto eth0 iface eth0 inet static* then add *address 192.162.1.x netmask 255.255.255.0 network 192.162.1.0 broadcast 192.162.1.255 gateway 192.162.1.x* below then exit and write to disk. After writing the changes you will want to edit the following file for DNS *sudo vi /etc/resolv.conf* where is says 'name server xxx.xxx.xxx.xxx' changed 'x' to the dns server you use, write the changes and restart networking with *sudo /etc/init.d/networking restart*. If you have any issues google 'ubuntu server static IP' which could help you out.

Many thanks many thanks......thank you everyone

---

