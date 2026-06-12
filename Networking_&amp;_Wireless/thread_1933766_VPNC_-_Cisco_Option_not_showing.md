---
title: "VPNC - Cisco Option not showing"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by BlastXng on 2012-03-01
Hey Folks

I installed VPNC on Ubuntu 11.10 / Kubuntu 11.10 however when I go to the Gnome Network Manager and try to create VPN the only selection type I have is Microsoft PPTP. I have no Cisco option or vpnc option as a selction. 

I have installed vpnc wihch installed network-manager-gnome using this link:

[http://www.ubuntugeek.com/how-to-install-cisco-vpn-client-on-ubuntu-11-10.html](http://www.ubuntugeek.com/how-to-install-cisco-vpn-client-on-ubuntu-11-10.html)

Output shown below of after the installation.. 

BlastXng@DarkUntu:~$ sudo apt-get install network-manager-gnome
[sudo] password for BlastXng: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-gnome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
BlastXng@DarkUntu:~$ sudo apt-get install vpnc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vpnc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
BlastXng@DarkUntu:~$ 

I did reboot after I installed these pieces, but the option to set-up/configure a Cisco VPN.. 

Any thoughts or suggestions?:confused:

Thanks

---

### Post by zappaff on 2012-03-13
Same in here. Please help. I have to use ubuntu in china because i cannot change my windows system's language to english.

---

### Post by adurand on 2012-03-20
Hey guys, not sure if you figured it out yet or not, but I'll go ahead and provide the answer in case someone else comes across this post. What you need is to install network-manager-vpnc-gnome and the option should show up!

```
sudo apt-get install network-manager-vpnc-gnome
```

---

