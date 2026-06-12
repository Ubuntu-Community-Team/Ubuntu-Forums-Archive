---
title: "wireless not working on windows8, ubuntu 12.10 is fine"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by pshuk on 2013-02-06
Hi,    I recently changed from win7 to Ubuntu 12.10 on one of my laptops. Since then, my wireless is acting strange. I have 2 other laptops (win7 and win8) and ipad. As soon as I start my Ubuntu, all other devices show limited connectivity to the wireless (and no internet access). And if I shut down my Ubuntu laptop, they all get access to wireless. Can anyone help me ?  thanks

---

### Post by carl4926 on 2013-02-06
Possibly they are competing for access
Make sure there are sufficient LAN addresses available by DHCP in the wireless router settings

---

### Post by pshuk on 2013-02-06
> **carl4926 said:**
> Possibly they are competing for access
Make sure there are sufficient LAN addresses available by DHCP in the wireless router settings

 Sorry, it might sound stupid but how do I make sure of this. I have set the max. no. of DHCP users to 50 and am using Automatic configuration DHCP. Is there anything else I should do at my Ubuntu machine?

---

### Post by carl4926 on 2013-02-06
> **pshuk said:**
> Sorry, it might sound stupid but how do I make sure of this. I have set the max. no. of DHCP users to 50 and am using Automatic configuration DHCP. Is there anything else I should do at my Ubuntu machine?

So that sounds like you already have such a setting.
Lets say your router login IP is 192.168.0.1
The first LAN IP would likely be 192.168.0.2 and the range can be set from here accordingly
It's usually under LAN setup
Start IP
Finish IP

You may also want to consider rebooting the router.
And whilst I doubt it, consider if you are using Address reservation... this is where each connecting device is assigned a LAN IP by it's device MAC address

---

