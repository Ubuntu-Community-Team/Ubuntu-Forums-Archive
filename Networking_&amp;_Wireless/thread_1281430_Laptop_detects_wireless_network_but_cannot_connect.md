---
title: "Laptop detects wireless network but cannot connect"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by woodley42 on 2009-10-03
I have just moved into a new shared house and my laptop can detect, but cannot connect to the wireless router provided by Sky Broadband.  Having checked on the forum sky seems to work with ubuntu (i run hardy heron).

I have tried using the edit wireless networks option as the information stored within this part related to my old connection.  HOwever having changed this, and many attempts at just typing in the password it refuses to connect.

I ran the suggestions in the wireless trouble shooting section and got the following but it means nothing to me.  Perhaps someone can offer some suggestions?  Many thanks in advance.


In the Hardware testing section i got this.......
Testing your connection to the Internet:

ERROR:root:Could not find def gateway info in /proc
Traceback (most recent call last):
  File "/usr/share/hwtest/scripts/internet_test", line 132, in <module>
    sys.exit(main(sys.argv[1:]))
  File "/usr/share/hwtest/scripts/internet_test", line 118, in main
    host = route.get_default_gateway()
  File "/usr/share/hwtest/scripts/internet_test", line 81, in get_default_gateway
    t1 = self._get_default_gateway_from_bin_route()
  File "/usr/share/hwtest/scripts/internet_test", line 69, in _get_default_gateway_from_bin_route
    if def_gateway:
UnboundLocalError: local variable 'def_gateway' referenced before assignment

For the later troubleshooting sections in the terminal i got this..........

paul@paul-laptop:~$ # sudo lshw -C network
paul@paul-laptop:~$ 
paul@paul-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11-DS  Mode:Managed  
          
wlan0     IEEE 802.11-DS  Mode:Managed  
          Link Quality:11/70  Signal level:-83 dBm  Noise level:-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:87  Rx invalid frag:0
          Tx excessive retries:9  Invalid misc:1089   Missed beacon:0

paul@paul-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:6b:d0:54:14  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64100 (62.5 KB)  TX bytes:64100 (62.5 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-05-3C-08-2B-AA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13231 (12.9 KB)  TX bytes:3788 (3.6 KB)
          Interrupt:11 

wlan0     Link encap:Ethernet  HWaddr 00:05:3c:08:2b:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11413 (11.1 KB)  TX bytes:3736 (3.6 KB)
          Interrupt:11 

paul@paul-laptop:~$ ping 82.211.81.158
connect: Network is unreachable


ANY ideas what the problem is?

Many thanks

---

### Post by unmole on 2009-10-03
Which drivers are you using. I had a similar problem with b43 drivers and now it is fixed with the STA driver.

---

### Post by woodley42 on 2009-10-03
Hi thanks for the quick reply.
How do i find out which drivers i'm using?

I tried the check for driver section 3.2.2 in troubleshhoting and got this....

paul@paul-laptop:~$ sudo lshw -C network
[sudo] password for paul: 
  *-network:0 DISABLED    
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:05:3c:08:2b:aa
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.4.9 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:09:6b:d0:54:14
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.0.8 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s


Does that help?  Needless to say I'm new to this.

---

### Post by unmole on 2009-10-03
Go to System->Administration->Hardware Drivers
All drivers currently in use should be displayed. Post back what you see.

---

### Post by woodley42 on 2009-10-03
It says no proprietry drivers are in use on this system.  

Not sure how it managed to work on the last router then!

---

### Post by woodley42 on 2009-10-03
HOwever, Ive just checked on the connection information menu (right clcik on network icon) and it says the driver is e100, interface is ethernet (Eth0)

---

### Post by unmole on 2009-10-03
post the out put of 

```
 iwconfig 
```

Just curious, did you mange to connect in windows?

---

### Post by woodley42 on 2009-10-03
iwconfig output

paul@paul-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:87  Rx invalid frag:0
          Tx excessive retries:9  Invalid misc:1089   Missed beacon:0


Yes it connected on windows and it also connected on linux to another router provided by TalkTalk (in the UK)

---

### Post by woodley42 on 2009-10-04
bump.

I still havent got this resolved.  A quick recap.  My laptop previously connected fine on linux to a router provided by a different ISP.  I have since moved house and it will not connect.

All the networks are detected but entering passwords does not work and having run through a few checks (see above) it seems the laptop isnt detecting any drivers.

Any suggestions gratefully recieved.

---

### Post by mbuell on 2009-10-04
My guess is that this is not a driver issue, but a network settings issue. Both are possible, I suppose, but this > paul@paul-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wifi0 IEEE 802.11-DS Mode:Managed

wlan0 IEEE 802.11-DS Mode:Managed
Link Quality:11/70 Signal level:-83 dBm Noise level:-94 dBm
Rx invalid nwid:0 Rx invalid crypt:87 Rx invalid frag:0
Tx excessive retries:9 Invalid misc:1089 Missed beacon:0 If I'm not mistaken, tells us your OS has found the wifi card and it is working. 

So I'm not clear on some things that might help narrow this down. I'll recap what you said, please make sure I've got it right.
1. This machine, with no hardware changes, using the same Ubuntu install, connected to a previous wifi network. 
2. This machine, using Windows, connected to that previous wifi network. 
3. And, of course, you aren't connecting to the new wifi network.

I have a question then. Did you connect to the NEW network with this machine running Windows? 
If yes, see (A)
If no, see (B)

(A)Run Windows. Check the wifi settings very closely, please. SSID, WEP or WPA authentication, "key" spelling and capitalization, password spelling, and anything else you may have there. Write down these settings and then please recheck the Ubuntu settings to make sure they are identical. 

(B)IF NO, this machine has NOT connected to the new network using a Windows install, then do you have a dual boot, and can you try to connect using Windows? If you don't, and haven't, then you can't rule out the settings. If this is the case, I would still review, if possible, the settings on a computer at the same location that DOES connect to the internet. 

Once you believe you have ruled out the network settings, you will want to try the driver route. While others have had success with madwifi, my best luck on my machines has been with ndiswrapper, and installing the Windows drivers. People also speak highly of wicd as a network manager, but I've had better luck with the native gnome network manager and Wifi-radar. I think this is all very setup-dependent.

Good luck.

---

### Post by woodley42 on 2010-01-31
Just updating this thread, as its pretty much solved now.

It turns out that the reason i could not link to the wireless router is that my laptop does not support WPA security on the router.  This is the offending hardware:

Prism 2.5 Wavelan chipset

By searching on the web i found out that it can work provided you change the settings in the router to WEP, which is supported. Presumably this was what my last router used.

However with 5 other people in the house i thought i'd be better investing in a long cable, rather than risk disturbing other peoples access.

---

### Post by northd_tech on 2010-02-21
> **mbuell said:**
> 
Once you believe you have ruled out the network settings, you will want to try the driver route. While others have had success with madwifi, my best luck on my machines has been with ndiswrapper, and installing the Windows drivers. People also speak highly of wicd as a network manager, but I've had better luck with the native gnome network manager and Wifi-radar. I think this is all very setup-dependent.

If people need to run WPA under ndiswrapper, I found some HOWTOs on that and posted them on this thread at post #3:

[http://ubuntuforums.org/showpost.php?p=8860325&postcount=3](http://ubuntuforums.org/showpost.php?p=8860325&postcount=3)

---

