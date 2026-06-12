---
title: "configuring eth0 with ifconfig is not persistent,why?"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by WTF1sh on 2009-09-26
Hy all!
I'm newbie,but here's my qestion:
I've just installed Ubuntu 9.04 on my pc,it starts just fine.I login , start a terminal and set the eth0 like this:
sudo ifconfig eth0 10.1.4.19 netmask 255.255.255.0

If i enter ifconfig -a,then it looks like eth0 is properly configured,but if a reboot the system, login and check ifconfig -a it looks like the previous setings are all gone!But why? :confused:
Respond here or send mail: hbaloo28 at gmail dot com
Thank!

---

### Post by puppywhacker on 2009-09-26
you can set the settings permanently in the network manager on the right top of the desktop. Or bypass the network manager (a bit more advanced) edit the file /etc/network/interfaces

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

---

### Post by chili555 on 2009-09-26
I don't believe the ifconfig method is intended to be persistent. If you want these settings to stick, I suggest you amend */etc/network/interfaces* like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.1.4.19
netmask 255.255.255.0
gateway 10.1.4.1
```Substitute your details, if your gateway or other access point is not 10.1.4.1.

Your interface will start and connect automatically without the need to use the terminal on every boot.

---

### Post by WTF1sh on 2009-09-26
I modified the interfaces, restarted, and after ifconfig -a all settings seemed to be allright,but there were no connections available when I tried to select one from the list from top right corner of monitor.It said no managed devices.I restored the interfaces file, and after a reboot i could connect to the internet just fine but of course still no eth0 settings.
how can i fix the bo managed device problem?What does it even mean?
Thanks for fast replies btw!

---

### Post by renkinjutsu on 2009-09-26
```
eth0 10.1.4.19 netmask 255.255.255.0
```

Put that into your /etc/rc.local file
then make it an executable if it isn't already
```
sudo chmod +x /etc/rc.local
```

---

### Post by chili555 on 2009-09-26
> connections available when I tried to select one from the list from top right corner of monitor.You don't need Network Manager to manage your connections if you want a static IP to be persistent. You were connected as you wished.

---

### Post by WTF1sh on 2009-09-26
Messign with ifdown,ifup and /etc/init.d/networking restart seems to have solved the problem.Thx for replies.I can connect using NetworkManager, what other methods there are?

---

### Post by Iowan on 2009-09-26
> **WTF1sh said:**
> I can connect using NetworkManager, what other methods there are?Another method is to define the interface in */etc/network/interfaces*
 as **chili555** mentioned...

---

