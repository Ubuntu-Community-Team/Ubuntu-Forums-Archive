---
title: "persistent static routes in ubuntu"
date: 2011-12-05
forum: Networking &amp; Wireless
---

### Post by freddiejason on 2011-12-05
Hey guys!
I am currently trying to add persistent static routes to ubuntu. the version I am using is 11.04. I have one problem though. I have followed every instruction that I have come across on the internet and so far I have been unsuccessful. with regard to adding a persistent route in ubuntu, you add the following command to the /etc/network/interfaces file in ubuntu:-route add -net <network address> netmask <subnet mask> gw < gateway address> dev <network interface>. You should also add the same entries to the rc.local(/etc/rc.local)file. All this works fine and the routes remain configured even after restarting the network service(/etc/init.d/networking restart). The problem arises after performing a system reboot. All the configured static routes disappear after a complete system reboot. is there something I'm missing? Can anybody assist with this, i.e how to make the routes stay configured even after a system reboot?](*,)

---

### Post by jonobr on 2011-12-05
It all sounds ok,

Can you post results of /etc/network/interfaces here to check your work?
Im figuring its ok given the static route appears to be added.

One other questions, I you running this in conjunction with the NM applet?

I figure if you disable NM applet and use manual configuration it will work ok, 

Cheers

Jonobr

PS- does my post indicate a lack of trust in Nm? If not, then I will say it here,
I dont trust the NM appplet!!!

---

### Post by freddiejason on 2011-12-06
Thanks for the speedy response jonobr. I have disabled the nm applet and the result is still the same. The routes remain nonexistent at system startup. the results of the /etc/network/interfaces file is as below:

auto lo
iface lo inet loopback

up route add -host 172.16.111.1 dev eth0
up route add -host 172.16.111.12 dev eth0
up route add -net 172.16.120.0 netmask 255.255.255.0 gw 172.16.111.1 eth0
up route add -net 172.16.121.0 netmask 255.255.255.0 gw 172.16.111.1 eth0
up route add -net 172.16.122.0 netmask 255.255.255.0 gw 172.16.111.1 eth0
up route add -net 172.16.123.0 netmask 255.255.255.0 gw 172.16.111.1 eth0
up route add -net 172.16.124.0 netmask 255.255.255.0 gw 172.16.111.1 eth0
up route add -net 172.16.125.0 netmask 255.255.255.0 gw 172.16.111.1 eht0
up route add -net 172.16.126.0 netmask 255.255.255.0 gw 172.16.111.1 eth0
up route add -net 172.16.128.0 netmask 255.255.255.0 gw 172.16.111.1 eth0
up route add -net 172.16.129.0 netmask 255.255.255.0 gw 172.16.111.1 eth0
up route add -net 132.160.160.0 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 192.1.30.215 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 172.16.111.64 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 172.16.0.0 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 172.21.1.0 netmask 255.255.255.0 gw 172.16.111.111 eth0
up route add -net 172.100.0.0 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 172.20.1.0 netmask 255.255.255.0 gw 172.16.111.1 eth0
up route add -net 192.168.1.0 netmaks 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 192.168.203.0 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 172.16.0.8 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 172.16.127.0 netmask 255.255.255.0 gw 172.16.111.1 eth0
up route add -net 172.16.15.114 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 192.168.60.0 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 192.168.70.0 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 172.29.130.0 netmask 255.255.255.0 gw 172.16.111.1 eth0
up route add -net 172.16.0.9 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 192.168.68.88 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 199.44.189.142 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 181.48.191.40 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 172.16.71.50 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 185.255.15.0 netmask 255.255.255.0 gw 172.16.111.12 eth0
up route add -net 205.165.41.0 netmask 255.255.255.0 gw 172.16.111.12 eth0
up route add -net 172.16.111.14 netmask 255.255.255.255 gw 172.16.111.1 eth0
up route add -net 172.16.111.6 netmask 255.255.255.255 gw 172.16.111.1 eth0

please let me know if there is something I have misconfigured. thanks in advance.

---

### Post by freddiejason on 2011-12-06
I found a solution. Its easier to make a script that adds those routes at system bootup than to try and add them to the rc.local file to make them get executed automatically. the procedure is as follows:
       1. create a script file in the /etc/init.d/ folder.
       2. add your route definitions to this file and change it to an executable file(chmod +x /path/to/file).
       3. run the update-rc.d <filename> defaults command to make the script executable at boot time.
       4. reboot the system and check whether the system adds the routes at startup(netstat -rn).

and thats all there is to it.

PS. it goes without saying that you must first add the routes using the route add command before doing the above procedure.

---

