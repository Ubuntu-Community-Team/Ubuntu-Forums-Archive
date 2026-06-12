---
title: "Restart Network"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by mthalis on 2009-06-15
I want to stop(restart) network then i tiped
sudo /etc/init.d/networking stop 
it gave 
      Reconfiguring network intefaces....
      Ignoring unknown interface eth1=eth1.  
out put but still I can go internet. Am I wrong?

Another problem is where locate network setting? surfing net I found it located /etc/network/interfaces 
but it contained 
   auto lo
   iface lo inet loopback

then I added

---------------------------------------------------------

# The loopback network interface
auto lo
iface lo inet loopback
# 
#
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 192.168.1.1
#
------------------------------------------

After adding this I couldn't go to internet. please help me I don't have good knowledge about networking..

I used Ubuntu 9.04 desktop edition, my machine have two network card and statics IP.

---

### Post by W03L on 2009-06-15
remove network-manager*
then restart PC

---

### Post by mthalis on 2009-06-15
After removing network-manage, what is the next step?

---

### Post by superprash2003 on 2009-06-15
leave your /etc/network/interfaces as it was in the beginning.. and add the following

auto eth1
iface eth1 inet dhcp


the problem is with eth1 not eth0`

---

### Post by mthalis on 2009-06-15
"sudo /etc/init.d/networking  restart(start|stop)" this command not restart network
why?

---

### Post by Iowan on 2009-06-15
> **mthalis said:**
> "sudo /etc/init.d/networking  restart(start|stop)" this command not restart network
why?
Network Manager is another player that might complicate things. **sudo /etc/init.d/NetworkManager restart** (or force-reload) *might* work.

---

### Post by mthalis on 2009-06-15
Thank for your help it's working...

---

