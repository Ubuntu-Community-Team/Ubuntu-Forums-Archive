---
title: "Static IP problem"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by ryrobbo on 2009-10-04
This has been a real pain in the backside, all day i have been trying to configure a static IP. I have done it many times in Ubuntu but it won't work now.

Here are my Belkin router settings.

Gateway: 192.168.2.1
Primary DNS: 194.168.4.100
Sec DNS: 194.168.8.100

I have opened up FTP, HTTP ports etc to work only with a PC connected with the 192.168.2.50 IP.

In Ubuntu i right clicked the network icon and selected "Edit Connections" and changed it to Manual with the following settings:

IP: 192.168.2.50
SubMask: 255.255.255.0
Gateway: 192.168.2.1
DNS: 194.168.4.100

I saved the settings and rebooted. I can still connect to the network fine and can access my Router in the FireFox browser but I have absolutely no internet access. Im sure i have done everything right. If i get an IP from the DHCP i can access the internet but not with a static.

Ive tested this method on another PC (still doesn't work) so its not the network card. And ive tried it on Fedora 10 and it says "its not configured".

Please can anyone help me?

Thanks.

---

### Post by ermeyers on 2009-10-04
If you want a static ip, the edit /etc/network/interfaces to get the Network Manager out of the configuration.

```

auto eth0
   iface eth0 inet static
   address 192.168.2.50
   netmask 255.255.255.0
   network 192.168.2.0
   broadcast 192.168.2.255

```

When you get an IP from DHCP, it modifies your /etc/resolv.conf which has "nameserver 194.168.4.100"

---

### Post by ryrobbo on 2009-10-04
Thanks for the reply.

I did what you said but still my new connection won't provide me an internet connection.

---

### Post by jward3010 on 2009-10-04
After you set up the above manual settings, click on the network icon again and you'll see a connection name to choose, pick it and see what happens. If thats doing nothing open a terminal and type:
```
sudo /etc/init.d/network restart
```

---

### Post by tripolitan on 2009-10-04
"If i get an IP from the DHCP i can access the internet but not with a static."

In your case, change your DNS in Network Mangler so it is the same as your gateway=192.168.2.1

I would do away with Network Mangler alltogether and edit /etc/network/interfaces instead and, as mentioned, sudo /etc/init.d/networking restart and ifup eth0 or wlan0

---

### Post by jward3010 on 2009-10-04
I apologise I didn't read well enough. Those DNS servers you've set could be dodgy or useless or down at the mo. Firstly try:
```
ping -c 3 208.67.222.222
```
Do you get replies? At the very least you should be able to ping that IP, if not it could be the way your firewall is setup

---

### Post by ermeyers on 2009-10-04
Internet probably works with DHCP, because when you get an address from the server it is also giving you DNS info for /etc/resolv.conf .

---

