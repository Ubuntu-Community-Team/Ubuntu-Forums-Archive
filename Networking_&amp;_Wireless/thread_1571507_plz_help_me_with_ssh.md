---
title: "plz help me with ssh"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by shakibv on 2010-09-09
hi , i've 2 laptops and a adsl wireless router (configured to redirect ssh port 22 to my local network) , i have ubuntu 10.04 lts on my both laptops i installed openssh-server on one and try to connect to it from the other one , it's ok when i use my local ip addresses but when i try ssh username@external ip it connect to my laptop but when entering pass just says permission denied what should i do ??

---

### Post by CharlesA on 2010-09-09
Try connecting using ssh -v user@host

---

### Post by joeaura7 on 2010-09-09
make sure the username is correct. the username is the username that is logged on on the server (the computer that has openssl-server) and something with the password.

---

### Post by shakibv on 2010-09-09
tnx for you replies i checke user/pass they are correct , my problem is that when i  use my local address az host eg. 192.168.1.2 it works but when i use my real external ip address (i mean adsl router) it connect to ssh port but when entering pass just reply permission denied :(

---

### Post by shakibv on 2010-09-09
this is what my terminal look likes : ( 78.39.139.231 my external ip )

shakib@shakib-laptop:~$ ssh shakib@78.39.139.231
The authenticity of host '78.39.139.231 (78.39.139.231)' can't be established.
RSA key fingerprint is d6:8f:96:ec:73:70:67:33:70:a7:52:a6:8a:2f:56:14.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '78.39.139.231' (RSA) to the list of known hosts.
shakib@78.39.139.231's password: 
Permission denied, please try again.
shakib@78.39.139.231's password: 
Permission denied, please try again.
shakib@78.39.139.231's password: 
Permission denied (publickey,password).
shakib@shakib-laptop:~$ 

----------------------------------------------------------------------

this is ssh using my local ip

shakib@shakib-laptop:~$ ssh shakib@192.168.1.2
shakib@192.168.1.2's password: 
Linux shakib-laptop 2.6.32-25-generic #43-Ubuntu SMP Wed Sep 1 09:46:39 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

Your CPU appears to be lacking expected security protections.
Please check your BIOS settings, or for more information, run:
  /usr/bin/check-bios-nx --verbose

Last login: Fri Sep 10 02:52:23 2010 from shakib-laptop.local
shakib@shakib-laptop:~$

---

### Post by dmizer on 2010-09-09
This is a router problem.

Most retail routers do not have the capability to do loopback. What this means is that while you are on your LAN, if you try to connect to your external IP address, you are simultaniously sending traffic out and requesting traffic in. This confuses the router so nothing happens.

Test SSH from a location other than your home, and it should work fine.

---

### Post by shakibv on 2010-09-10
thank you dmizer :) you are right , when i connect from another location it works :)

---

