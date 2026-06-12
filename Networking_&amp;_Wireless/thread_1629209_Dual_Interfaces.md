---
title: "Dual Interfaces"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by version7x on 2010-11-23
Ok...

I know I'm close, but can't seem to find the exact solution.  I've got a ethernet port and wifi on my netbook.  Our company's wired network is EXTREMELY locked down and I can't get outside from it except to approved sites.  

We also, however have wifi which is much more "flexible" with its security (very little security).  I'd like my default gw to be the wireless interface as I can get anywhere outside (like ubuntuforums ) from there.

I've edited my /etc/network/interfaces file to configure the eth interface via dhcp.

```
auto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp
```

I know that the interface is being configured without this addition to the interfaces file, but I thought I'd see if that made a difference.  NOPE!

I've also went into NetworkManager, under IPv4 Settings -> routes and checked the "use this connection only for resources on this network"

When the wlan device is disconnected, it works.  With wirless activated, it doesn't work.

I can provide the routing information, but that looks correct for each.  What am I missing?

Thanks in advance!
-M

---

### Post by version7x on 2010-11-23
Ok,

I think I've got it.  Please correct me if I'm wrong!

I found that I could manually add the route on the command line:

```
sudo route add -net 192.168.0.0 netmask 255.255.0.0 dev eth2
```

that seemed to work, but I wanted to add it permanently, so I now have the following for /etc/network/interfaces:

```
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp
     up route add -net 192.168.0.0/16 dev eth2
```


It seems to work after network restarts.  Any pointers or do I have it correct?


Thanks!

---

### Post by cybergnome on 2010-11-23
I suggest you ask your IT people for the solution.  This is not the place to discuss strategies that can be employed in breaching corporate intranets, regardless of your intentions.

---

### Post by version7x on 2010-11-24
> **cybergnome said:**
> I suggest you ask your IT people for the solution.  This is not the place to discuss strategies that can be employed in breaching corporate intranets, regardless of your intentions.

Thanks for the suggestion, but I'm not working on breaching anything... I'm attempting to set a standard for obtaining updates.  Up until myself, we've been a windows only shop.  And they have no clue.

:)

---

### Post by version7x on 2010-11-24
Also, I've noticed after reboots, that network manager no longer shows the interface.  This is preferrable for a server, in my opinion, but, I'd like the ability to have network manager fully informed in a desktop setting.

SO, I've reverted to the original interfaces file and added the following in network manager:

Under the wired connections -> IPv4 -> Routes

```

Address        192.168.0.0       
Netmask        255.255.0.0         
Gateway     
Cost           16
```

Seems to bridge the networks perfectly for those who need to legitimately access two networks.

---

### Post by grahammechanical on 2010-11-24
I am confused. What do you want to be your default network connection. Wired or Wireless? 

I have two ethernet ports and wireless. I use network manager to set my wireless connection to connect automatically and I make sure that both ethernet connections are not set to connect automatically. And wireless becomes my default connection even though I have an ethernet cable connected as well. I can make one of the ethernet connections the default connection in the same way if I like. Is the answer to your problem this simple? 

Regards.

---

### Post by version7x on 2010-11-25
> **grahammechanical said:**
> I am confused. What do you want to be your default network connection. Wired or Wireless? 

I have two ethernet ports and wireless. I use network manager to set my wireless connection to connect automatically and I make sure that both ethernet connections are not set to connect automatically. And wireless becomes my default connection even though I have an ethernet cable connected as well. I can make one of the ethernet connections the default connection in the same way if I like. Is the answer to your problem this simple? 

Regards.

I was trying to be able to hit both networks automatically, using my wired connection for all internal traffic and my wireless for external web connections like ubuntu updates.

Before I posted, I verified that both interfaces were configured correctly, automatically, but only one worked at a time.  I knew how to add a route, but didn't know the best way to make it persistent.

My first discovery was how to manually configure it in /etc/network/interfaces.  It worked, but I wanted to be able to do it from the desktop since I had gnome up and running.  I finally found out how to set up Network Manager to do the dirty deed for me.

All is well now!  Works like a champ!

I just wanted to make sure there wasn't a better way to do the same thing.

Thanks!

---

