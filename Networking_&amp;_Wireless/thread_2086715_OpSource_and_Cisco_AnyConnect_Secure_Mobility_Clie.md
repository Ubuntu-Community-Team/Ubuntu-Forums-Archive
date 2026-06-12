---
title: "OpSource and Cisco AnyConnect Secure Mobility Client"
date: 2012-11-21
forum: Networking &amp; Wireless
---

### Post by hank22077 on 2012-11-21
Hello folks, haven't visited for a while.

I have some general issues.
1st. OpSource is offering a $200 credit for their pay-as-u-go VPS services. I signed up and was wondering if anyone else has tried their service. It sounds great. But, I've had issues which I was hoping the community could help me with.

It appears they only offer: Ubuntu 8.04.4 LTS (64-bit) and Ubuntu 10.04 LTS (64-bit) servers. Also, they use the Cisco AnyConnect Secure Mobility Client to provide ssh root access.

So, 2nd. They provide the certificate for Cisco free, but;  The auto download they have does not work. The link they provide doesn't install on Ubuntu 12.04 LTS. I can't get it to work via NetworkManager as well as Remmina. 

So, not wnting to pass up the $200 credit I just wanna know if ANY one has/is using OpSource/Cisco successfully with Ubuntu 12?

Any advice would be appreciated.

Thanks

---

### Post by netopalis45 on 2012-11-21
You could use the network manager to do this. I connect to a Cisco VPN at my school and the AnyConnect client is uncompatible with 12.04 (last I checked). This site gives directions on how to install openconnect. 
[http://www.humans-enabled.com/2011/06/how-to-connect-ubuntu-linux-to-cisco.html](http://www.humans-enabled.com/2011/06/how-to-connect-ubuntu-linux-to-cisco.html)
Hope this helps.

---

### Post by galfly on 2013-03-12
Hi,

AnyConnect VPN client IS compatible with 12.04 and installs and works fine. Cisco supports Ubuntu.

Hank, what does your syslog say about the attempted installation? Do you have xterm on Ubuntu?

---

