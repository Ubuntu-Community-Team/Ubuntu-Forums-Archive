---
title: "problem connecting xbox to internet"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by chrisr6 on 2008-12-15
I am sort of new to ubuntu 8.10 i do have a little no how. my problem is that when i had my network wired directly to my dsl router i could connect to xbox live without a problem but now since i connected a wireless router to my computer my xbox connects to my network but will not connect to the Internet my setup that i have now is my xbox is connected to my computer via crossover cable and my computer is connected to the Internet via wireless adapter. The Internet works on my computer just not on my xbox. Any help would be appreciated.


Here is my ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:10:b5:70:b1:85  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::210:b5ff:fe70:b185/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47670 (47.6 KB)  TX bytes:123310 (123.3 KB)
          Interrupt:5 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17600 (17.6 KB)  TX bytes:17600 (17.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:df:2e:fb:16  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:dfff:fe2e:fb16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5315193 (5.3 MB)  TX bytes:743405 (743.4 KB)

---

### Post by ThaddeusW on 2008-12-16
Ok you need to first make sure the xbox is on fact properly connected to the computer. Most every switch and Ethernet card made today and for some time is already capable of Auto-MDIX. That means you don't need a crossover cable. Make sure the connection is up.

Now you need to bridge the wireless network adapter to the ethernet adapter. Bridging means your not routing but making two separate networks work as one. Your pc will just pass the ethernet frames between the two networks. It does not care what protocol is used (yes your pc will still connect to the internet just fine). I am going to be lazy and copypasta [>>this post<<]("http://www.criticalsecurity.net/index.php?showtopic=29894") here as a guide:

> Bridging requires the bridge-utils package, a standard component of every modern Linux distribution that provides the command-line utility brctl.

To create a bridge between your network adapters, begin by taking both adapters offline with the ifdown command. In our example eth0/eth1 setup, run sudo ifdown eth0 and sudo ifdown eth1 from the command line.

Next, create the bridge with sudo brctl addbr bridge0. The addbr command creates a new "virtual" network adapter named bridge0. You then connect your real network adapters to the bridge with addif: sudo brctl addif bridge0 eth0 adds the first adapter, and sudo brctl addif bridge0 eth1 adds the second.

Once configured, you activate the bridge0 virtual adapter just as you would a normal, physical Ethernet card. You can assign it a static IP address with a command like sudo ifconfig bridge0 192.168.1.100 netmask 255.255.255.0, or tell it to retrieve its configuration via DHCP with sudo dhclient bridge0.

You can then attach as many computers, hub, switches, and other devices as you want through the machine's Ethernet port, and they will all be able to see and communicate with each other. On the downside, if you have a lot of traffic, your computer will spend some extra energy passing all of those Ethernet frames back and forth across the two adapters.  

I have yet to try it but it should work! In fact I will play with this myself right now. Let me know if you get this to work. You could even put a switch there and hook more stuff to the wireless.

---

### Post by chrisr6 on 2008-12-17
chris@RIEMENAPP-PC_Network:~$ sudo ifdown eth0
sudo: unable to resolve host RIEMENAPP-PC_Network
ifdown: interface eth0 not configured
chris@RIEMENAPP-PC_Network:~$ sudo ifdown eth1
sudo: unable to resolve host RIEMENAPP-PC_Network
ifdown: interface eth1 not configured
chris@RIEMENAPP-PC_Network:~$ sudo ifdown wlan0
sudo: unable to resolve host RIEMENAPP-PC_Network
Ignoring unknown interface wlan0=wlan0.
chris@RIEMENAPP-PC_Network:~$ 


this is what i get when i try to shutdown my networks

---

### Post by pmcchapman on 2008-12-29
I have just sorted this for my set up, which appears to be pretty much like yours. However, I used Firestarter rather than manually set up the network bridge. Hope this helps:

[http://ubuntuforums.org/showthread.php?p=6458974#post6458974]("http://ubuntuforums.org/showthread.php?p=6458974#post6458974")

---

