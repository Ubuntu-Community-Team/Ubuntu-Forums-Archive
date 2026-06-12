---
title: "How to set DNS for static server"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by JD32 on 2013-07-08
I'm sorry if this has already been over im sure it has but about after an hour of searching I'm still stuck. Anyway,

I have a Ubuntu server running that i want to keep set static. What i don't know is how to obtain my DNS server IP address and where to put it? in the[COLOR=#111111][FONT=Consolas]/etc/network/interfaces file? 


[/FONT][/COLOR]```
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static


address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1



```
[COLOR=#111111][FONT=Consolas]
This is what i have and it works fine on my LAN. I just need it to get to the internet too!

Any help?
[/FONT][/COLOR]

---

### Post by papibe on 2013-07-08
Hi JD32.

Try this:
```
auto lo
iface lo inet loopback

auto eth0

iface eth0 inet static
  address 192.168.1.5
  netmask 255.255.255.0
  gateway 192.168.1.1
  **dns-nameservers** 192.168.1.1
```
Replace 192.168.1.1 with another address if your router does not work as DNS. For instance OpenDNS' 208.67.222.222, or Google's 8.8.8.8

You need to restart the networking stack to take effect:
```
sudo service networking restart
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by JD32 on 2013-07-09
That did the trick, I should have known that!

But thanks anyhow!

---

