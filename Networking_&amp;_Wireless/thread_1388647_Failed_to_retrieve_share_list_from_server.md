---
title: "Failed to retrieve share list from server"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by llawwehttam on 2010-01-23
I have a share on my home server with all my music in. When I go to a windows PC ( Windows 7) and go to network I can see the share, but when I try to connect in ubuntu by going to places>network>windows network  I get the error 

Unable to connect
Failed to retrieve share list from server

however when I try the connect to server option and specify the IP address its fine. I have tried this with the firewall disabled with the same results.

I am trying to get my family to use ubuntu and I don't want them to have tp specify an IP address.


Any ideas?

---

### Post by Morbius1 on 2010-01-23
Want the fastest way?

Go to Connect to Server again using the ip address and when Nautilus opens up to that location, **Bookmark** it. It will show up under "Places" on the left panel on nautilus exactly like a "mapped drive" does in Windows. If you right click that entry you can even change it's name.

---

### Post by llawwehttam on 2010-01-23
> **Morbius1 said:**
> Want the fastest way?

Go to Connect to Server again using the ip address and when Nautilus opens up to that location, **Bookmark** it. It will show up under "Places" on the left panel on nautilus exactly like a "mapped drive" does in Windows. If you right click that entry you can even change it's name.

I was considering that and it works great but I really want to get the problem fixed properly. This will do great as a temporary fix but its really quite annoying as my sister's windows 7 laptop can see all the shares but none of my ubuntu machines can. I have heard this is a gnome specific bug but I can't test that right now.

Any fixes are appreciated.

---

### Post by Morbius1 on 2010-01-23
What OS is on the server?

---

### Post by llawwehttam on 2010-01-23
Its just running ubuntu on that server but the problem is not caused by the server. To update the problem I if disable the firewall on the machine I am trying to connect from and it all works. What service / ports should I be allowing in the firewall apart from samba and netbios-scan ?

---

### Post by Morbius1 on 2010-01-23
I don't use a firewall on each machine because I'm behind a router, but if I remember correctly the following ports need to be open:

135
137
138
139
445

tcp and udp 

If I'm wrong I'm sure to be corrected shortly.:)

---

### Post by llawwehttam on 2010-01-23
Right that works great and lets me connect but for some reason the folders in networked computers appear empty ( there are things in them).

Any ideas what port is needed for that?

EDIT: used wireshark to find out. I needed 53960 but i still can't mount the share. Guess I just need to allow another port.

---

### Post by Iowan on 2010-01-23
Have you seen [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To for Windows (Samba) sharing problems?

---

### Post by llawwehttam on 2010-01-23
> **Iowan said:**
> Have you seen [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To for Windows (Samba) sharing problems?

No I hadn't seen that. Thanks a lot --> problem fixed

---

