---
title: "I just want to browse the internet"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by klunuts on 2009-02-15
Oh... Oh dear lord... This is torturous. I finally have gotten my wired connection to connect, but now whenever I go to Firefox and type in a URL it comes up with the "Address Not Found" page. So, I go to Admin>Network Tools and click the "Ping" tab and just type in a URL (I used [www.ubuntu.org](www.ubuntu.org)), and it pops up with a box that says "**The address 'www.ubuntu.org' cannot be found**/ Please enter a valid network address and try again." This is going to drive me completely insane... I just want to go on the internet... Please help me...

---

### Post by zander1013 on 2009-02-16
there is a network applet on the bar on top of the desktop. it should show weather or not you are connected. it shows bars for wireless and monitor siluet if it is ethernet.

if you right click on that little network icon and select edit connections then select a connection then select edit that connection and then select IPv4 tab make sure that Method is set to automatic dhcp.

note that i have assumed that you have access to the internet through a router. otherwise you have to come up with a connection through a router or dialup modem.

---

### Post by klunuts on 2009-02-16
Ah, well, you see, if i set it to Automatic DHCP, it will say it's disconeccted. But, when I do it manually, what I'm experiencing above happens.

---

### Post by TombKing on 2009-02-16
Sounds like you are not getting any name resolution.
On your dns box put in 208.67.222.222, 208.67.220.220

Then you can try all the instructions at

[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by klunuts on 2009-02-16
Alright, I'll go try that out, thanks!

---

### Post by klunuts on 2009-02-16
Damn it, won't work... I did notice something interesting though (and is probably the problem); When I manually type in the Adress, Netmask, and Gateway, after I click "OK" it changes the Gateway to "0.0.0.0" Don't know why it's doing that...

Also, don't know if it matters, but I'm using an Apple Airport and a Motorola SB5100 SURFboard modem.

---

### Post by TombKing on 2009-02-16
Yeah that gateway address would get you nowhere.

You have me stumped as I haven't done anything technical with apple anything in 10 or more years.

---

### Post by klunuts on 2009-02-16
damn... Is it most certainly something with the Apple Airport then?

---

