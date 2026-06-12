---
title: "How do I ping a Windows PC by name?"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by bamim2 on 2010-09-10
I'm running  Ubuntu 9.10. What do I need to install/setup on my system to be able to ping a Windows box by name? It seems like I used to be able to ping the PC on my network by name, but I can't any longer. I can see the Window PC on my network in the file browsers (Nautilus), but I can't ping them by name. I don't want to add them to the hosts file. That's cheating.

---

### Post by surfer on 2010-09-10
you have to have a dns server somewhere. either on your router (this would probably be the cleanest solution, if you router provides that feature) otherwise on any other machine.

dnsmasq is a very simple dns server. and yes, it reads the hosts file...

---

### Post by bamim2 on 2010-09-10
Since the Windows PC can all ping each other by name & the router shows the names all of the systems on the network, I would 'guess' that my router provides this function. Now what?

---

### Post by Joeb454 on 2010-09-10
In a terminal, type ```
ping windowspc
``` Where 'windowspc' is the name of the Windows PC :)

If this doesn't work, it might be that you need to install avahi (at least, I think it's avahi, I could be completely wrong on that :p)

**Edit:** It also depends on the router, for example, on my system, I got the following output:

```
joe@kashyyyk:~$ ping dagobah
ping: unknown host dagobah
joe@kashyyyk:~$ ping dagobah.local
PING dagobah.local (10.0.1.30) 56(84) bytes of data.
64 bytes from dagobah.local (10.0.1.30): icmp_req=1 ttl=128 time=0.894 ms
64 bytes from dagobah.local (10.0.1.30): icmp_req=2 ttl=128 time=0.947 ms
64 bytes from dagobah.local (10.0.1.30): icmp_req=3 ttl=128 time=0.960 ms
64 bytes from dagobah.local (10.0.1.30): icmp_req=4 ttl=128 time=1.07 ms
--- dagobah.local ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 0.894/0.969/1.075/0.066 ms
```

---

### Post by surfer on 2010-09-10
try to configure the networking of your ubuntu machine to use your router as dns server. use the network manager (or edit  /etc/resolv.conf ).

---

### Post by bamim2 on 2010-09-10
Where do I find "Network Manager"? It shows as bing installed on this system, but I don't see it anywhere. It's not in System>Administration (or not by that name).

---

### Post by surfer on 2010-09-11
System -> Preferences -> Network Conections
or in your gnome panel (top right) right-click the network applet.

---

### Post by bamim2 on 2010-09-11
Thank you.

---

### Post by bamim2 on 2010-09-11
My card is set to "Automatic (DHCP)". My network says my address is 127.0.1.1 though & not my actual IP address of 192.168.0.4. Do I need to set something in "DHCP Client ID"? It's blank. When I ping my Ubuntu box by name, it resolves to that 127.0.1.1 IP address. I don't have to ping it with the "name.local", but when I do, it resolves to the correct IP address. 

Also, when I try to ping one of the Windoze PC on my network by name it tries to ping some crazy IP address that's not any where near the correct IP address. I can ping everything correctly by address without a problem. 

Thanks for any help I can get...

---

