---
title: "Cannot connect ti wireless with Lubuntu 12.04 but Ubuntu 10.04 LiveCD connects"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by OpenInformation on 2012-07-08
I boot up with live CD of Ubuntu 10.04 and click on the network icon on the taskbar, (you know the  .))))) ) and it connects nicely.

WIth my newly installed Lubuntu 12.04 I cannot connect in the same way it goes to 'configuring wireless' then says 'connection disconnected' or something like that.

May be I was foolish to select a wireless on installation. Hence my settings are as follows:

```
After connection attmempt1 on Lubuntu 12.04
g@uuD800:~$ iwconfig eth0
eth0      IEEE 802.11-DS  ESSID:"AndroidAP"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          Link Quality=0/100  Signal level=-116 dBm  Noise level=-116 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:350   Missed beacon:0
``````

g@uuD800:~$ 

g@uuD800:~$ iwconfig
wifi0     IEEE 802.11-DS  ESSID:"AndroidAP"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          Link Quality=0/100  Signal level=-116 dBm  Noise level=-116 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:584   Missed beacon:0

lo        no wireless extensions.

eth0      IEEE 802.11-DS  ESSID:"AndroidAP"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          Link Quality=0/100  Signal level=-116 dBm  Noise level=-116 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:584   Missed beacon:0

```**WORKING UBUNTU LIVE CD;**

```
ubuntu@ubuntu:~$ iwconfig eth0
eth0      IEEE 802.11-DS  ESSID:"tsunami"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          Link Quality=0/100  Signal level=-116 dBm  Noise level=-92 dBm
          Rx invalid nwid:171  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1514   Missed beacon:0
```After connectin sucessfully 
```

ubuntu@ubuntu:~$ iwconfig eth0
eth0      IEEE 802.11-DS  ESSID:"AndroidAP"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 5C:4C:A9:CB:AB:69   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          Link Quality=72/100  Signal level=-60 dBm  Noise level=-92 dBm
          Rx invalid nwid:191  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1776   Missed beacon:0


ubuntu@ubuntu:~$ iwpriv
lo        no private ioctls.

eth0      Available private ioctls :
          airoioctl        (8BE0) : set  12 byte  & get 2047 byte 
          airoidifc        (8BE1) : set  12 byte  & get   1 int  

wifi0     Available private ioctls :
          airoioctl        (8BE0) : set  12 byte  & get 2047 byte 
          airoidifc        (8BE1) : set  12 byte  & get   1 int  

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth0
       serial: 00:11:21:3d:0d:03
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.43.135 multicast=yes wireless=IEEE 802.11-DS
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:21:3d:0d:03  
          inet addr:192.168.43.135  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::211:21ff:fe3d:d03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2543 errors:27 dropped:0 overruns:0 frame:27
          TX packets:2109 errors:6 dropped:0 overruns:0 carrier:6
          collisions:23 txqueuelen:1000 
          RX bytes:3273289 (3.2 MB)  TX bytes:178415 (178.4 KB)
          Interrupt:3 Base address:0xd100lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8256 (8.2 KB)  TX bytes:8256 (8.2 KB)
```

---

### Post by OpenInformation on 2012-07-10
ifconfig  shows two network devices  wifi0 and eth0  with the same MAC address

Will boot with Lubuntu 12.04 live/install CD and check.

Checked this:  Lubuntu 12.04 live/install CD has the same problem!
Maybe it is a version 12,04 problem, 

Maybe I can remove the wifi0 entry and see

Also there is a sticky on how to list wireless info for troubleshooting: Will post info next 

  [Supported wireless cards list and procedure to get help]("http://ubuntuforums.org/showthread.php?t=370108")

---

### Post by OpenInformation on 2012-07-10
Working Ubuntu 10 live cd settings:

```

ubuntu@ubuntu:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common



ubuntu@ubuntu:~$ sudo lshw -C Network
PCI (sysfs)  
  *-network               
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth0
       serial: 00:11:21:3d:0d:03
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.43.135 multicast=yes wireless=IEEE 802.11-DS

``````
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11-DS  ESSID:"AndroidAP"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 5C:4C:A9:CB:AB:69   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=83/100  Signal level=-54 dBm  Noise level=-94 dBm
          Rx invalid nwid:211  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6366   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"AndroidAP"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 5C:4C:A9:CB:AB:69   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=83/100  Signal level=-54 dBm  Noise level=-94 dBm
          Rx invalid nwid:211  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6366   Missed beacon:0

```Now, Lubuntu 12.04 installed

```
g@uuD800:~$ iwconfig
wifi0     IEEE 802.11-DS  ESSID:"AndroidAP"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-116 dBm  Noise level=-116 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:584   Missed beacon:0

lo        no wireless extensions.

eth0      IEEE 802.11-DS  ESSID:"AndroidAP"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-116 dBm  Noise level=-116 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:584   Missed beacon:0

```The main difference is;
[B]
 Access Point: Invalid   [/B]

---

### Post by OpenInformation on 2012-07-11
This seems to be a common problem. Should fun to fix :)

**Possible solutions:**
**[FONT=Arial][SIZE=2]http://linuxplained.com/how-to-fix-wireless-problems-in-ubuntu-1204-precise-pangolin/[/SIZE][/FONT]**

**Way back to 2008:**
[http://ubuntuforums.org/showthread.php?t=914205](http://ubuntuforums.org/showthread.php?t=914205)
[http://ubuntuforums.org/showpost.php?p=5876983&postcount=8](http://ubuntuforums.org/showpost.php?p=5876983&postcount=8)
[http://ubuntuforums.org/showthread.php?t=917267](http://ubuntuforums.org/showthread.php?t=917267)

**Something about firmware**
[http://askubuntu.com/questions/133639/wireless-problems-ubuntu-12-04](http://askubuntu.com/questions/133639/wireless-problems-ubuntu-12-04)
[http://blog.tech4him.com/broadcom-wireless-on-ubuntu-11-04-and-11-10/](http://blog.tech4him.com/broadcom-wireless-on-ubuntu-11-04-and-11-10/)
[http://askubuntu.com/questions/125529/wireless-doesnt-work-on-a-broadcom-bcm4312](http://askubuntu.com/questions/125529/wireless-doesnt-work-on-a-broadcom-bcm4312)

**Guide**

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Lots of hacking ahead :)

Oh by the way, adding those lines to blacklist got the "networks detected" message going on the top right side of the screen. However still could not connect.

---

### Post by OpenInformation on 2012-07-15
downgraded to Ubuntu 10.04

Lubuntu is different from Ubuntu in the LXDE desktop and applications so Ubuntu with a lightweight desktop and lightweight apps will suffice:

Reinstalled Ubuntu 10.04


[LIST]
[*]Connected to wireless
[/LIST]

[LIST]
[*]Installed Video card using the software that detects and install the correct Invidia card
[*]Using Gnome-Openbox
[/LIST]
Disappointing that it did not work - will continue to test.

But still cannot connect to wireless when running LXDE.

---

