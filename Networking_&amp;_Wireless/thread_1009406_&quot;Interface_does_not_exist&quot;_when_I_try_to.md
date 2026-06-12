---
title: "&quot;Interface does not exist&quot; when I try to configure my ethernet connection."
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by ratdog on 2008-12-12
Hello, I'm having problems with my wired network.
I'm using Hardy 64 bit wired to a laptop with Intrepid 32 bit.

I've been using firestarter on the laptop to share its internet connection with the desktop running Hardy 64 for a couple of weeks now.  I initially got the connection all set up and have just left the laptop on since then.  I finally shut them both off yesterday and since rebooting have not been able to reconnect them.  

I have the laptop setup to automatically connect to the wired network, but it doesn't now.  When I ask it to connect, it just says "Requesting a network address from the wired network..."

On the desktop when I enter Network Tools, it shows 2 network devices.  The loopback interface and the Ethernet interface.  The Ethernet interface shows all the correct info that I entered when setting up the network, but when I click on "Configure", it says: "The interface does not exist.  Check that it is correctly typed and that it is correctly supported by your system."

Why would it show the Ethernet interface and then say that it does not exist??

I have not messed with any of the network settings on either computer recently.  I did try to setup Pulseaudio (unsuccessfully) on the Hardy64 desktop, but have since been able to use the network fine.

I'm kind of a Ubuntu noob, so please let me know what other info you might need to diagnose the problem.    

Thanks so much!!

---

### Post by ratdog on 2008-12-13
*bump*
Anyone have an idea?

---

### Post by superprash2003 on 2008-12-13
post output of ifconfig from the terminal.. what is you rmodem/router ip address??

---

### Post by ratdog on 2008-12-13
ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:01:52:ee  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe01:52ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:33937 (33.1 KB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:136712 (133.5 KB)  TX bytes:136712 (133.5 KB)


I'm not sure exactly what info you want about the router, but here is some info...
The routers local IP addy:192.168.1.1
Subnet mask: 255.255.255.0
DHCP starting IP addy:192.168.1.100

Need anything else?

Thanks so much

---

### Post by ratdog on 2008-12-13
regarding the above info...

The computer I'm having trouble with is just connecting to the laptop, not the router(I think?).

---

### Post by superprash2003 on 2008-12-14
so is your laptop a xp machine which has internet connection sharing enabled?? if so back in the terminal of your computer type ping 192.168.0.1 and post output here

---

### Post by ratdog on 2008-12-14
No Windows involved..

As stated in the first post, the laptop whose internet connection is being shared is running intrepid ibex.  I did do the ping though and here is the output:

$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.2 icmp_seq=2 Destination Host Unreachable
From 192.168.0.2 icmp_seq=3 Destination Host Unreachable
From 192.168.0.2 icmp_seq=4 Destination Host Unreachable
From 192.168.0.2 icmp_seq=7 Destination Host Unreachable
From 192.168.0.2 icmp_seq=8 Destination Host Unreachable
From 192.168.0.2 icmp_seq=11 Destination Host Unreachable
From 192.168.0.2 icmp_seq=12 Destination Host Unreachable
From 192.168.0.2 icmp_seq=14 Destination Host Unreachable
From 192.168.0.2 icmp_seq=15 Destination Host Unreachable
From 192.168.0.2 icmp_seq=16 Destination Host Unreachable
From 192.168.0.2 icmp_seq=17 Destination Host Unreachable
From 192.168.0.2 icmp_seq=18 Destination Host Unreachable
From 192.168.0.2 icmp_seq=19 Destination Host Unreachable


it went on pinging 192.168.0.2 200 times or so before I stopped it.

---

### Post by ratdog on 2008-12-14
I'm starting to think the problem is with the laptop with Intrepid Ibex installed on it.  I just tried to connect an old windows machine to it and when I plugged in the ethernet cable the windows machine said it was connected to a wired network.  I could not get the laptop to find the new machine however.  When I went into the network settings on the windows machine and tried to adjust the tcp/ip settings, I got an error saying "you must first enable a network card".  But the same window showed the ethernet card selected and enabled.  That is a very similar error I had when trying to connect my Ubuntu desktop to the laptop and internet.

Here's hoping this might shed some light on things.
Thanks

---

### Post by Iowan on 2008-12-16
> **ratdog said:**
> I'm starting to think the problem is with the laptop with Intrepid Ibex installed on it.  I just tried to connect an old windows machine to it and [COLOR="Red"]when I plugged in the ethernet cable[/COLOR] the windows machine said it was connected to a wired network.  ...
Here's hoping this might shed some light on things.
Thanks Direct machine-to-machine connection will require a crossover cable...

---

### Post by Naipes on 2008-12-17
I wonder if this thread is related?

[http://ubuntuforums.org/showthread.php?p=6385463#post6385463](http://ubuntuforums.org/showthread.php?p=6385463#post6385463)

---

