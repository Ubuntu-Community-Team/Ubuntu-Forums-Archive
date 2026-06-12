---
title: "Connecting 2 Ubuntu PCs through a crossover cable"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by cronco on 2009-09-08
Ok, I just bought a new laptop for college and slapped Jaunty Jackalope on it, and I want to transfer all my music, pictures, other data from my old desktop (which runs Intrepid Ibex) to my laptop. We're talking about tens of GB, so using DVDs, or USB flash memory is not feasible.

I thought connecting the two PCs and making a small LAN through a crossover cable would be trivial, but it has proven anything but that. I have tried every combination from the nm applet, and from what I've read, setting the IPs manually would be the way to go.
So, I have set the IP for the desktop to 192.168.1.11 and for the laptop to 192.168.1.12, gateway to 192.168.1.11 and netmask to 255.255.255.0. But I can't even ping between them. I get "Destination Host Unreachable" every time. 

And yes, I know the cable works fine, it has been tested before.


I know it's been done before and it seems like a very noob question even to me (I've been using Ubuntu since 2007) and it would be trivial using a router or a switch, but I wouldn't actually use it afterwards so it just seems like a waste of money. Any help would be appreciated.

---

### Post by wojox on 2009-09-08
Look at this link:

[http://swiss.ubuntuforums.org/showthread.php?p=7909020](http://swiss.ubuntuforums.org/showthread.php?p=7909020)

---

### Post by uncle-c on 2009-09-08
What does your /etc/network/interfaces file on the laptop look like ?

---

### Post by cronco on 2009-09-08
wojox, thanks for the idea, it seemed like the natural thing to do at first, but it just wouldn't work. Thinking the cable might be the issue in the end, I went to a friends house to get a replacement.

I took my laptop with me to check if I could at least connect to his desktop (also running Ubuntu). Trying the "Link-local only" setting, the pcs appear to connect, they both get IPs, but pinging wouldn't work. 

Now, here comes the weird part. Pulling the cable from my laptop and putting it in his, the connection worked out of the box. (link-local only).

Both laptops are running 9.04. 

Another interesting detail is the fact that all the PCs I've tried connecting through this method all choose an address from the 169.254.8.x family. My laptop always chooses 169.254.7.131. Manually setting my IP to an IP from the 169.254.8.x family doesn't help either.

uncle-c, my /etc/network/interfaces is as follows:

```

auto lo
iface lo inet loopback

```

---

### Post by uncle-c on 2009-09-09
/etc/network/interfaces file should look something like this :

```
unclec@unclec-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.3.** 
netmask 255.255.255.0
network 192.168.3.0
gateway 192.168.3.1
broadcast 192.168.0.255
unclec@unclec-desktop:~$ 

```

address ( 192.168.3.**) is the IP address of the machine. You can try to set this manually using the ifconfig command and then edit the /etc/network/interfaces file accordingly. Obviously if there is no network and the two computers are linked with a crossover cable then you can omit the network, broadcast and gateway values

---

### Post by Iowan on 2009-09-09
> **uncle-c said:**
> 0[/COLOR].255
unclec@unclec-desktop:~$ 

```

Typo? 192.168.3.255?

---

