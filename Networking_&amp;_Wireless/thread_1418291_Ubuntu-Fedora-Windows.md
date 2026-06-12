---
title: "Ubuntu-Fedora-Windows"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by Odaym on 2010-02-28
Hello, i have a problem concerning the above 3 OS's when it comes to putting them in one network.

I have two laptops and one desktop and 1 8-port switch 10/100M.
The first laptop has Ubuntu Karmic on it, the second has Windows 7 on it and the third Fedora 12.
All three are connected to the switch and the switch is on of course, and it's lighted to show that they are connected properly. 
The IP's are set as 192.168.0.1, 198.168.0.2 and 192.168.0.3 on all 3 respectively.
When i ping from Ubuntu to Fedora, i get a reply and it's all fine, same from Fedora to Ubuntu.
and also when i ping from windows to Fedora or Ubuntu i get normal replies and vice versa.
When i access the network on Ubuntu, I can see my Windows but not my Fedora.
When i access the network on Windows, I cannot see anything.
When i access the network on Fedora, I cannot see anything.

I have no idea what the problem is, would appreciate some help, thank you

---

### Post by pirateghost on 2010-02-28
So you are wanting to see the SAMBA shares on each one?
Are all the machines in the same workgroup?  Do you actually have the Samba share created in ubuntu and fedora?

---

### Post by Odaym on 2010-02-28
would you please tell me how to check if i do on both? although i strictly remember seeing a lot of Samba and/or SMB packages being installed on the various times that i've updated

---

### Post by pirateghost on 2010-02-28
> **Odaym said:**
> would you please tell me how to check if i do on both? although i strictly remember seeing a lot of Samba and/or SMB packages being installed on the various times that i've updated
I would suggest you read up on how to setup SAMBA for windows sharing.  there are about a million pages/tutorials out there on the subject
heres one for fedora
[http://www.reallylinux.com/docs/sambaserver.shtml](http://www.reallylinux.com/docs/sambaserver.shtml)

you will find a lot of valuable info here as well:
[http://www.howtoforge.com/howtos](http://www.howtoforge.com/howtos)

---

### Post by Odaym on 2010-02-28
thanks a lot :)

---

