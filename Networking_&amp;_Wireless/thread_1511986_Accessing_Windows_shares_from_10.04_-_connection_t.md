---
title: "Accessing Windows shares from 10.04 - connection timeout"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by Cenci-Thomas on 2010-06-17
Hello. Sorry if someone has asked this already, I did search the forums but didn't come across anything exactly like what I'm dealing with here. I'm pretty new to Linux, running a new install of 10.04 on a Gateway nv53 laptop (dual booting with Win 7), accessing a desktop running WinXP SP3 with several shares on it. About half the time I can access the shares. The other half (and especially if I'm copying large files, which is often) the connection will time out halfway through the job with the error:

Could not display "smb://server/share/".
Error: Connection timed out
Please select another viewer and try again.

or sometimes when I try to open a share I'll get

Unable to mount location
Failed to retrieve share list from server.

Haven't had any trouble accessing the Internet. Restarting Nautilus doesn't help. Restarting the wireless connection *sometimes* helps but not always, and lately it's been helping less and less. I tried shutting off DHCP at the router and manually configuring my IP addresses but no change. I don't have trouble when I boot to the Win 7 partition from the laptop. Here are the [ifconfig] and [lspci | grep Wireless] outputs if that helps--

ifconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:26:2d:6a:3a:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:a6:cf:39  
          inet addr:10.35.54.4  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::721a:4ff:fea6:cf39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1082 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1133498 (1.1 MB)  TX bytes:204246 (204.2 KB)

lspci | grep Wireless:
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)


Does anyone have any ideas? I really don't want to have to go back to Windows but with the number & size of files I have to copy up & down for my work, this is a dealbreaker if I can't get this fixed. :( Thanks in advance.

---

### Post by Cenci-Thomas on 2010-06-17
FYI: Changed up my search parameters and found this:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Won't have a chance to test until tonight though.

---

### Post by Cenci-Thomas on 2010-06-18
HAH. Fixed. Found dmizer's howto here: [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534), set up a permanent mount (or 4) and voila. THANK YOU DMIZER.

---

### Post by GerMulvey on 2010-07-12
Same problem for me. I used connect to server in the live cd which worked fine until I rebooted. This is something that should work from the get go.
Glad to see you got it working but for me why so much work for as I say something that should work!

---

