---
title: "Very slow internet in ubuntu"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by baskar007 on 2009-09-07
Hi guys,
    i am using wireless broadband card in Ubuntu.
I have just noticed after in reinstalled Ubuntu, my internet connection was very very slow compare with windows xp on the same machine ,same internet connection.

Mozilla and other browsers are does not load any website's fully.

browsers takes long time to get speed.(always transfer 40b/100b while loading after a minute browsers shows a blank page with webpage icon.) at the same connection on XP same webpage loading takes 5 to 10 sec.

i have disabled ivp6 on my Ubuntu. 

any one have idea? i am new to linux.

---

### Post by yeats on 2009-09-07
What are your machine's specs?

If you can, go to a terminal (Applications -> Accessories -> Terminal) and use ping to test your connection.  Ping your internet gateway (assuming your gateway's IP is 192.168.1.1 in this example), then ping a website by name, then by IP:

```
ping *192.168.1.1* 
ping ubuntuforums.org
ping 91.189.94.12
```

Ctrl-C will stop the pinging, but let it run for a bit to see the speeds (e.g., "time=117 ms") and whether there are dropped packets (any breaks in the sequence of numbers in the "icmp_seq=1" field).  Post back your results within CODE tags.

You could also experiment with a direct Ethernet connection to the network...

---

### Post by jward3010 on 2009-09-07
Did you hit the problems after uninstalling IPv6? 

Also run the command:
```
sudo lspci
```
and paste into CODE tags what appeared.

---

### Post by baskar007 on 2009-09-07
> **chrissharp123 said:**
> What are your machine's specs?

If you can, go to a terminal (Applications -> Accessories -> Terminal) and use ping to test your connection.  Ping your internet gateway (assuming your gateway's IP is 192.168.1.1 in this example), then ping a website by name, then by IP:

```
ping *192.168.1.1* 
ping ubuntuforums.org
ping 91.189.94.12
```

Ctrl-C will stop the pinging, but let it run for a bit to see the speeds (e.g., "time=117 ms") and whether there are dropped packets (any breaks in the sequence of numbers in the "icmp_seq=1" field).  Post back your results within CODE tags.

You could also experiment with a direct Ethernet connection to the network...

_Here ping details:_

baskar@Baskar:~$ ping softwareroxer.blogspot.com
PING blogspot.l.google.com (74.125.93.191) 56(84) bytes of data.
64 bytes from qw-in-f191.google.com (74.125.93.191): icmp_seq=1 ttl=42 time=741 ms
64 bytes from qw-in-f191.google.com (74.125.93.191): icmp_seq=3 ttl=42 time=880 ms
64 bytes from qw-in-f191.google.com (74.125.93.191): icmp_seq=2 ttl=42 time=1961 ms
64 bytes from qw-in-f191.google.com (74.125.93.191): icmp_seq=4 ttl=42 time=852 ms
64 bytes from qw-in-f191.google.com (74.125.93.191): icmp_seq=5 ttl=42 time=740 ms
64 bytes from qw-in-f191.google.com (74.125.93.191): icmp_seq=6 ttl=42 time=637 ms
64 bytes from qw-in-f191.google.com (74.125.93.191): icmp_seq=7 ttl=42 time=639 ms
64 bytes from qw-in-f191.google.com (74.125.93.191): icmp_seq=8 ttl=42 time=779 ms
^Z
[3]+  Stopped                 ping softwareroxer.blogspot.com

this ping are worked when browsers or other internet programs not in use.
(browsing and pinging on the same time does not work for me. It will gives 'ping unknown host google.com')

mozilla always said connection intrepated.

any solution?  :(
[thanks in advance]

---

### Post by baskar007 on 2009-09-07
> **jward3010 said:**
> Did you hit the problems after uninstalling IPv6? 

Also run the command:
```
sudo lspci
```
and paste into CODE tags what appeared.

here PCI details:
baskar@Baskar:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)


please help me i was so disgraced by this problem/

---

### Post by baskar007 on 2009-09-07
In ubuntu 9.04
My download speed is 1kb to 9kb unstable speed (always change in speed) 
My upload speed is 20kb stable speed (speed does not change untill the upload task is complete)

Is this normal???????:confused:

---

### Post by jward3010 on 2009-09-07
The Realtek is most likely your wireless device. Try:
```
iwlist scanning
```
and paste output here.

Also go to System menu > Administration > Hardware Drivers, and see if there's any drivers or even firmware to get.

When you're testing this are you far from the Access Point that you're wirelessly connected to. If so, get as close as you can, not inches away, preferably 5 ft. would be perfect with nothing blocking signal (walls, coat stands, groups of people, metal girders, the postman, a mountain etc. etc.)

---

### Post by baskar007 on 2009-09-08
> **jward3010 said:**
> The Realtek is most likely your wireless device. Try:
```
iwlist scanning
```
and paste output here.

Also go to System menu > Administration > Hardware Drivers, and see if there's any drivers or even firmware to get.

When you're testing this are you far from the Access Point that you're wirelessly connected to. If so, get as close as you can, not inches away, preferably 5 ft. would be perfect with nothing blocking signal (walls, coat stands, groups of people, metal girders, the postman, a mountain etc. etc.)

baskar@Baskar:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.


I have no driver software installed for this modem in ubuntu. i did only setting up my internet conection setting. there is no problem for connect to isp but problem is slow speed.
i got slow internet in only ubuntu not in windows.  
and my area signal strength is very good there is no chance for signal blocking.

I hardwaresection i get "No proprietary drivers are in use on this system."

my system configure is:
intel P4 2.4GHz
180Gb sata
1Gb Ram
chipset : 845intel

Note:
 i was recently uninstalled deamon or somthing like that (i forget its name).

---

### Post by baskar007 on 2009-09-09
does no one have a solution or simple workouts????????:lolflag:

---

### Post by jward3010 on 2009-09-09
> **baskar007 said:**
> Note:
 i was recently uninstalled deamon or somthing like that (i forget its name).

Go into Synaptic Package Manager and find the History section in one of the menus (I can never remember exactly where it is) and see if you can find what daemon you uninstalled.

---

