---
title: "How to set up ssh connection (over internet) using MTS MBLaze modem ?"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by shan23 on 2011-08-06
I have a MTS MBlaze USB dongle, with which I can connect to the internet. The question is, how do I set up a **ssh connection accessible over the internet** so that any one can connect to my PC through that (using valid username/password provided by me of course) ? If not possible, what do I need to make this possible ?

---

### Post by pytheas22 on 2011-08-06
It should be relatively simple.  Assuming you have your Internet connection working correctly on Ubuntu, you only need to install an OpenSSH server on your Ubuntu computer for receiving connections.  You can install it with the command:
```

sudo apt-get install openssh-server
```

Now anyone will be able to connect with a command like ssh username@your-ip-address

If your Ubuntu computer is separated from the public Internet by a firewall, you will need to configure port forwarding on your router so that requests on the ssh port (port 22 by default) are forwarded to your Ubuntu machine.

---

### Post by shan23 on 2011-08-06
Thanks for the quick reply. However, what happens if I'm being connected to the net using DHCP (by my service provider) ? So, would I still be able to connect from anywhere using root@<ip address> ?

---

### Post by pytheas22 on 2011-08-06
> **shan23 said:**
> Thanks for the quick reply. However, what happens if I'm being connected to the net using DHCP (by my service provider) ? So, would I still be able to connect from anywhere using root@<ip address> ?

Yes, you can still connect from anywhere, but you need to know the IP address leased to you by your ISP at the time you want to connect.  Obviously that can become complicated if the DHCP address changes frequently.  I don't know of any way around this difficulty, other than to get a static IP address, but I think most ISPs make you pay extra for that.

---

