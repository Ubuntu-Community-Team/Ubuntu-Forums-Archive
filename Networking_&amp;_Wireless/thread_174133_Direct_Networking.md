---
title: "Direct Networking"
date: 2006-05-11
forum: Networking &amp; Wireless
---

### Post by JNowka on 2006-05-11
I have two computers and I am trying to network them directly.  I have plugged one Ethernet cord into both computers.   One is a Ubuntu and the other is Windows XP HE.  I have got them both to recognize that the cord is in and both computers are on and ports active, but from there no luck.  

I have used the following to help me with my endevor.
[https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba) [http://static.kdenews.org/content/siddhuwarrier/20030610/](http://static.kdenews.org/content/siddhuwarrier/20030610/) 


The windows computer says that it sends out data but recieves none back.  I am unsure on how to look for ips for connecting machines on the network.  

At the start up list for ubuntu it waits a while for the network interface to come up and thien gives an error message that says that there is a Temporary problem with the naming resolution.  

I have the configuration set up to be DHCP in System->Admin->Networking for the ethernet port being used.

And to my best knowledge from both of the websites I have done everything correctly.

---

### Post by vigos on 2006-05-11
Well I assume you've used a cross-over cable otherwise the ports on both computers wouldn't be active. 

Have you done an ipconfig on the Windows XP machine and an ifconfig -a on the linux box to check the ip addresses?

It maybe that there is a routing problem, also do a netstat -rn on both boxes and show the results

---

