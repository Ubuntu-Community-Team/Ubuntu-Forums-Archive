---
title: "Aircrack-ng D-Link Wireless Issue"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by deat on 2009-08-27
Hello,

I am attempting to set up Aircrack-ng for educational purposes and to gain experience with the terminal. I am using the guide from [Aircrack-ng]("http://www.aircrack-ng.org/doku.php?id=newbie_guide") I have Ubuntu 9.04 running in a virtual machine (VirtualBox). I have installed RaLink rt2570 and everything is fine other than when I try to do 'modprobe rt2570'. 
Then I get a message:
```

WARNING: All config files need .conf: /etc/modprobe.d/ralink, it will be ignored in a future release.

```
It isn't giving any fatal error, so I continued on, and I attempted to set up my computer to go into monitor mode by typing:
```

airmon-ng start rausb0

```
and it gives me the message:
```

Found 3 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
2336	NetworkManager
2342	wpa_supplicant
2486	dhclient


Interface	Chipset		Driver

```
After that, I ran iwconfig, which gave me this message:
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

then I tried running airodump-ng rausb0, and had this message:
```

Interface rausb0: 
ioctl(SIOCGIFINDEX) failed: No such device

```

The only thing I can think which would be causing this to run incorrectly would be that Ubuntu is running in a virtual machine, so the network is running as a NAT setup. Any help would be greatly appreciated!

---

### Post by deat on 2009-09-01
I forgot to mention my wireless card is a D-link Airplus G DWL-G122 (Rev.B). If anyone can help, it would be greatly appreciated.

---

