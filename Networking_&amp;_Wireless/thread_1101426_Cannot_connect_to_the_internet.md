---
title: "Cannot connect to the internet"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by mikios on 2009-03-20
Hello

Im a newbie in linux. I installed Ubuntu 8.10 3 days ago in my flash drive. All the procedure went fine. I just cannot connect on the internet.

I am using an ethernet pci card and a DSL router. Ubuntu

I have read in many forums about the changes i have to make to "Auto eth0" but it looks like i dont have the permission to do it.I also write this code to the terminal (its all what i read from forums)

ubuntu@ubuntu: (i write)sudo bash
roo@ubuntu:~# (Q.is this means i am logged as a admin?)
(so then i write)
roo@ubuntu:~# /etc/network/interfaces
(and i get)
bash:/etc/network/interfaces : permission denied

*Just to mention that on the top right of my desktop i can see  the icon that my network is enable.

Please help...thanks

---

### Post by tenmoi on 2009-03-20
system/admistration/network and check the box next to your card. Then select your connection -> properties -> dhcp from the dropdown box.

---

### Post by Iowan on 2009-03-20
> **mikios said:**
> ubuntu@ubuntu: (i write)sudo bash
roo@ubuntu:~# (Q.is this means i am logged as a admin?)
(so then i write)
roo@ubuntu:~# /etc/network/interfaces
(and i get)
bash:/etc/network/interfaces : permission denied
A couple of things to point you in a slightly different direction: ```
roo@ubuntu:~# /etc/network/interfaces
```This will try to execute the file. You *probably* want to edit it.  Try one of these:```
sudo nano /etc/network/interfaces
```
```
gksu gedit /etc/network/interfaces
```

---

### Post by mikios on 2009-03-20
> **tenmoi said:**
> system/admistration/network and check the box next to your card. Then select your connection -> properties -> dhcp from the dropdown box.

Thanx a lot for the reply

I did what you said (well i hope i did).
1. In the Network device Window i choose the ethernet interface. When i close the window and re-open it its going back to loopback interface (lo).is that positive?

2. At the network connection window i see only one connection and that is *Auto eth0* which has a "never" beside. in the edit menu i see 
MAC address 00:50:B&#915;:AB:F9:41
MTU : Automatic
and in the IPv4 settings the method is Automatic (DHCP)

I also created an new account as a administrator but in the terminal i get the same permission denied. 

Thanx again for your reply

---

### Post by mikios on 2009-03-20
> **Iowan said:**
> A couple of things to point you in a slightly different direction: ```
roo@ubuntu:~# /etc/network/interfaces
```This will try to execute the file. You *probably* want to edit it.  Try one of these:```
sudo nano /etc/network/interfaces
```
```
gksu gedit /etc/network/interfaces
```

Thanx a lot Iowan i 'll check it out and text you back

---

### Post by mikios on 2009-03-20
> **mikios said:**
> Thanx a lot Iowan i 'll check it out and text you back

Well i try the second command [gksu gedit /etc/network/interfaces] and the editor opens with these two lines 

               auto lo
               iface lo inet loopback

According to other threads i continue forming this
                
                allow hot-plug eth0
                iface eth0 inet static
                address ...
                netmask ...
                broadcast ...
                gateway ...
and then i save the file. try to connect but nothing happens
I know this issue has solved years ago but it looks like im doing s'thing wrong here 

please help..
Thanx

---

### Post by tenmoi on 2009-03-20
If you do not know about TCP/IP addressing I advise you do this:
Remove: allow hot-plug eth0
iface eth0 inet static
address ...
netmask ...
broadcast ...
gateway ...

Then add this line: iface eth0 inet dhcp
Then:
  sudo /etc/init.d/networking restart
if this wont work, post result of ifconfig -a and your NIC's name and model.

---

### Post by ugm6hr on 2009-03-21
I would suggest you confirm basic details, just to ensure you are not barking up the wrong tree.

It appears you are trying to use a wired ethernet to connect to a router with static IP.

You mention the Network Manager icon that confirms your card is enabled; not really sure what this means.

A later comment mentions DHCP; does your router use DHCP or static ip?

---

### Post by dmurat on 2009-03-21
i am also having a very similar problem with realtek RTL8111/8168B (the driver being loaded wrongly bug) and cant seem to fix it for a month...
i installed 9.04 alpha but they still dont seem to solve this issue. i want to use ubuntu instead of fedora so..please..need help =)

thanks

---

### Post by mikios on 2009-03-21
Hi again..and really thanx for the interest

So..in gedit i remove what you told me to and i wrote:
  

> iface eth0 inet dhcp and then save the file.

Then i go to the terminal and wrote:
> sudo /etc/init.d/networking restart

It say something about reconfiguring network. The result of ifconfig is:

> root@ubuntu:~# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)


The lspci gives me this:
> oot@ubuntu:~# lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:0b.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
02:0e.0 USB Controller: NEC Corporation USB (rev 41)
02:0e.1 USB Controller: NEC Corporation USB (rev 41)
02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
root@ubuntu:~# 
so it sees my NIC.

Any advice?

---

### Post by linuxisevolution on 2009-03-21
> **mikios said:**
> Hi again..and really thanx for the interest

So..in gedit i remove what you told me to and i wrote:
  

 and then save the file.

Then i go to the terminal and wrote:


It say something about reconfiguring network. The result of ifconfig is:



The lspci gives me this:

so it sees my NIC.

Any advice?

Can you get connected yet? It's very odd your having this much trouble, but are you connected with a dsl connection? Of so, connect the computer directly to the modem and type 192.168.1.1 in the browser and then configure your modem to auto connect using the password and username provided by your isp.

---

### Post by Death_DealerV69 on 2009-03-21
i keep seeing everywhere to go to system-admin-network but i dont have that option.
i have network tools.
i can't connect to the internet using wireless.
btw i just installed it yesterday and am completely new to this.
i got all the updates that i could through the update manager.

---

### Post by mikios on 2009-03-21
> **ugm6hr said:**
> I would suggest you confirm basic details, just to ensure you are not barking up the wrong tree.

It appears you are trying to use a wired ethernet to connect to a router with static IP.

You mention the Network Manager icon that confirms your card is enabled; not really sure what this means.

A later comment mentions DHCP; does your router use DHCP or static ip?

Yes thats right...wired ethernet through a router.
When i go to the page of the router, in the LAN tab it gives me the IP add, the subnet and also say  [HTML]DHCP Server : enabled[/HTML]

At the WAN tab it gives me all the address(IP, Gateway,SUB,DNS) and also say that status is connected and the connection type is PPPoe.

As for the icon i meant the same one that appears on Windows to show you that you ethernet is plugged. Its on my right top of my desktop and look like its plugged.

I hope these informations was clear enough...

Thank you for your time

---

### Post by ugm6hr on 2009-03-21
OK.

It sounds like your computer has acquired an IP from the router.

Confirm with:
```
ifconfig
ping -c 3 www.opendns.com
ping -c 3 208.67.219.101
```

Give the output of these commands.

---

### Post by tenmoi on 2009-03-22
> **mikios said:**
> Yes thats right...wired ethernet through a router.
When i go to the page of the router, in the LAN tab it gives me the IP add, the subnet and also say  [HTML]DHCP Server : enabled[/HTML]

At the WAN tab it gives me all the address(IP, Gateway,SUB,DNS) and also say that status is connected and the connection type is PPPoe.

As for the icon i meant the same one that appears on Windows to show you that you ethernet is plugged. Its on my right top of my desktop and look like its plugged.

I hope these informations was clear enough...

Thank you for your time

Mikios. I do not want to repeat my self so you can go to this thread [http://ubuntuforums.org/showthread.php?t=1100819&page=2](http://ubuntuforums.org/showthread.php?t=1100819&page=2), post #12 and see if it can help.

---

### Post by mikios on 2009-03-22
OK **[SIZE="3"]ugm6hr[/SIZE]**

The ifconfig command fives me this:

> root@ubuntu:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:bf:a8:f9:41  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1240 (1.2 KB)  TX bytes:3327 (3.3 KB)
          Interrupt:23 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

ping -c 3 [www.opendns.com](www.opendns.com) gives me "unknown host"
ping -c 3 208.67.219.101 give  me this:

> root@ubuntu:~# ping -c 3 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.
64 bytes from 208.67.219.101: icmp_seq=1 ttl=50 time=237 ms
64 bytes from 208.67.219.101: icmp_seq=2 ttl=50 time=238 ms
64 bytes from 208.67.219.101: icmp_seq=3 ttl=50 time=228 ms

--- 208.67.219.101 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2006ms
rtt min/avg/max/mdev = 228.491/234.872/238.564/4.548 ms

Thanx again...

---

### Post by ugm6hr on 2009-03-22
This is a DNS resolution issue.

Try using the opendns servers:
[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

Or this might be better:
[http://208.67.219.101/start/device/ubuntu](http://208.67.219.101/start/device/ubuntu)

---

### Post by mikios on 2009-03-22
Ok this is weird but im happy to say that this reply is from my Ubuntu.

The problem is that i dont know exactly what i did.

I took the first step of [https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu) twice without any success. Came back to windows and i said i give it one more try. So i went in ubuntu open firefox and voila!!! What i noticed later was that another Auto eth0 was added to the Network connection window but with different settings. If you could give me some details about this i would be greatfull cause i would like to help some1 in the future like you did to me.

I also did the A-B-D-C steps of what TENMOI told about /lib/modules for 2 8*.ko files (cause i wasnt sure which one was the right) but i was getting the msg "ignoring unknown interface eth0=eth0"
I hope i dont have any probs in the future.

I really want to thank you guys. I really do.

Its time for me to explore my new LINUX!!!:D:D:D:D
Have  a nice time

---

