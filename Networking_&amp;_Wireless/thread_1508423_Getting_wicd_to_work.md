---
title: "Getting wicd to work"
date: 2010-06-12
forum: Networking &amp; Wireless
---

### Post by okos on 2010-06-12
I want to switch from Network Manager to WICD. I installed wicd while still having network manager installed. I disabled Network Manager and tried to connect with Wicd. WICD shows that I have an ip address when connecting but my browser says that I am disconnected. I still have network manager installed and am afraid that if I remove the package I will lose my internet connection completely. 

Can I remove network manager and wicd will start to work?

---

### Post by mobilediesel on 2010-06-13
> **okos said:**
> I want to switch from Network Manager to WICD. I installed wicd while still having network manager installed. I disabled Network Manager and tried to connect with Wicd. WICD shows that I have an ip address when connecting but my browser says that I am disconnected. I still have network manager installed and am afraid that if I remove the package I will lose my internet connection completely. 

Can I remove network manager and wicd will start to work?

When I installed wicd, the package manager automatically removed Network Manager. They're probably conflicting with each other.
Before removing Network Manager, go to [http://packages.ubuntu.com/hardy/i386/network-manager-pptp/download](http://packages.ubuntu.com/hardy/i386/network-manager-pptp/download)
and download the deb file for Network Manager so it could be reinstalled if your internet connection does stop working.

---

### Post by okos on 2010-06-15
Great idea.
I downloaded all of the NM from the repository.
I installed wicd and things got kind of wierd.
Network manager was still working and wicd was not.
I removed wicd rebooted, reinstalled wicd, rebooted and wicd started working.

Last night wicd was not working. Only NM was working.

My whole issue is not really with which manager to use. I considered using wicd since it worked so well with slackware. My real issue is that I keep getting dropped from my wireless connection with ubuntu 10.04. I thought changing to wicd would be a start.

It seems that I am not the only one with this issue but have not found any solutions.

---

