---
title: "VMware - dapper vs breezy networking"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by fedinho on 2006-06-12
I have a VMware guest running Breezy (server install). Cloning this works perfectly.

I also have a VMware guest running Dapper (server install). When cloning this (full clone), starting it with WMware Player, the eth0 is not found!

Anyone experienced similar problems? Or any Ideas? :confused:

---

### Post by fedinho on 2006-06-13
I've even downloaded the Ubuntu 6.06 Virtual Appliance via VMware homepage.
([http://www.thoughtpolice.co.uk/vmware/](http://www.thoughtpolice.co.uk/vmware/))

I've tested this release on mulitiple hosts (Windows XPs) running VMware Player, but eth0 fails for Dapper Server. 

I posted a thread at VMware as well.
[http://www.vmware.com/community/thread.jspa?threadID=44925&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=44925&tstart=0)

---

### Post by burnt-sigil on 2006-09-22
[http://www.thoughtpolice.co.uk/vmware/howto/ubuntu-server-6.06-networking.html](http://www.thoughtpolice.co.uk/vmware/howto/ubuntu-server-6.06-networking.html)

---

### Post by toobuntu on 2006-10-19
removed redundant message

---

### Post by www.rzr.online.fr on 2008-02-08
hi
same question on debian host
since there is no /etc/iftab on etch, are there alternatives files ?

regards
--
[http://rzr.online.fr/q/vm](http://rzr.online.fr/q/vm)

---

### Post by dmizer on 2008-02-08
i got around this by using eth1 instead of eth0.

despite the fact that everything reports my card as being eth0:
```
$ dmesg | grep eth
[   14.894206] eth0: registered as PCnet/PCI II 79C970A
```
i could only get the card to become active as eth1:
```
$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0C:29:3B:D8:22  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
```
i remember frequently having this problem in dapper full install as well as in a vmware environment.  don't know if this will help you with debian or not, but it's worth a shot.

---

