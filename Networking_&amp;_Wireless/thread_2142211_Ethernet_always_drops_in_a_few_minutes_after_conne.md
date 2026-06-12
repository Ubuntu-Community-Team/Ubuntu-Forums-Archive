---
title: "Ethernet always drops in a few minutes after connection established on Ubuntu 13.04"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by topmark on 2013-05-04
[SIZE=2]Hello,
I'm using Qualcomm Atheros AR8151.
I have upgraded Ubuntu 13.04 from 12.10 and after installing it the wired network got unstable.
On Ubuntu 13.04 the wired connection always lost in a few minutes after connection established. The system didn't shows any error or disconnected notification for that. The network icon on the system tray still shows normal "connected" icon. But i couldn't browse any website or ping any ip address on the internet.
And after unplug and plug in the ethernet cable again, the wired network works fine for a few more minutes and then the problem shows again.

Before upgrating to 13.04, the ethernet network works great on Ubuntu 12.04 and 12.10 (they are both 32 bit). After that I have tried erase Ubuntu and reinstall 13.04 but it didn't help.

When I run lspci i get:
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce 610M] (rev ff)
03:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)
05:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

Please help. Any information would be greatly appreciated.[/SIZE]

---

### Post by sanderj on 2013-05-05
Anything in dmesg when the network becomes unavailable?

---

### Post by topmark on 2013-05-05
> **sanderj said:**
> Anything in dmesg when the network becomes unavailable?
Thanks for your reply : )
 There is nothing dirrerent, the output just same as the connection established.

---

### Post by topmark on 2013-05-05
> **sanderj said:**
> Anything in dmesg when the network becomes unavailable?

But "ifconfig -a" shows me this:

```
eth0      Link encap:Ethernet  HWaddr 20:6a:8a:7d:4a:da  
          inet6 addr: fe80::226a:8aff:fe7d:4ada/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2962 errors:1 dropped:1538 overruns:1538 frame:1539
          TX packets:2929 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:1876123 (1.8 MB)  TX bytes:432962 (432.9 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:272475 (272.4 KB)  TX bytes:272475 (272.4 KB)


wlan0     Link encap:Ethernet  HWaddr c0:18:85:77:87:4a  
          inet6 addr: fe80::c218:85ff:fe77:874a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3733 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2216855 (2.2 MB)  TX bytes:519106 (519.1 KB)

```
The "RX dropped" counting from "eth0" part keeps growing when network becomes unavailable and before that it was 0.
I just found out these.

---

### Post by aguegu on 2013-05-13
I confirm with your problem. I got the same problem. Big headache. I have to keep a terminal pinging my netgate, replug the cable as the connection lost.

---

### Post by aguegu on 2013-05-13
I googled a new thread here about rolling back the alx driver which is functional.

[http://blog.norture.com/2013/05/how-to-fix-ubuntu-13-04-alx-ethernet-driver/](http://blog.norture.com/2013/05/how-to-fix-ubuntu-13-04-alx-ethernet-driver/)

worthing trying.;)

---

### Post by prscarp on 2013-06-05
> **topmark said:**
> [SIZE=2]Hello,
I'm using Qualcomm Atheros AR8151.
I have upgraded Ubuntu 13.04 from 12.10 and after installing it the wired network got unstable.
On Ubuntu 13.04 the wired connection always lost in a few minutes after connection established. The system didn't shows any error or disconnected notification for that. The network icon on the system tray still shows normal "connected" icon. But i couldn't browse any website or ping any ip address on the internet.
And after unplug and plug in the ethernet cable again, the wired network works fine for a few more minutes and then the problem shows again.

Before upgrating to 13.04, the ethernet network works great on Ubuntu 12.04 and 12.10 (they are both 32 bit). After that I have tried erase Ubuntu and reinstall 13.04 but it didn't help.

Please help. Any information would be greatly appreciated.[/SIZE]

I believe it has something to do with the Wi-Fi conflicting with the wired. If you click up in the network notification and uncheck "Enable Wi-Fi" the wired connection is stable again. I've also tried reinstalling the alx module from the compat-drivers package that aguegu linked to.

---

### Post by minple on 2013-06-28
Sorry. My english is not good.

I has the same problem. Network on ubuntu server 13.04 is unstable.
My ubuntu server 13.04 on hyper-v that installed on windows server 2008. its network is ethernet.
information for eth0 (ethernet network): RX packets:4286705 errors:0 dropped:287758 overruns:0 frame:0When I run a command "ifconfig" and do it again, dropped is up. 

my ubuntu server 13.04 on virtualbox that installed on ubuntu 13.04. its network is wlan (wifi). dropped is always 0
Hoping our help. Hoping Canonical know this problem.

---

### Post by rahul14 on 2014-05-06
I am running with same problem that you have.

Do you get solution of this problem ?
If yes them please replay me on here.

---

### Post by coffeecat on 2014-05-06
@rahul14, this is an old thread where the OP has not logged in since a few days after they last posted.

If you have a problem with networking, please start your own thread giving full details of the problem, what hardware you are using and which version of Ubuntu you are running.

Thread closed.

---

