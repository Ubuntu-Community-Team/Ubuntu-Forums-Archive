---
title: "Routes not persistent"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by computerman on 2010-09-01
Hello, 

I have a ubuntu 10.04.1 install with openvpn, so I have some routes in my /etc/networking/interface file. But for what ever reason when it boots the routes don't come up and I have to restart the networking before they come up. Once I do that all is well. Any idea's why it's doing that?

Thanks!

---

### Post by computerman on 2010-09-04
I added the up and down commands in my config and they come up as they should. I though I tried that at one point but I don't think ubuntu can handle 192.168.1.1/16, instead i had to give it the full netmask. IE 192.168.1.1 255.255.255.0. 

Cheers

---

