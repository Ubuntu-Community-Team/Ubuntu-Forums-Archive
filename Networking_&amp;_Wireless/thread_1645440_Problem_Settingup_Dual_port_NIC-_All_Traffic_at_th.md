---
title: "Problem Settingup Dual port NIC- All Traffic at the same Interface"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by rsh2000 on 2010-12-14
Hello All,

I am trying to setup IP addresses for my dual port NIC on Ubuntu 10.10
I have attached my /etc/network/interfaces file.
I removed network manager packages and added /etc/inet.d/networking to startup
everything is fine and all IP setting are applied on the startup ( the output of ifconfig is the second attachment)

Now the problem is that all the input traffic( no matter to which IP) goes to the same NIC(eth1) !

So i was wondering if i am making any mistake on my approach for setting up the IPs?

If anybody had the same experience before, would you please share it.

Thanks,
RSH

---

### Post by rsh2000 on 2010-12-14
To add more details,
when i check the arp table of other computers connecting to my server, i see that for all the IPs the same MAC address ( the one for eth1) is assigned !

So now i guess there should be a problem with arp reply !

---

### Post by rsh2000 on 2010-12-15
I am still hopeful to get an answer ;)

and I have an update, i though maybe there is a teaming process active in my NIC, so i decided to activate NIC bonding, this way at least i have control over load balancing. so i used this ([https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)) tutorial (I used mode=0) and it works fine. Now the problem is that i don`t have access to Internet and i need it ! For this i need to use dhcp, but i don`t now how to use NIC bonding with dhcp !
Does any one know any solution for this new problem ?

---

### Post by rsh2000 on 2010-12-15
It is solved.
This worked for me: :) 
[http://ubuntuforums.org/showthread.php?p=10243389#post10243389](http://ubuntuforums.org/showthread.php?p=10243389#post10243389)

---

