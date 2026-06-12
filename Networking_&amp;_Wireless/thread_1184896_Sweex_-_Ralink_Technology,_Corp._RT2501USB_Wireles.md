---
title: "Sweex - Ralink Technology, Corp. RT2501USB Wireless Adapter - problems"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by Gird3r on 2009-06-11
I have spent around 5 hours on this problem now. And it's crucial that I get this to work because my dad want's to get rid of the network cables as soon as possible.

I have heard of two methods that works: the ndiswrapper and compiling the sourcecode that Ralink provides.

Here I will provide all information (that i remember doing) about this little annoying problem:

```


ndiswrapper -l
#It shows this below
rt2500usb : driver installed
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt73 : driver installed
	device (148F:2573) present (alternate driver: rt2500usb)

```
Before, it just showed the text below all the Warning. This appeared after I tried to blacklist the rt2500usb driver in:

sudo gedit /etc/modprobe.d/blacklist

Apprently, this was for blacklisting drivers that might "compete" for control. But it have not seemed to work.

An effect I noticed while exprementing was that the "Connect to hidden network" and "Create network" in the Network manager logo suddenly dissapeared. Also Wireless Network now shows:

Device is not handled(hanteras inte)

Yes i'm not some OMFG UBER GEEK PRO ubuntu user. So bear with me.

```

ifconfig 
#Shows this:

eth0      Link encap:Ethernet  HWaddr 00:19:21:35:f0:93  
          inet addr:192.168.10.99  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fe35:f093/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:933 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1200176 (1.2 MB)  TX bytes:171784 (171.7 KB)
          Interrupt:248 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:0a:19:4e:59  
          inet6 addr: fe80::216:aff:fe19:4e59/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:16:0a:19:4e:59  
          inet addr:169.254.3.107  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

```

The one at the bottom of that text appeared after I went trying to add two inf files to the GUI version of ndiswrapper. The inf files was rt73.inf and the rt2500Usb.inf files. They came from the WINXP folder that I copied off from the CD that you recive when buying one of these crappy things.

```

iwconfig
#Shows this:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
Note: Somehow I managed to force ESSID into dlink, wich is the standard router ESSID for the Dlink. I did the:

sudo iwconfig wlan0 essid dlink

That I think was all for that method.

I also heard about the sourcecode for Ralink's official Sourcecode drivers. So I went on trying to compile it, but it just tells me that there's no Rule for target config.o that's needed for wpa_supplicant: Stopping.


Wireless: 

Sweex LW053 USB Wireless "card".


I'm pretty much stuck on this, and would greatly appericiate help in form of a big THANK YOU.

So, how do I unfail what I done and peform win on this problem?

P.S. And if this get solved, how do I get this thing to connect to an Wireless router? D.S.

---

