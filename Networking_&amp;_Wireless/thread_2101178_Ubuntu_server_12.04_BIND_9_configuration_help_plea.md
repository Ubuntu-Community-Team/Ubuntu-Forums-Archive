---
title: "Ubuntu server 12.04 BIND 9 configuration help please."
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by AkerokSauren on 2013-01-03
I'm currently trying to configure my server with DNS server software BIND9.  I'm uncertain how to configure this properly.  This server is going to be a web server that will host the website and tools that my friend and I have built.  I have business class internet for this server, with a static IP address, subnet, and 2 DNS configurations.  Does anyone know how to configure BIND9 so that our website will be able to be accessed through the browser?

---

### Post by chadk5utc on 2013-01-04
Perhaps one of the Admins could move this to servers.

> **AkerokSauren said:**
> I'm currently trying to configure my server with DNS server software BIND9.  I'm uncertain how to configure this properly.  This server is going to be a web server that will host the website and tools that my friend and I have built.  I have business class internet for this server, with a static IP address, subnet, and 2 DNS configurations.  Does anyone know how to configure BIND9 so that our website will be able to be accessed through the browser?

This should get you started in terminal also note there are other text editors I use vi aka vim or there is nano for use on command line.
> sudo vi /etc/network/interfaces
THEN Set per your IP Info
    # The primary network interface

    auto eth0
    iface eth0 inet static
    address 192.168.3.90
    gateway 192.168.3.1
    netmask 255.255.255.0
    network 192.168.3.0
    broadcast 192.168.3.255

Then
> sudo vi /etc/resolv.conf

nameserver 192.168.3.2 #your DNS
nameserver 192.168.3.3 #your DNS

Then
> sudo /etc/init.d/networking restart

And a tutorial for BIND can be found here
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

---

### Post by jdthood on 2013-01-05
chadk5utc advises editing /etc/resolv.conf but as of Ubuntu 12.04 this is not correct because that file is dynamically generated.

---

### Post by jdthood on 2013-01-05
> **AkerokSauren said:**
> Does anyone know how to configure BIND9 so that our website will be able to be accessed through the browser?

If you are running a website on a machine and you want others to be able to access that website by domain name then you will have to register the machine's domain name in DNS.

If you want to make it available to users on the Internet then you will have to register the machine's domain name with an Internet DNS provider.

If you only want to make it available to users on a LAN then you will have to configure a nameserver somewhere (e.g., bind9) to resolve the machine's name to the machine's address and also configure the users' machines on the LAN to use that nameserver for DNS resolving.

---

### Post by linuxsyst on 2013-01-05
[http://ubuntuforums.org/showthread.php?t=1710039](http://ubuntuforums.org/showthread.php?t=1710039)
My Tutorial

---

### Post by AkerokSauren on 2013-01-07
> **linuxsyst said:**
> [http://ubuntuforums.org/showthread.php?t=1710039](http://ubuntuforums.org/showthread.php?t=1710039)
My Tutorial
Your tutorial was very informative.  I'm still having an issue, though.   I don't have the domain name at this time (trying to purchase it).  I  also can't ping my server from another computer through the Internet (I  can ping my external IP, though).  What could be the issue?  Also, the DNS server and the web server are the same computer.

---

