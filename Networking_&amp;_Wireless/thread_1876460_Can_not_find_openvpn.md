---
title: "Can not find openvpn"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by xavi fernandez on 2011-11-06
Hi all, I install open vpn for import my vpn that I use in windows to ubuntu 11.10 and when I try find the program doesn't appear, I'm typing in the dash home, and nothing.
Any help will be appreciated.

Thanks in advance

---

### Post by praseodym on 2011-11-06
Hi,

you can install openvpn as a tool for the network-manager-applet:

```
sudo apt-get install --reinstall network-manager network-manager-gnome network-manager-openvpn network-manager-openvpn-gnome
sudo service network-manager restart
```

---

### Post by xavi fernandez on 2011-11-06
Thanks Praseodym, I just put the commands in the terminal, after that was running the terminal with so many lines there,when finished I close it, and try search for the software in the dash home but nothing.
Should I remove it and install again? I tried already install with the terminal like

sudo apt-get install openvpn

and as well from the option in the software center, do you think this app is not working well for ubuntu 11.10?

Thanks for your time

---

### Post by praseodym on 2011-11-06
Right-click on the NetworkManager applet->Edit connections. Choose VPN there->Import

---

### Post by xavi fernandez on 2011-11-06
Praseodyn, thanks again for your help and your patience, I'm really new in linux. I did what you say but I can not import nothing because I can not find it. What I tried to do is Alt+F2 and in the searching bar appears the an icon from openvpn and another from ca.crt that are the file that I need for set up the vpn... I hope!!!
But when I click in the icons, nothing happen, what can I do?

---

### Post by praseodym on 2011-11-06
The Wifi-symbol right of the envelope in the top bar.

---

### Post by xavi fernandez on 2011-11-07
Yes, the problem is that when I follow this steps and click in import, in the options are not the ca. crt files that I need and not the openvpn, that's why I can not import the files. In the only place that I've seen this files was in the panel from the picture on my last message. I hope you understand what I say cos I really don't know how to access to this files.

Thanks

---

### Post by duboisj on 2012-01-08
> **praseodym said:**
> Hi,

you can install openvpn as a tool for the network-manager-applet:

```
sudo apt-get install --reinstall network-manager network-manager-gnome network-manager-openvpn network-manager-openvpn-gnome
sudo service network-manager restart
```


I am using 11.10 on a 64-bit machine & could not get the openvpn plugin for network manager to install correctly.  It appears to me that somewhere in the setup teh 64-bit options were not set properly.  Running the above re-install and restart of the network manager service finally gave me an openvpn option in the network manager.

Prior to running that, even with a reboot, the openvpn option would never appear in the network manager.  The prior package I tried to install was network-manager-openvpn_0.9.0-0ubuntu1_amd64.  That didn't work.  (the forced reinstall above caused apt-get to find network-manager_0.9.1.90-0ubuntu3_amd64.deb, which might be the reason I was having trouble, although I'm not sure why the 0.9.0 package didn't complain if there was a newer one on the system ... maybe something I don't understand.  Anyway, the above lines worked for me).

---

