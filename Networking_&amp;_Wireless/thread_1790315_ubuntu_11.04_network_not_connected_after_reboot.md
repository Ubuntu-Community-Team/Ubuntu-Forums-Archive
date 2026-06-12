---
title: "ubuntu 11.04 network not connected after reboot"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by ntlam on 2011-06-24
Hi,

After install Ubuntu 11.04, I set IP address to be static, everything worked fine for a week. Then I reboot and now the network is not connected. 

I have tried to go back to DHCP, no luck.

Edit /etc/network/interfaces to be:

auto eth0
iface eth0 inet static
        address 192.168.159.17
        netmask 255.255.255.0
        network 192.168.159.1
        broadcast 192.168.159.255
        gateway 192.168.159.245

edit /etc/resolv.conf 
  nameserver 192.168.159.1

then sudo /etc/init.d/networking restart

got the message:
  SIOCADDT: No such process
  Failed to bring up eth0

Any help please.

Lam

---

### Post by ntlam on 2011-06-24
BTW, I tried login Windows to see if the ethernet port has problems, windows work fine.

Lam

---

### Post by dFlyer on 2011-06-24
Backup you interfaces file and edit it to look like this. Reboot and see if connects:

auto lo
iface lo inet loopback

Those are the only two lines in my interfaces.

---

### Post by ntlam on 2011-06-24
I wonder why l0, but not eth0?

Now it seems I also have a reboot problem, it takes forever. Last time I had to push the power button to shut it down.

Will let you know after it's rebooted.

---

### Post by ntlam on 2011-06-24
yes, the network is up now. Thanks a lot.

Lam

---

