---
title: "Belkin USB No internet"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by charliko on 2009-05-13
I have been reading and reading.  Here are some commands I ran.  I believe the reader will conclude that I have a connection with my wireless access point, but cannot get to internet.  Hopefully, someone will give some guidance or suggestions.  Belkin usb rtl8187 is being used.

Here are the results:

           char@char-desktop:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr 00:18:f3:a0:63:13   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:23 Base address:0x6000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 wlan0     Link encap:Ethernet  HWaddr 00:1c:df:37:9c:c3   
           inet addr:192.168.15.2  Bcast:192.168.15.255  Mask:255.255.255.0  
           inet6 addr: fe80::21c:dfff:fe37:9cc3/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:6 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:29 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:1617 (1.6 KB)  TX bytes:5322 (5.3 KB)  
 

 wmaster0  Link encap:UNSPEC  HWaddr 00-1C-DF-37-9C-C3-63-63-00-00-00-00-00-00-00-00   
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 char@char-desktop:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wmaster0  no wireless extensions.  
 

 wlan0     IEEE 802.11bg  ESSID:"phoenix"   
           Mode:Managed  Frequency:2.462 GHz  Access Point: 00:19:5B:3F:91:E6    
           Bit Rate=1 Mb/s   Tx-Power=20 dBm    
           Retry min limit:7   RTS thr:off   Fragment thr=2352 B    
           Power Management:off  
           Link Quality=60/100  Signal level:-41 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 pan0      no wireless extensions.  
 

 

 PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.  
 64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.033 ms  
 64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.025 ms  
 64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.009 ms  
 64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.008 ms  
 64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.007 ms  
 64 bytes from 127.0.0.1: icmp_seq=6 ttl=64 time=0.009 ms  
 64 bytes from 127.0.0.1: icmp_seq=7 ttl=64 time=0.007 ms  
 64 bytes from 127.0.0.1: icmp_seq=8 ttl=64 time=0.031 ms  
 64 bytes from 127.0.0.1: icmp_seq=9 ttl=64 time=0.031 ms  
 64 bytes from 127.0.0.1: icmp_seq=10 ttl=64 time=0.031 ms  
 64 bytes from 127.0.0.1: icmp_seq=11 ttl=64 time=0.008 ms  
 64 bytes from 127.0.0.1: icmp_seq=12 ttl=64 time=0.008 ms  
 64 bytes from 127.0.0.1: icmp_seq=13 ttl=64 time=0.007 ms  
 64 bytes from 127.0.0.1: icmp_seq=14 ttl=64 time=0.010 ms 




char@char-desktop:~$ ping 208.65.153  
 PING 208.65.153 (208.65.0.153) 56(84) bytes of data.  
 From 192.168.15.2 icmp_seq=9 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=10 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=11 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=12 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=13 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=14 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=15 Destination Host Unreachable 



Thanks in advance, 



-Charlie

---

### Post by superprash2003 on 2009-05-13
post output of** ping 74.125.67.100** . the last output you posted is invalid, as 208.65.153 is an invalid ip

---

### Post by charliko on 2009-05-13
Here it is!  Wish it said something else!



har@char-desktop:~$ ping 74.125.67.100  
 PING 74.125.67.100 (74.125.67.100) 56(84) bytes of data.  
 From 192.168.15.2 icmp_seq=1 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=2 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=3 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=4 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=5 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=6 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=7 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=8 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=9 Destination Host Unreachable

---

### Post by charliko on 2009-05-14
If this were a port problem, would it work it VISTA?

---

### Post by superprash2003 on 2009-05-14
no, type the following commands and then try - this command would bring down interfaces which are not in use
 
sudo ifdown eth0
sudo ifdown wmaster0

---

### Post by charliko on 2009-05-14
Here it is.  Still blocked somehow is my guess.  

> **superprash2003 said:**
> no, type the following commands and then try - this command would bring down interfaces which are not in use
 
sudo ifdown eth0
sudo ifdown wmaster0

	 	 char@char-desktop:~$ sudo ifdown eth0  
 [sudo] password for char:  
 ifdown: interface eth0 not configured  
 char@char-desktop:~$ sudo ifdown wmaster0  
 ifdown: interface wmaster0 not configured  
 char@char-desktop:~$ ping 74.125.67.100 
 PING 74.125.67.100 (74.125.67.100) 56(84) bytes of data.  
 From 192.168.15.2 icmp_seq=9 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=10 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=11 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=13 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=14 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=15 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=16 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=17 Destination Host Unreachable  
 From 192.168.15.2 icmp_seq=18 Destination Host Unreachable

---

### Post by superprash2003 on 2009-05-14
post the contents of the /etc/network/interfaces file

---

### Post by charliko on 2009-05-15
> **superprash2003 said:**
> post the contents of the /etc/network/interfaces file

       Response to       sudo gedit /etc/network/interfaces    is

   
  auto lo
   
  iface lo inet loopback

---

### Post by superprash2003 on 2009-05-15
add the following lines to the file
[B]
auto eth0

iface eth0 inet dhcp

auto wmaster0

iface wmaster0 inet dhcp[/B]

then type in the terminal **sudo /etc/init.d/networking restart**
then type the two commands i mentioned earlier ( the ifdown ones..)

---

### Post by charliko on 2009-05-15
> **superprash2003 said:**
> add the following lines to the file
[B]
auto eth0

iface eth0 inet dhcp

auto wmaster0

iface wmaster0 inet dhcp[/B]

then type in the terminal **sudo /etc/init.d/networking restart**
then type the two commands i mentioned earlier ( the ifdown ones..)

	 	 char@char-desktop:~$ sudo /etc/init.d/networking restart  
  * Reconfiguring network interfaces...                                          /etc/network/interfaces:6: unknown method  
 ifdown: couldn't read interfaces file "/etc/network/interfaces"  
 /etc/network/interfaces:6: unknown method  
 ifup: couldn't read interfaces file "/etc/network/interfaces"  
                                                                          [fail]  
 char@char-desktop:~$ sudo ifdown eth0  
 /etc/network/interfaces:6: unknown method  
 ifdown: couldn't read interfaces file "/etc/network/interfaces"  
 char@char-desktop:~$ sudo ifdown wmaster0  
 /etc/network/interfaces:6: unknown method  
 ifdown: couldn't read interfaces file "/etc/network/interfaces"  
 char@char-desktop:~$  
 char@char-desktop:~$ sudo gedit /etc/network/interfaces  
 char@char-desktop:~$ sudo gedit /etc/network/interfaces  
 char@char-desktop:~$ sudo ifdown eth0  
 /etc/network/interfaces:4: unknown method  
 ifdown: couldn't read interfaces file "/etc/network/interfaces"  
 char@char-desktop:~$ sudo ifdown wmaster0  
 /etc/network/interfaces:4: unknown method  
 ifdown: couldn't read interfaces file "/etc/network/interfaces"  
 char@char-desktop:~$ sudo gedit /etc/network/interfaces  
 

 

 auto lo  
 iface lo inet loopback  
 auto eth0  
 iface eth0 inet dchp  
 auto wmaster0  
 iface wmaster0 inet dchp


Before I restarted, the Belkin and your settings were working very well with 9.04.  I was able to pull up pages on the internet.  



When I restarted, it appeared that all was gone from the settings.  I could not get it to add a new wireless setting.  Hopefully this is as expected.  



Thanks again...for your know how.



-Charlie

---

### Post by superprash2003 on 2009-05-15
so after you restarted, did the /etc/network/interfaces file change again?? did you use the ifdown commmands after you restarted?

---

### Post by charliko on 2009-05-20
> **superprash2003 said:**
> so after you restarted, did the /etc/network/interfaces file change again?? did you use the ifdown commmands after you restarted?

I have tried and tried things.  I think I may be best served to just start completely over.  Before I completely reload the distro, I thought i would ask how to completely get things to where I could attempt to replicate your thread of commands.  

Presently, after I have given the system the encryption password ( I really wanted to avoid this) I am not connecting at all.  When I first tried the ifdown commands I could get the system to download webpages again.  Presently I cannot get a connection at all.  

Hence my logic to just get the system to erase all the clutter I may have created since we last chatted!

Thanks again!

-charlie

---

### Post by charliko on 2009-06-02
I take it that there is no fix in the works for all these wifi adaptors that will not work with jaunty

---

