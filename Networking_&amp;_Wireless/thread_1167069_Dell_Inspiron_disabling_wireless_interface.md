---
title: "Dell Inspiron: disabling wireless interface"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by jeenuv on 2009-05-22
Hi,

I switched my network manager to wicd. Wicd, unfortunately, doesn't have a GUI option to shut an interface down, in the event that I don't want it powered up. But network manager used to have this feature, and the interface LED goes off indicating a power down (?).

Now, Inspiron doesn't have a power off switch for the wireless interface alone. I'm looking for a way to shut the interface down from the command line. I tried "sudo ifdown wlan0" but that throws out the message:

ifdown: interface wlan0 not configured

While my connection is active, ifconfig command does show wlan0 in output.

Please could somebody tell me how to bring the interface down?

Thanks
:J

---

### Post by superprash2003 on 2009-05-22
if its not on ifconfig output , its down

---

### Post by jeenuv on 2009-05-22
I said ifconfig **does** show wlan0 in its output.

```

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:4e:f0:b9  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe4e:f0b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2324474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2915377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1271176406 (1.2 GB)  TX bytes:2561959300 (2.5 GB)

```

---

### Post by superprash2003 on 2009-05-23
post contents of the /etc/netwokr/interfaces file

---

### Post by jeenuv on 2009-05-23
```

auto lo
iface lo inet loopback

```

I guess there isn't an entry for wlan0. Probably wicd configures and manages it?

Let me know if I can post any more details

---

### Post by superprash2003 on 2009-05-24
ok , backup your  /etc/network/interfaces file and add the following lines to the interfaces file

[B]auto wlan0
iface wlan0 inet dhcp[/B]

now save the file , and type **sudo /etc/init.d/networking restart**. then type **sudo ifdown wlan0**

---

### Post by jeenuv on 2009-05-24
OK, edited the file. And now I get this when I restart networking:
```

 * Reconfiguring network interfaces...
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:19:d2:4e:f0:b9
Sending on   LPF/wlan0/00:19:d2:4e:f0:b9
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
Terminated
Failed to bring up wlan0.
   ...done.

```

---

### Post by superprash2003 on 2009-05-26
could you post the contents of the /etc/network/interfaces file again.. it talks about wmaster0 but you dont have a wmaster0

---

### Post by jeenuv on 2009-05-26
It's the same that I had posted. And as you said, I don't have that entry you mentioned.

---

### Post by t0mppa on 2009-05-26
There are quite a few drivers that create another "version" of the interface to handle some issues with wireless. Wmaster0 is referred to as the "internal master device" and it's used by the mac80211 module.

For instance, ath5k and b43 drivers have wlan0 be the device relevant to the user and then wmaster0 is this internal one that's sometimes hidden from the user, since it's just there for the OS's internal workings and doesn't need user input. Think of it a bit like a symbolic link to the real thing. With ath_pci it's a pair of ath0 and wifi0 (doesn't use mac80211, so it's a different name here) and I'm sure there are other pairs as well out there. And yes, the number can be anything, but you get the idea.

Just to point out that it's nothing particularly troublesome and you should just let it do its own thing. The output you see is more of a byproduct of your original problem than any real issue that you should worry about.

---

### Post by jeenuv on 2009-05-27
OK. Any thoughts on my original question: how to bring it down from the command-line?

---

### Post by t0mppa on 2009-05-27
Well, I just use 'sudo ifconfig <interface> down' and 'sudo ifconfig <interface> up'. The only time I had some trouble with them was when my connection had somehow lost the default route in the middle of some other work and it kept saying interface isn't configured, before I fixed the route.

But other than that, don't have any troubleshooting experience with the terminal, since it seems to just work. Maybe you could post in [this thread]("http://ubuntuforums.org/showthread.php?t=571188") and they'd know better how to help you out.

---

