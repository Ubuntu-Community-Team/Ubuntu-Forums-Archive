---
title: "Fresh Install  and no wired connection"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by jus71n742 on 2010-11-20
10.04 Fresh install, I just installed it on my laptop and well I am using it right now to post this information.  It works wirelessly no problems.  However on my desktop I have tried a couple things to no avail.  I have tried manual IP, and restarting network services.  what other options are there to get the wired connection working again?

I noticed on a server I am installing 10.10 on that it failed autoconfig.  related issue?

here is a thread I tried and got nothing
[http://ubuntuforums.org/showpost.php?p=9733891&postcount=6](http://ubuntuforums.org/showpost.php?p=9733891&postcount=6)

---

### Post by uncaspi on 2010-11-20
Did you put in the correct values for your environment i.e gateway ,DNS , static ip address of your card etc.?

---

### Post by jus71n742 on 2010-11-20
It automatically found the correct MAC, and I used this laptop to get the correct gateway, DNS, etc.  I noticed when I rebooted to Windows it didn't have connection either so I moved it to eth1 ( I have 2 GigE ports on this board) and now Ubuntu see's autoeth1 under connections but will not connect.  Even if I set it back to automatic DHCP.

It also shows the 2 ports if I click the network icon in the task bar.  saying both are disconnected.[quote]
Wired Network (Realtek RTL8111/8168B PCI Express Gigabit Ethernet Controller)
 disconnected
[\quote]

There a way I can get these drivers and install?

---

### Post by uncaspi on 2010-11-20
Try it manually. Plug in the cable in eth1.Stop network-manager.

sudo service network-manager stop

sudo /sbin/ifconfig eth1 up

sudo dhclient eth1

sudo /sbin/route add default gw x.x.x.x eth1
where x.x.x.x is your router gateway.

ping x.x.x.x -c 4

Do you get response? If so
sudo echo "nameserver 8.8.8.8" > /etc/resolv.conf
Can you now ping google.com -c 4
If not restart networking

sudo /etc/init.d/networking restart

Try pinging again.

What do you now

---

### Post by jus71n742 on 2010-11-22
```
# dhclient  eth0
No DHCPOFFEERS received.
No working leases in database - sleeping
```

---

### Post by uncaspi on 2010-11-22
If you try dhclient eth1
do you get the same?

---

### Post by jus71n742 on 2010-11-23
yes, both failed.

---

