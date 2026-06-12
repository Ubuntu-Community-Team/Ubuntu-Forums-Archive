---
title: "trendnet tew-643pi wireless card not working"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by fibo112358 on 2009-01-05
Hi Forum!

I just installed my new wireless pci adapter, but it is not connecting to my wireless network. I installed the card, then booted into XP and the driver is installed there and the card works fine from XP. 

In Ubuntu, I installed ndiskwrapper and installed the driver from there. I think the device is being recognized: 

```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:f1:fc:02:59  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fefc:259/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:712568 (712.5 KB)  TX bytes:123121 (123.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:14:d1:4d:65:18  
          inet6 addr: fe80::214:d1ff:fe4d:6518/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:9702 (9.7 KB)
          Interrupt:21 Memory:feaed000-feaee000 

```

...but still no connection. Anything else I can try? Thank you!

Info: 

1. The card is listed above, and is wireless-n. 
2. I am using WEP, and when it tries to connect I am able to put in my key, but it doesn't work. 
3. I am connected now by my ethernet cable to the modem.

---

### Post by fibo112358 on 2009-01-05
Here is some more info about my situ:

```
lspci -nn
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8190]

```

(there are more pci devices of course, but this is my wireless card)

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan1
       version: 00
       serial: 00:14:d1:4d:65:18
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8190p driverversion=1.53+Realtek,05/21/2008,5.1058.0 latency=64 maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:0c:f1:fc:02:59
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.0.2 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 22:09:f6:3a:dd:41
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

```
sudo iwlist scan
[sudo] password for chase: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: 00:0F:B3:32:59:AB
                    ESSID:"CHASE"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

pan0      Interface doesn't support scanning.

```

-fibo out

---

### Post by fibo112358 on 2009-01-06
...anybody out there? I'm dying here.

---

### Post by fibo112358 on 2009-01-06
this is fibo coming to you wireless...

so after reading someone else's thread [http://ubuntuforums.org/showthread.php?t=1025208]("http://ubuntuforums.org/showthread.php?t=1025208"), I disabled WEP and now have a strong wireless connection. Just to recap, I:

1. installed trendnet tew-643pi into pci bus slot
2. installed latest driver with ndiswrapper
3. card seemed to be recognized and tried to autoconnect with my wep key
4. disabled WEP and am now connected.

I'll keep trying to get this connection secured, and report back my results.

By the way, this card is not listed on the list of supported Trendnet cards wiki and I can't find information about my chipset (10ec:8190) anywhere. I would think that someone would be interested in my problem. Unless I'm missing something in the code above (which is very probable), the problem seems to be in trying to use WEP with my combination of ndiswrapper running net8190p.inf driver. Since WEP is supported on my card, I thought this would be an interesting problem but the forum doesn't seem to want to parse this. How do I report this bug to the right people?

---

### Post by 73ckn797 on 2009-01-06
Try using wpa for security. I am reading much on WEP not working. I have a Trendnet card also on another computer and it does not even work. I have just begun the adventure!

---

### Post by monikersupreme on 2009-01-14
I've got one of these as well and am going to try and get it working on a dual boot XP / Intrepid installation. 

Currently under XP the card seems to work although the wireless bandwidth seems flaky at best... I've yet to install any specific drivers though. 

Hopefully under Ubuntu I'll be able to maintain a decent enough connection to pull video files off of my downstairs HTPC...

---

### Post by jeukel on 2009-11-09
Hello eveyone! I'm brinding this up cause i have the same card and intent to use it on ubuntu x64, no matter which distro just x64 along with native drivers, not ndiswrapper... If anyone has an idea, welcome! A friend made me compile the kernel around the driver trying to get a .ko but still need some files to make it work:

"RTL8192E/boot.img"
"RTL8192E/main.img" 
"RTL8192E/data.img" 

Aparently they comes along with openSUSE but had no chance to install it on my machine or a VM to get the files. They dont just come into the live CD. Hope this will help a lot of people that are having issues with the same card. If anyone wants exactly waht i did to get the . ko just ask ;)!

---

### Post by 73ckn797 on 2009-11-10
I solved my weak connection issue by going to Synaptic, installing "ndisgtk" then using the Windows XP driver. Works like a charm on 2 computers. I use WPA.

---

### Post by jeukel on 2010-01-11
Hi!

73ckn797: Mine worked like a charm just the way you said but usind the 8.10 i386, Now i'm with 9.10... I tried the i386 version and it had problems now and then... the dmesg gave me some error... Then, the x64 version, NOT working... it freezes the whole system... thats why i was wondering to use free drivers for this card... 

Still nobody has gone any further?? :(...

---

### Post by 73ckn797 on 2010-01-11
I have not tried it on a 64 bit setup.

---

### Post by IceCap on 2010-01-11
Looks like we have a similar situation.  I'm using xubuntu 9.10 (Mythbuntu 9.10).

  Using ndiswrapper with the drivers it appears to be recognized properly and work.  I can see the network.  However, when I try to connect to my network (with WPA2 security) it doesn't get an IP address.  For one reason or another DHCP doesn't get a lease offer (or something like that).

 The strange thing is that it worked the first time I set it up.  Then it stopped working.  Then I started playing around with my router (Airport Extreme) settings, like changing channels and enabling/disabling the 5MHz portion.  Each time I changed the setting (and the router rebooted) it would work for one connection (still very slow to acquire IP address though).

  I'm still working on this (don't get your hopes too high, I'm a total newbie).  It looks to me that this isn't related to the driver but really to some of the other pieces of software that are involved in getting the connection going (something isn't setup correctly).  There are multiple post on very similar symptoms for variety of setups, even wired connections.  

  IC

---

### Post by feetwet on 2010-01-27
Can anyone post their interfaces file that got this to work?

My card is working with the ndiswrapper and the xp drivers... I can do an 'iwlist scan' and see a list of networks including my own.

I cannot however seem to get connected to mine.. I use WEP.

A couple of old devices I have don't support WPA so I'm probably stuck on WEP.

Are there any settings to autostart the card at startup.

---

### Post by feetwet on 2010-01-28
> **feetwet said:**
> Can anyone post their interfaces file that got this to work?

My card is working with the ndiswrapper and the xp drivers... I can do an 'iwlist scan' and see a list of networks including my own.

I cannot however seem to get connected to mine.. I use WEP.

A couple of old devices I have don't support WPA so I'm probably stuck on WEP.

Are there any settings to autostart the card at startup.

Update...
I can get connected on WEP manually using iwconfig
[FONT=Courier New]sudo iwconfig wlan0 essid <essid> ap <xx:xx:xx:xx:xx:> key <XXX> commit[/FONT]

I can't figure out why I can't get this connection to autostart by adding these values to the interfaces file.???

The key shows up in the iwcofig after a system restart , but the essid does not seem to be set.

---

