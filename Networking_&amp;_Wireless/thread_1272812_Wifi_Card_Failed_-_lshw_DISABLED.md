---
title: "Wifi Card Failed - lshw DISABLED"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by Mr.Macdonald on 2009-09-22
My wifi was working fine until, my laptop's battery died and then it fails to connect to anything, or even scan.

#NOTE the lshw claims my network is disabled

Here is some useful info:
[iwconfig]("http://pastebin.com/m3243f117")
[lshw]("http://pastebin.com/m3a89462")
[lspci -knn]("http://pastebin.com/m72a9c9c4")
[ifconfig]("http://pastebin.com/m1a5a20cf")
```

# uname -a
Linux aidan-laptop 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

```

---

### Post by Iowan on 2009-09-22
Is ethernet cable connected? (**ifconfig** suggests it is...) Unplug it and try again.

---

### Post by Mr.Macdonald on 2009-09-22
the ethernet is so I can connect to the internet, it doesn't nor shouldn't affect anything. I didn't boot with it in, so why would the kernel screw itself.

---

### Post by Iowan on 2009-09-22
If you use Network Manager, it will manage only one interface at a time (giving preference, I read, to the fastest interface - which is probably eth0). To have both active, you'll (probably) need to configure one through **/etc/network/interfaces**.

---

### Post by Mr.Macdonald on 2009-09-23
/etc/network/interfaces
```
auto lo
iface lo inet loopback

```

I have had this problem before, on Ubuntu NBR (I tried it out). I finally had to resort to a full reinstall of ubuntu, while on the live cd I still had the problem, with fingers crossed I booted into a fresh install which worked.

The problem is that although I can detect the hardware, I can't use it.

iwlist wlan0 scan
```
wlan0     No scan results

```

but ...

iwconfig wlan0
```
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and ...

dmesg | grep wlan
```
[   17.744814] wlan: 0.9.4
[   42.929774] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

As in the lshw, I think that the device is disabled my hal or a similar program

---

### Post by cariboo on 2009-09-23
Iowan is right, Network Manager will not manage more than one interface at a time (at least I haven't been able to). Use wicd, it is in the repositories if you are running Jaunty, or use gnome -network-admin, or configure the network interfaces manually.

---

### Post by Mr.Macdonald on 2009-09-23
Please correct me if I am wrong, Although I will later try what you said (not at that computer now), but if my iwlist wlan0 scan won't return anything then how would I possibly be able to connect or configure my wireless.

Here is how the problem arose,

[LIST]
[*]My computer's battery died
[*]I turn it on as normal (no ethernet cable yet)
[*]I tried to connect to a unsecured wifi source, failed
[*]Confused, I looked at lshw -C network and found it DISABLED
[*]I then plugged the ethernet cable in to go to the internet so I can learn how to fix the wireless
[*]Then I ended up here
[/LIST]

My wifi hasn't gotten anymore broken since I plugged the ethernet in, so how could that cause a problem. Please read my lshw and compare it to yours (if you use wifi). I have a feeling yours won't say disabled.

And if Network Manager is configured incorrectly, then why do I have the same problem on the live CD. Yet after a fresh install, it was fixed, for the time being. Now I will admit that it is possible (and probable) that Network Manager may have disabled my wifi card, but I don't see how wicd would re-enable it. Upon an install, why would wicd enable previously disabled cards. This seems like a dangerous "feature" to program into the software, having a program scan the system and turn on hardware interfaces?!?! Dangerous for many reasons.


Thank you for your help, but rather then tell me to do something (aka install packages, reconfigure the default configuring), explain why my reasoning is wrong/right first.

Thank you

EDIT:
Tried wicd and gnome-network-tool, and only succeeded in preferring wicd. Much better feeling, but still doesn't work

---

### Post by Mr.Macdonald on 2009-09-23
Thank you for your responses, but I fixed it!!

My stupid problem was solved but a hard shutdown, battery and power supply pull.


Ahhhhhhhhhhhhhh!!!!

---

