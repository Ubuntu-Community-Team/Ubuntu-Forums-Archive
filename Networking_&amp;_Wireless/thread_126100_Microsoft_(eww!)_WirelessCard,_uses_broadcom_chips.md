---
title: "Microsoft (eww!) WirelessCard, uses broadcom chipset - but no &quot;bcmwl5.inf&quot; drivers??"
date: 2006-02-05
forum: Networking &amp; Wireless
---

### Post by Jiketsu on 2006-02-05
Hello hello :)

I tried to find this on my own and I found a pretty good prospect:

[http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

Unfortunately the drivers that came with my pci card do not contain "bcmwl5.inf" as required to fulfill the instructions. I am certain its because my card was resold by the evil corporation of death. What I do have is:

MN110-50.sys
MN130-50.sys
MN520-51.sys
MSWNDS50.sys
MSWUSB51.sys
MN120-50.sys
MN130-51.sys
mn720-50.sys
MSWNDS51.sys
MN120-51.sys
MN510-51.sys
MSWIOC.vxd
MSWUSB50.sys

Of course, I have to be an idiot to actually buy a microsoft product, but it wasn't my fault.. I promise. I am quite certain it is using Broadcom, because if I view it with the Device Manager, it says so. So I guess I'll take it's word for it!

**So now what I really need to know is, if someone would kindly provide me with some bcmwl5.inf, or bcmwl5a.inf, bcmwl5.sys files, would I be good to go if I used them with the instructions in the above thread? Or has the card been tainted by the touch of microsoft and I have to find another way?**

Your help is certainly appreciated. I want to make a direct wireless connection to my laptop (which I think is called adhoc?) to share internet without a router. I can do it using Windoze, but of course with windoze I am only allowed to share internet to only one other connection... so now I aim to have my linux box setup to act as a router of sorts.

**If I cant use the bcmwl5.inf drivers if provided to me, then does any one know which of the drivers I have been given I should use? Anyone had any success with this card?**
[B]
Thank you kindly for the help :)[/B]

---

### Post by Lambert on 2006-02-05
What's the model number of the card?

What's the output of 

```
sudo lspci -v
```
and
```
sudo lspci -n
```

match up the pciid code you get with the list on the ndiswrapper wiki.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

I don't believe any of the files you listed are the driver file you need.

If you need help with ndiswrapper, click on the wifidocs link in my signature or post back here and somebody should be able to.

---

### Post by Jiketsu on 2006-02-05
Thank you for the reply. I am not certain of the model number, sorry.

lspci -v:

0000:02:09.0 Network controller: Broadcom Corporation: Unknown device 4325 (rev 02)
        Subsystem: Microsoft Corporation: Unknown device 0004
        Flags: bus master, fast devsel, latency 64, IRQ 11
        Memory at fe1fc000 (32-bit, non-prefetchable) [size=8K]

lspci -n:
chibi@taminaru:~$ sudo lspci -n
0000:00:00.0 0600: 8086:1a30 (rev 03)
0000:00:01.0 0604: 8086:1a31 (rev 03)
0000:00:1e.0 0604: 8086:244e (rev 12)
0000:00:1f.0 0601: 8086:2440 (rev 12)
0000:00:1f.1 0101: 8086:244b (rev 12)
0000:00:1f.2 0c03: 8086:2442 (rev 12)
0000:00:1f.3 0c05: 8086:2443 (rev 12)
0000:00:1f.4 0c03: 8086:2444 (rev 12)
0000:01:00.0 0300: 10de:0110 (rev b2)
0000:02:07.0 0200: 10b7:9200 (rev 78)
0000:02:08.0 0401: 1102:0002 (rev 07)
0000:02:08.1 0980: 1102:7002 (rev 07)
**0000:02:09.0 0280: *14e4:4325* (rev 02)**
0000:02:0a.0 0200: 10b7:9055 (rev 30)

Searching for 14e4:4325 in the link you provided me I did find a listing. There are three possible installation solutions. I guess my only real concern now is installing and using ndiswrapper correctly. I will check out that link in your signature. BTW I love NIN. Probly my fav band. Good song there too. Thank you for helping me out on this.

Also, believe it or not, heh, I am going in for surgery tomorrow. I have a collapsed lung so I will  be gone for a week.. so if you reply and I don't reply back, that's the reason why. But ahh don't worry bout the surgery I'll be fine, no need to wish me luck and all that stuffs :P This is the third time so i just kinda shrug.

Time to get this card working...

---

### Post by YumaJim on 2006-02-07
Boot up Widows and so a search for "bcm*.inf'" starting in the /windows
directory. You should be able to find both the sys and inf files.

If you have the windows partition mountable (RO) you can search and copy the files from windows to your Ubuntu directory.

regards,
YumaJim

---

### Post by boomerian on 2006-02-07
I've struggled with a Broadcomm chipset in my LinkSys WMP54G v.2 adapter.
You may need the bcmwl5a.inf, if the bcmwl5.inf doesn't work. I think either will work with the bcmwl5.sys file. Check this out, for downloads:
[http://ftp.us.dell.com/network/R74092us.EXE](http://ftp.us.dell.com/network/R74092us.EXE)
(All the bcmwl5 driver files are there...)
Good luck (I still don't have internet access with Ubuntu). Keep bumping this thread until you get the answers and help you need.
Cheers,

---

### Post by Jiketsu on 2006-02-17
Okay I posted this topic awhile back. I had surgery and all that and I've finally got around to installing this card. The installation seems to be successful as far as I can tell. I have ndiswrapper and the ndisgtk installed and the card lights up and everything.

I have a new problem now though. Whenever I 'activate' the card from within that little networking utility that comes with ubuntu (or gnome) my shared internet connection to my other computer goes poof. When I 'deactivate' the internet on that second desktop pops back on.

As far as I know there are no IP conflicts at all. This is what I got:

chibi@taminaru:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:76:CB:E7:41
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::204:73ff:fecb:e741/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19632814 errors:0 dropped:0 overruns:1 frame:0
          TX packets:13566348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:356399736 (339.8 MiB)  TX bytes:899654449 (857.9 MiB)
          Interrupt:16 Base address:0xec80

eth1      Link encap:Ethernet  HWaddr 00:10:5A:D0:1B:0F
          inet addr:70.31.237.216  Bcast:70.31.237.255  Mask:255.255.255.128
          inet6 addr: fe80::210:5acf:fed0:1b0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16578010 errors:7 dropped:0 overruns:0 frame:7
          TX packets:21475655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1545921552 (1.4 GiB)  TX bytes:523532155 (499.2 MiB)
          Interrupt:19 Base address:0xe880

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3481760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3481760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:260965176 (248.8 MiB)  TX bytes:260965176 (248.8 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:0D:3A:24:87:CE
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:3aff:fe24:87ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:47750 (46.6 KiB)  TX bytes:378 (378.0 b)
          Memory:fe1fc000-fe1fdfff

recap: eth1 is dhcp to internet, eth0 is static for home network. The second computer is running windows, and its also static at 192.168.0.6

Is this some kinda masquerading issue that needs to be fixed? Everytime I reboot Ubuntu there is a little script I run to make masquerading work again:

#!/bin/sh

iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE;
echo 1 > /proc/sys/net/ipv4/ip_forward;

Anyone know what the problem is? Your help is appreciated.

---

