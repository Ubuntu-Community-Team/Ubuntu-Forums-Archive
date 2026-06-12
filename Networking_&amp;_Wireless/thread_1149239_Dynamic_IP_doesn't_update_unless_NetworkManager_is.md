---
title: "Dynamic IP doesn't update unless NetworkManager is restarted. (8.10)"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by Ursa on 2009-05-05
I'm having trouble with my connection dying over night, when I get it running again my IP-adress has always changed so I guess that's why it dies.

How can I get Ubuntu to update the IP automatically?

I run Ubuntu 8.10.

---

### Post by Ursa on 2009-05-05
Doesn't anybody have an answer?

I do a /etc/init.d/NetworkManager restart to make it work again.

How does Ubuntu normally handle dynamic IP adresses?

Also: *bump* ;)

---

### Post by jowilkin on 2009-05-05
Your ip address shouldn't change while the computer is on.  Do you shut down the computer overnight?  Or put it to sleep?  Is your connection wired or wireless?

Did you try right clicking on the network manager icon and disabling networking then re-enabling it?  Or left clicking on the icon and clicking on the name of your connection?

---

### Post by Ursa on 2009-05-05
It shouldn't? Maybe it changes because I restart NetworkManager then?

I have my computer up and running 24/7. Wired network. There shouldn't be any processes putting it to sleep and I don't do it manually.

It's like this:
I leave my computer on during the night, when I get back to it in the morning the connection's sometimes down. If the connection dies, it's always around 04:00.
`ifconfig eth0 down && ifconfig eth0 up` changes nothing, I have to do `/etc/init.d/NetworkManager restart` for it to work again.

I use wmii so I don't have the icon, but I guess ifup/ifdown or ifconfig something does the same thing as clicking the icon.

I always blame my forsaken ISP for these things, I get the feeling they're screwing around with the network 04:00 at night because they're evil. ;)

---

