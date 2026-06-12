---
title: "VPN Connection in lubuntu.."
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by Lyoko on 2010-10-04
hello, recently i have installed the great ubuntu version called lubuntu.. i would like to use it but i can't get vpn connection up and running..

when i use the nework manager applet, i click on vpn tab **and the "Add" button is blocked..**
so i don't have any idea how to get around this problem, i can't install alternatives to network manager, Because that vpn is my internet connection through the ISP..

So, i really hope you could help me guys..

---

### Post by mikewhatever on 2010-10-05
You need to install one of the Network Manager plugins to use vpn.
Check out the Quick Start part of the howto.
[https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)

---

### Post by Lyoko on 2010-10-05
ok, what is the easiest way to do it while i don't have internet connection to get that plugin?

---

### Post by elperrillo on 2010-10-05
There is not guide available for Lubuntu. VPN connection in Ubuntu can be challenging. Follow this guide for Ubuntu. It works for me all the time, make sure not to skip any steps.

[http://geekyprojects.com/ubuntu/ubuntu-vpn-connection/]("http://geekyprojects.com/ubuntu/ubuntu-vpn-connection/")

---

### Post by mikewhatever on 2010-10-05
> **Lyoko said:**
> ok, what is the easiest way to do it while i don't have internet connection to get that plugin?

You could use [Keryx]("http://keryxproject.org/") to get the required package + dependencies.

If you want to tackle it manually, and assuming your ISP uses pptp, you'll need the following two packages:
```
network-manager-pptp pptp-linux
```

They can be downloaded from [http://packages.ubuntu.com](http://packages.ubuntu.com).

---

