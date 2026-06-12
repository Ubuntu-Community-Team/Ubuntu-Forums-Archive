---
title: "No internet access for either machine when sharing WiFi connection via ethernet"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by oarion7 on 2013-02-08
Greetings

I am running Lucid (10.04) on a laptop and am trying to share my WiFi connection to a Windows machine via the ethernet cable connecting the two machines. I have created a special wired connection in Gnome Network Manager and under the IPv4 Settings for this connection I have selected "Shared to other computers"

From the Ubuntu laptop I am **able** to simultaneously connect to both the WiFi access point and the special ethernet connection I created. However, when I do this, the source (Windows) machine receives "Limited or no activity" and the **Ubuntu machine has no working internet access** (i.e. via browser or ping) unless I disconnect the ethernet connection, at which point the WiFi works again, instantly.

Is my laptop somehow incorrectly prioritizing the devices? On my system, for some reason, the ethernet is represented by "eth0" and the wireless is represented by "eth1" and I wonder if this is confusing one of the little dinosaurs that live inside the machine that do all the dirty work.

Here is the readout for "route" in the terminal, which I have read about but remains a bit unclear for me .

With WiFi connected only:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         home            0.0.0.0         UG    0      0        0 eth1
```


With WiFi and shared wired connection both connected and no internet access available:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      *               255.255.255.0   U     1      0        0 eth0
192.168.1.0     *               255.255.255.0   U     2      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.254   0.0.0.0         UG    0      0        0 eth1

```

Thanks in advance to anyone who can assist!

---

### Post by ahallubuntu on 2013-02-08
~

---

### Post by oarion7 on 2013-02-08
> **ahallubuntu said:**
> Shouldn't it be the other way around?  That is, in your WiFi connection, in Network Manager config, tell it to "share with other computers?"

I don't think so... Followed the instructions [here]("http://askubuntu.com/questions/215576/how-to-share-wifi-through-ethernet-cable-to-windows-pc") as elsewhere.

> **ahallubuntu said:**
> 
However, you may need a switch between the laptop and the router.  I'm told that modern network cards autosense the connection and can flip transmit/receive lines automatically...but this has never worked for me.

Would the adding of a switch resolve the issue of the Wi-Fi becoming inaccessible on the laptop (source machine) itself? If so I can give it a try.

---

### Post by oarion7 on 2013-02-08
> **oarion7 said:**
> 

[QUOTE=ahallubuntu;12499566]However, you may need a switch between the laptop and the router.  I'm told that modern network cards autosense the connection and can flip transmit/receive lines automatically...but this has never worked for me.

Would the adding of a switch resolve the issue of the Wi-Fi becoming inaccessible on the laptop (source machine) itself? If so I can give it a try.[/QUOTE]

Thanks for trying to help; I found a network switch I had laying around and this did not appear to resolve the issue. I am still of the impression that Ubuntu is trying to access the internet through the device that is supposed to be connecting it to the Windows machine instead of via the WiFi. Otherwise, why would turning the wired connection on cause the WiFi to stop working (albeit while remaining connected)? Perhaps I am wrong!

---

### Post by ahallubuntu on 2013-02-08
~

---

### Post by oarion7 on 2013-02-08
> **ahallubuntu said:**
> Have you tried setting the WiFi card as the default gateway?

[https://help.ubuntu.com/10.04/serverguide/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/network-configuration.html)

```
sudo route add default gw 10.0.0.1 eth0
```

As for the connection between computers via ethernet: you should be able to check the network between them, right?  Is the Windows machine getting an IP now after you connect via the switch?  I believe in this mode the Ubuntu machine is running a DHCP server on the ethernet card automatically when you setup sharing.  I did it in 11.04 - 10.04 shouldn't be a whole lot different.

The Windows machine is not getting an IP, even with the switch. 

Thanks, setting the default gateway to the wireless sounds like a good idea here, but I may need a little more help doing it. The exact command you gave me looks like it would actually set the default to **eth0** which is not the wireless for me but the ethernet. Anyway, whether I run that with **eth1** or **eth0** I get an error:

```
SIOCADDRT: No such process
```

Still fiddling with it.

---

### Post by ahallubuntu on 2013-02-08
~

---

### Post by oarion7 on 2013-02-08
Thanks, not sure if this is going in the right direction or not. As it is now, it looks to me as if maybe the wireless (**eth1**) is already the default gateway, considering my output of **route** is:

When shared connection is off
```
default         home            0.0.0.0         UG    0      0        0 eth1
```

When shared connection is on (and internet is inaccessible)
```
default         192.168.1.254   0.0.0.0         UG    0      0        0 eth1
```

---

### Post by ahallubuntu on 2013-02-08
~

---

### Post by oarion7 on 2013-02-08
Well thanks for your help and the clarification but I'm not making much progress. According to my own limited understanding so far, it looks to me like the output from **route** suggests that my default gateway [i]is/[i] set to the WiFi card in both cases (i.e. see my previous post).

EDIT: Do any of the "metric" values need to be altered? I tried a few different arrangements, but did not come up with anything helpful. Not sure what else to try.

---

### Post by oarion7 on 2013-02-10
Hope I might be permitted a *bump* , thanks.

---

### Post by oarion7 on 2013-02-10
Again, whenever I enable the shared "eth0" connection linking the laptop to the Desktop, the laptop loses its connection with the Internet. The WiFi on the laptop appears to be connected and operating, but the wrong interface (I presume) is being used to access the web. The web should be being accessed by "eth1" (the Wifi Card.)

So I am unable to share the connection, as when I turn on the link I have no access to the Internet at all (from either machine); also, no IP is being assigned to the recipient machine. When I disable the link at "eth0," the WiFi works fine.

As mentioned already in the thread, the **route** command displays "default" as "eth1" which is the WiFi card, so that does not appear to be the problem.

Thanks to anyone who can help

---

