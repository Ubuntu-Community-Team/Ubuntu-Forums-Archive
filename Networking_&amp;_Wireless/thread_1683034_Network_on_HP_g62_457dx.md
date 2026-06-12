---
title: "Network on HP g62 457dx"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by AlexBaranosky on 2011-02-06
Hi 

I just got  a new HP G62 457dx and when I turn it on, it is not recognizing my wireless network, which all my other computers find fine.  What do I need to do to get it to see the network?

iwconfig:

```
eth0      Link encap:Ethernet  HWaddr 98:4b:e1:93:90:8f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:32 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

```

ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 98:4b:e1:93:90:8f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:32 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:3f:f5:7c:4e  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:3fff:fef5:7c4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:519776 (519.7 KB)  TX bytes:150168 (150.1 KB)

```

Thanks for the help,
Alex

---

### Post by arjuntank on 2011-02-06
okay, it looks like you are already connected to a wireless network. what does the network manager show you?

---

### Post by AlexBaranosky on 2011-02-07
Hmmm... I may have mistakenly run ifconfig/iwconfig when the USB  wireless adapter was plugged in (so I could access the net, but I don't want to NEED to use the USB adapter...)...  I'll redo those numbers when I have no net access.

---

### Post by AlexBaranosky on 2011-02-07
Here are the results of running them with the usb network adapter removed.

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 98:4b:e1:93:90:8f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:32 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```

Thanks for all your help!

---

### Post by AlexBaranosky on 2011-02-07
bump.

Still could use some help with this :)

Thanks!

---

### Post by AlexBaranosky on 2011-02-08
No one can help?

---

### Post by AlexBaranosky on 2011-02-08
bump

---

### Post by moaoci on 2011-02-08
Open a terminal and type
lspci | grep -i net

Post the results... someone with the same hardware will take the lead...

---

### Post by AlexBaranosky on 2011-02-08
~$ lspci | grep -i net
02:00.0 Network controller: RaLink Device 5390
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


Thanks :)

---

### Post by moaoci on 2011-02-08
Your solution might be here [http://ubuntuforums.org/showthread.php?p=10240071#post10240071]("http://ubuntuforums.org/showthread.php?t=1645716") . That's all I can do for you, since I don't have your hardware.

Good luck...

---

### Post by AlexBaranosky on 2011-02-10
Thanks!  It worked :)

---

