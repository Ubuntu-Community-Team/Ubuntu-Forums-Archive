---
title: "wireless working but not wired?"
date: 2012-06-10
forum: Networking &amp; Wireless
---

### Post by itba on 2012-06-10
I had my wired connection working fine on my ubuntu machine until 2 days ago when I last turned on my computer. Today I turned my computer on, and it is catching the wireless connection on my LAN but when I plug the wire, it shows Auto eth0, but it just refuses to connect.
I am confused how that could have happened. I plug the same cable into another computer and the wired connection works on it.
Any suggestion on how I can get my wired connection to work back again?
here's the info from lspci
```

lspci|grep Network
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```and this is what ifconfig returns:
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

```

---

### Post by sudodus on 2012-06-10
I suggest that you try to find out if it is a hardware or software problem.

- Can you boot a live session from a CD or USB drive? It should readily connect via wired ethernet if the hardware is OK.

---

### Post by itba on 2012-06-10
> **sudodus said:**
> I suggest that you try to find out if it is a hardware or software problem.

- Can you boot a live session from a CD or USB drive?  It should readily connect via wired ethernet if the hardware is OK.

hi sudodus,
I booted from my CD and it gave me the same problem. It couldn't recognize wired. does that mean it is a hardware issue.
I did run this command a week ago and I wonder if that messed up anything?
```

sudo sysctl -w net.ipv4.ip_forward=1;

```also, when I turn off wireless and let it find wired, it used to show the up/down arrow icon, but now it tries to connect to Auto eth0 as if it is wireless, i.e. the wireless icon displays as it would when I try to connect to a wireless network.

I should also mention that the last time the wired connection was working I was having the following issue - with the wired connection on, it would try to look for a wireless and I had to turn the wireless switch off to prevent the conflict. 

I also noticed that in 
```
/etc/network/interfaces
```
I only had the following 2 lines:
```

auto lo
iface lo inet loopback

```
so I just added 
```
Auto eth0
```

and rebooted my computer, but to no avail

---

### Post by sudodus on 2012-06-11
I think that the settings of your installed system is not used at all when you run a live session booted from CD/USB. So it indicates that there is something wrong with your ethernet hardware. The only exception would be if you have changed some hardware setting (switch) or changed the BIOS setting, but I don't think so (you should remember that).

Have you had any incident with a high voltage peak, for example from a thunderstorm nearby? Or did you just have bad luck, that some electronic component broke spontaneously (without any obvious reason)? Except for voltage peaks, wired (ethernet) connections are very reliable.

If you want or need a wired connection, there are small USB adapters for wired (ethernet) connection for laptops. If it is a desktop/tower model, you can easily insert a cheap ethernet card.

---

### Post by itba on 2012-06-11
> **sudodus said:**
> I think that the settings of your installed system is not used at all when you run a live session booted from CD/USB. So it indicates that there is something wrong with your ethernet hardware. The only exception would be if you have changed some hardware setting (switch) or changed the BIOS setting, but I don't think so (you should remember that).

Have you had any incident with a high voltage peak, for example from a thunderstorm nearby? Or did you just have bad luck, that some electronic component broke spontaneously (without any obvious reason)? Except for voltage peaks, wired (ethernet) connections are very reliable.

If you want or need a wired connection, there are small USB adapters for wired (ethernet) connection for laptops. If it is a desktop/tower model, you can easily insert a cheap ethernet card.

hi sudodus, there wasn't any high voltage incident or such. 
I tried to set up a new wired connection (changed method in IPv4 to Manual) as I thought it might be worth a shot - strangely that worked. Now, I am quite confused as to what went wrong with the first one. Any thoughts/insights as to what the reason for that would be.

---

