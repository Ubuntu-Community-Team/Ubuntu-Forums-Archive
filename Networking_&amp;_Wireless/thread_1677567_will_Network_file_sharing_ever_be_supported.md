---
title: "will Network file sharing ever be supported"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by davethewave83 on 2011-01-28
I have installed Ubuntu within a network full of Windows7 OS but I am unable to see the network shares of the windows machines. I have poked around and tried to figure all the Samba things out but to be honest, networking has always been my weak point in computers. I can assemble computers and disassemble computers as well as troubleshoot most all other aspects to computers but when it comes to networking I am lost. 

Sometimes I can access the windows share by using the ip address of the windows machine, but only if I know the exact name of the shared folder I wish to access, but I would like to convert one of the other machines to Ubuntu as well and the user of that machine knows even less than I do about networking. 

How long will it take before Ubuntu will be released with file sharing working out of the box with Windows 7? 

Also if there is any information you can give me to help me better understand how to get network browsing to work and a more simple point-click setup I would be most grateful. I apologize for my ignorance in this area.

---

### Post by SeijiSensei on 2011-01-29
This looks like a decent tutorial with a focus on Ubuntu:

[http://ubuntu.swerdna.org/ubusambabrowse.html](http://ubuntu.swerdna.org/ubusambabrowse.html)

The simplest solution is to use an "lmhosts" file on the Ubuntu box containing the IP addresses and computer names of the machines on the network.  That works fine for a small network, but doesn't scale well if you're constantly bringing new machines online.  

Setting up Samba to be a "local master browser" is another approach.  You can force the Windows machines to acknowledge the Ubuntu server as the central repository of server names and IP addresses.  

A third, more complicated, option is to configure the Ubuntu machine to be a WINS server (if you don't have one already) and tell the Windows machines via DHCP to register their names with it.  

All these methods are described in the article above.  Fixing the order of name resolution and making Samba be the local master as the author explains may be all you need to do.

---

### Post by YesWeCan on 2011-01-29
It is supported out of the box.
Just go to "places/network"

---

### Post by davethewave83 on 2011-01-29
> **YesWeCan said:**
> It is supported out of the box.
Just go to "places/network"

this doesn't work

---

### Post by piquat on 2011-01-31
Testing thread for OP:
[http://ubuntuforums.org/showthread.php?t=1678742](http://ubuntuforums.org/showthread.php?t=1678742)

---

### Post by davethewave83 on 2011-01-31
to be more specific, when I go to places/network I can see Windows Shares, but when I try to open them I get 'Unable to mount location. Failed to retrieve share list from server. 

(( the thread let me post now :) ))

---

### Post by Morbius1 on 2011-01-31
> **SeijiSensei said:**
> Fixing the order of name resolution and making Samba be the local master as the author explains may be all you need to do.
Swerdna may have the only technically correct "Classic" Samba HowTo on the internet. I would suggest you follow the advice above and start with reordering the name resolve order:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section of smb.conf:
```
name resolve order = bcast host lmhosts wins
```Save the file and in a terminal restart samba:
```
sudo service smbd restart
```

---

