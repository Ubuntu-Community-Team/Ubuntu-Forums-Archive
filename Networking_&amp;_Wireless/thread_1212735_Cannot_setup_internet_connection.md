---
title: "Cannot setup internet connection"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by fcmessi on 2009-07-14
Hey,

I have Ubuntu 8.01, running as an alternate OS next to WinXP. I have an ADSL+2 modem given by my service provider, which I am able to set up pretty easily in the XP boot. In the XP boot, I just select manually configure IP and enter the IP, Subnet etc.

I would greatly appreciate if someone would guide me through the steps required to set up the same connection for ubuntu.

Thanks

---

### Post by papangul on 2009-07-14
There are many howtos available in the net for this:
[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html)

edit: what is ubuntu '8.01'?

---

### Post by fcmessi on 2009-07-14
I have already seen that stuff, but it does not seem to work with my provider.

My provider gives specific values for IP, Subnet mask and gateway. We can enter that stuff in windows in network connections. How do I find the Ubuntu equivalent of the same?

---

### Post by wojox on 2009-07-14
```
ifconfig
```

---

### Post by martinbaselier on 2009-07-14
You have the network manager in your settings. It's a graphical tool to create a connection. In it you can easily enter your settings. If you use ubuntu, there's a network icon on your taskbar. You can also access it by clicking the right mousebutton on the icon.

---

### Post by superprash2003 on 2009-07-15
look under system->pref->network connections

reference : [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by specular on 2009-08-07
Hi I just solved this same problem.
As others have said under > system > preferences > Network Configuration > Wired > Auto Etho > Edit > IPv4Settings > Method (drop down box) > Manual
the click add and click under address for the IP Address, Netmask to enter the subnetmask and gateway for the Default Gatway, then type the preffered DNS under DNS Servers.

Hope this helps all the others Greenies like me out there.

---

