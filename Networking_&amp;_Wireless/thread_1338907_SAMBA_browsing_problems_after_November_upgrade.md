---
title: "SAMBA browsing problems after November upgrade"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by UncleAelfrich on 2009-11-26
I have a home network with an Ubuntu 9.10 file server which I installed on November 6, 2009; (it was a clean install from a previous 8.04 server.) I have three Windows 7 machines on the network. I was able to browse my Samba shares on my windows 7 machines just fine until I updated samba on November 13. During the update, it gave me the option to keep my old smb.conf file or switch to the new one. I kept my old one.

Since then, I have been unable to browse Samba shares on my Windows 7 machines through the network icon. I can connect to the shares by using the Windows run command, but I need/want to be able to browse the shares via Windows networking as I was before I applied the update.

Can anyone help me with this problem please?

---

### Post by dmizer on 2009-11-27
Please see the 6th link in my sig.

Also, make sure you have all the latest updates by running this command
```
sudo apt-get update&&sudo apt-get full-upgrade
```

---

### Post by UncleAelfrich on 2009-11-27
I had looked at your link before. Problems one and two I had already solved much earlier. My smb.conf file had implemented both of these fixes. For problem four, I don't believe it is a problem because I ran the command and it appears that my command line response matches the one for iptables and a firewall that is disabled.

For Problem 3, I followed the information for Jaunty/Karmic regarding uncommenting the line for name resolution order and put host at the end of the line. However, I have not installed winbind. (NOTE that under 8.10, I did not need to have the line uncommented or to have installed winbind.) This change did not fix the problem.

When I attempted sudo apt-get full-upgrade, my response was "Invalid operation full-upgrade".

One thing I have noticed is that when I restart my 9.10 server, I am unable to connect to the server from my Windows 7 machines until I restart the Windows 7 machine. Once I do that, I can access the samba shares via Windows "Run" command, but I am not able to browse shares via the network in Windows Explorer.

---

### Post by UncleAelfrich on 2009-11-29
bump

---

### Post by dmizer on 2009-11-29
Try this:
```
sudo aptitude full-upgrade
```

---

