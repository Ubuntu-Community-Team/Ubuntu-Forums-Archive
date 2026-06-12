---
title: "Configure server dhcp or static?"
date: 2011-12-23
forum: Networking &amp; Wireless
---

### Post by Yumi on 2011-12-23
My small networks hardware is connected by a wireless router. The router also acts as dhcp server. This is convenient as guests can easily connect without the need for a static IP to be issued.

Now I am to connect a server. The advice in the net is to configure the server to a static IP address. I set the router to always issue the same IP address 192.168.0.10 to the servers MAC address.

Question: in the servers configuration file should I set it to "dhcp" or "static and enter the IP as 192.168.0.10".

Merry Christmas
Michael

---

### Post by collisionystm on 2011-12-23
> **Yumi said:**
> My small networks hardware is connected by a wireless router. The router also acts as dhcp server. This is convenient as guests can easily connect without the need for a static IP to be issued.

Now I am to connect a server. The advice in the net is to configure the server to a static IP address. I set the router to always issue the same IP address 192.168.0.10 to the servers MAC address.

Question: in the servers configuration file should I set it to "dhcp" or "static and enter the IP as 192.168.0.10".

Merry Christmas
Michael

ALWAYS set a server to static.

DHCP is nice, but always keep dhcp for client machines and never for servers. Of course I am sure you would be OKAY but its just a good rule of thumb to follow... especially when you work in larger environments, which you might some day! :)

---

### Post by Yumi on 2011-12-23
Thank you collisionystm. That was a quick reply!

I did not find the answer to "can I mix dhcp and static addresses within
one network. A question you answered for me too. Obviously it is possible.

Michael

---

### Post by collisionystm on 2011-12-23
> **Yumi said:**
> Thank you collisionystm. That was a quick reply!

I did not find the answer to "can I mix dhcp and static addresses within
one network. A question you answered for me too. Obviously it is possible.

Michael


Yup. The best way to mix the 2 is to decide a range for your statics and set your DHCP around it.

For instance at my work, I have my network setup on a 172.16.64.0/19. I have 172.16.64.0 for my servers. 172.16.65.0 for my printers and 172.16.69.0-172.16.71.0 for dhcp. I can go all the way to 172.16.95.0 but I save all the extra room in case I have a dhcp server failure. Then I can just bring up a new one, set the dhcp range to something else outside of what we have and there wont be any conflicts.

This is complete over kill... I know. But I like having the freedom of such a wide address range.

On a small network, set 192.168.1.1-25 for your statics. This will give you server and printer room. Make 26-254 dhcp for your machines.

---

### Post by Yumi on 2011-12-23
:) A clear and understandable explanation. But should I ever reach your size of network I will get in a professional for sure. Until then I have to cope myself and learn the ropes.

Michael

---

### Post by collisionystm on 2011-12-23
> **Yumi said:**
> :) A clear and understandable explanation. But should I ever reach your size of network I will get in a professional for sure. Until then I have to cope myself and learn the ropes.

Michael


Good luck! If you need anything dont be afraid to ask.

---

