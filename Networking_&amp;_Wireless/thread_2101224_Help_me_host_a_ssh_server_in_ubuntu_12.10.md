---
title: "Help me host a ssh server in ubuntu 12.10?"
date: 2013-01-04
forum: Networking &amp; Wireless
---

### Post by KIRON127 on 2013-01-04
so as the title implies, im trying to figure out how to host a ssh server on my old laptop running ubuntu 12.10. my main purpose for the server would be to connect to my ssh server on my laptop for tunneling purposes mostly to get around web filters of some public hotspots and whatnot while on my evo 4g lte (android). The problems im having are 1.since most of the guides ive found lead to an address that has 192.168.blah i assume they only work if you are on the same network as the server which doesn't fit my needs. and 2. most of the guides seem really complicated and i get lost since im not exactly a wizard when it comes to linux.

if anyone can help me out in getting this started i would really appreciate it :)

---

### Post by Rocklobster690 on 2013-01-04
First install OpenSSH server on your old laptop:

     $ sudo apt-get install openssh-server

Setup a Port Forwarding rule using the Router's Web Interface: 

     Port 22 both TCP and UTP point to the old girl's IP address. 

Fin.

Test using phones 4G network and SSH app by connecting to your WAN IP address (or Public DNS if you have one) and can be found out by typing "what's my ip address" into Google Search.

If you want to setup port tunneling to use HTTP on your old laptop here's how:

     $ ssh -L 80:<OLD-LAPTOP-IP>:80 <USER>@<WAN-IP>

If your requirements are different from what I gathered just post a little more info.

---

### Post by KIRON127 on 2013-01-04
thanks! that sounds a lot easier than the rest of the guide i have found make it seem. ill try it out and let you know later today when i get home :)

---

