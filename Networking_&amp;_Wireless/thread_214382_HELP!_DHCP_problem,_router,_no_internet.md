---
title: "HELP! DHCP problem, router, no internet"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by rayraymo on 2006-07-12
Basiclly in the installation of the OS, when it tried to set up the DHCP it said it couldn't do it. Now when I'm loggin in I can't find out how to set this up so I can get onto the internet, (Yes I'm a total Linux noob as of 10 minutes ago).

The computer is partitioned, (I'm using the XP half now, which recognised the internet and everything straight away, no setting up). And I'm using a NETGEAR dg834gt ADSL router, connected via an ethernet cable.

One thing i thought of, is my motherboards ethernet port working? Does it need drivers for linux? (ASROCK 939A8X-M)

I know it's just probably something stupid, but I thought I'd share all the information i could.

Thanks in advance. :-D

---

### Post by jenred on 2006-07-12
I've often had problems with DHCP during the install as well, but found that if I try it twice DHCP works on the second time around. 

But since you've already installed try this:

```
Login to the desktop
Go to:  System | Networking
```

Using a static IP first will help to verify that your hardware is all installed properly (provided the network is up), then try DHCP.  (Your network interface should appear in the list if it's recognized.)

The Networking interface is pretty intuitive.  There are ways to do this via the command-line as well, but try the via the desktop first.

---

### Post by mgor on 2006-07-12
try typing `iwconfig eth0` in a terminal (alt+f2, type 'gnome-terminal').
if it says something about "device not found", then your network card isn't working.

then, in that same terminal, run `lspci | grep Ethernet`. the output should be something similar to this:
```
0000:01:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
```

then search on [www.google.se/linux](www.google.se/linux) for the chip name, in this case it would be 'Intel Corporation 82801CAM' and look for page that might explain how to set it up.

---

### Post by rayraymo on 2006-07-12
Well that was the second time today I've installed the OS and both times it didnt work, (Don't fancy trying again).

I've tried to set it up through the gui, it shows something like 'eth0' and a modem link under it. I've tried adding an I.P. and checking DHCP but no pages in FF are displayed. Is there anyway like in windows where you can see if any packets have made it to the machine, (I.E. top see if i'm actually on the network?)

MGOR I'll try the network card thing in a minute and report back, I presume that the network card see's that theres a cable plugged in and so is working though if it comes up with the 'eh0' and modem bit.

Thanks

---

### Post by mips on 2006-07-12
My standard response follows:

What hardware are you using, modem/router model etc ???
How is the above hardware configured ???

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)
[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337) 

1. Please post output of **ifconfig eth0**  (Depends on your interface number)
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**
7. Please copy **entire** output of windows **ipconfig /all** command here
8. Who is your ISP and provide a web link.

---

