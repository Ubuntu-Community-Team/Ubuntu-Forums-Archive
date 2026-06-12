---
title: "not able to connect wireless network"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by baksheen on 2009-02-15
Hi friends,

I am new to linux.  Actually I want to configure my wireless net work connection in Ubunt 8.04.1 LTS.  I gave ip address and everything. But I am not able to connect to network. That means if I am using first time the network it will first ask network key. But I dont know where I can give the network key. I could not find out any option for giving network key.  So Please help me to solve this problem.

I could connect to wireless network in window xp.


Thanks
Bhanu lakshmi.

---

### Post by x33a on 2009-02-15
first you need working drivers. have you loaded the drivers? post the output of ifconfig, iwconfig, and iwlist scan.

---

### Post by indeterminate on 2009-02-15
Do you mean that you don't know how to find out what the key for your network is? Or that you don't know how to tell that key to Ubuntu?

To find out what your network key is, you should use a computer already connected to your network, and browse to your wireless access point (probably [http://192.168.0.1](http://192.168.0.1) or [http://192.168.1.1](http://192.168.1.1)). Enter the admin name and password. One of the sections should be called "wireless security" or "WEP key" or "WPA passphrase" or something like that. That's the key you need.

To get Ubuntu to ask you for it, click the NetworkManager icon which should be in your notification bar (probably next to the volume icon). You should see a list of wireless networks; select yours. It should prompt you for the network key.

If it doesn't, you can manually edit your connection settings: right-click the NetworkManager icon and select "Edit Connections". On the Wireless tab, select your network and click Edit. Click the Wireless Security tab and enter the network key.

Hope that helps.

---

### Post by hridyagati on 2009-02-15
Hi
Check if you have to use a static IP or the IP is to be assigned automatically by the ISP...

Thanks

---

