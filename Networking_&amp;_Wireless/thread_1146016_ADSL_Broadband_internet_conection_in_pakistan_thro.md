---
title: "ADSL Broadband internet conection in pakistan through PTCL"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by simbiwa on 2009-05-02
I recently got a broadband connection from PTCL in Pakistan,Karachi.
The technician of PTCL set up on my XP , and it started working fine. I asked him to set up on my Ubuntu  9.04 OS as well but he said he has no idea how to set it up on Linux.

The modem that came with this setup is Huawei , Does any one have an idea how I can set up so that I can connect to internet? 
Any help will be appreciated. thanks

---

### Post by lisati on 2009-05-02
If it already works with XP, there is a good chance that it will work with Ubuntu without you having to change any settings.

---

### Post by simbiwa on 2009-05-02
Thanks for a quick reply, but somhow it is not working in Ubuntu 9.04.

---

### Post by simbiwa on 2009-05-02
Bump

---

### Post by simbiwa on 2009-05-03
I managed to solve the problem by doing the following, I am posting this to help out someone who might have the same problem.

1.Removed and purged Network Manager.

2. edited /etc/resolv.conf 
   
nameserver 203.99.163.240 (PTCL dns server)
nameserver 203.99.163.243

3. edited /etc/network/interfaces

  auto eth0 
  iface eth0 inet static
  address 192.168.1.2  (ip of my NIC)
  netmask 255.255.255.0
  gateway 192.168.1.1 (ip of modem)

This is for the wired modem/router

---

