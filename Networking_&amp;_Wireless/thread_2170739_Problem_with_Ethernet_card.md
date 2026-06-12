---
title: "Problem with Ethernet card ?"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by ndnd on 2013-08-27
Hi, 
I am new to linux. I have installed Ubuntu 10.xx server version. It was originally setup with for static IP and It worked fine and was shutdown for 4-5 months. I recently started it again updated the new ip details (tried both static as well as dhcp as I had options for both) in interfaces file and when I restarted the network got error (attached). 

I checked few places online there seems to be people mentioning that this could be because of Mac address going wrong but I find that weird. Also, I am not sure how to check that and modify it. 

Also, at the back of the server where there Ethernet cable get's attached to the card I don't see any lights (steady or blinking) if my understanding is correct that shouldn't be the case. 

Thanks in advance for any help insight in this matter.

Again, this system worked fine when it was shutdown and was started after couple of months and I faced this problem.

---

### Post by wildmanne39 on 2013-08-27
*Thread moved to **Networking & Wireless**.*

---

### Post by ndnd on 2013-08-27
Sorry for posting in wrong section

---

### Post by wildmanne39 on 2013-08-27
No worries, just putting it where you will get the most help.

---

### Post by ndnd on 2013-08-27
Problem solved 

Two links helped solve it 

> [http://blog.inventic.eu/2013/03/ubuntu-eth0-error-while-getting-interface-flags-no-such-device/](http://blog.inventic.eu/2013/03/ubuntu-eth0-error-while-getting-interface-flags-no-such-device/)
[https://forums.virtualbox.org/viewtopic.php?f=7&t=43090](https://forums.virtualbox.org/viewtopic.php?f=7&t=43090)


Based on the above I did: 
> 
$lspci
The output at the end suggested the Ethernet device was working fine. 
Now 
Ifconfig eth0 
Ifconfig eth1
Ifconfig eth2  (finally it showed mac addresses here)


Now two options either modify the /etc/network/interfaces file to have eth2 instead of eth0 or reset so that eth0 label becomes on. 
So I reset the label by deleting the file 

> $sudo rm /etc/udev/rules.d/70-persistent-net.rules 

After this I rebooted the system and I was all set......!

---

