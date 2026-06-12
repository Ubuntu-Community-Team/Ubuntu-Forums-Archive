---
title: "Wired internet connection and sound problems on ubuntu LTS 10.04"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by mohammedsaqib_2006 on 2011-07-01
H.. I've just started using ubuntu. Installed 10.04 LTS..64 bit on Vaio VPCCB laptop..
  The wired internet provided by the college isnt even getting detected.. and the network icon on the top right cornet of the screen still says no wireless network detected..
  I entered the proxy settings under wired tap of Network connections.
  

Internet works fine on windows 7
   
  etc/network/interfaces looks like this
  auto lo
  iface lo inet loopback


  On terminal: 

  saqib@saqib-VPCCB15FG:~$ ifconfig
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:76 errors:0 dropped:0 overruns:0 frame:0
            TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:5648 (5.6 KB)  TX bytes:5648 (5.6 KB)
   
  saqib@saqib-VPCCB15FG:~$ ifconfig -a
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:76 errors:0 dropped:0 overruns:0 frame:0
            TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:5648 (5.6 KB)  TX bytes:5648 (5.6 KB)
   
  wlan0     Link encap:Ethernet  HWaddr 4c:0f:6e:f9:c2:c4  
            BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Pls help me resolve these problems

---

### Post by himanshu.irde on 2012-04-02
download the file
[ATTACH]215322[/ATTACH]

extract the file in one folder .. ignore any error message..
open terminal & go to folder where u uncompress the files
and execute the following commands

sudo su
make install
modprobe atl1e
exit


ur wired lan will start working ..

but still i am not able to find sound card driver if u have any information plz share

---

