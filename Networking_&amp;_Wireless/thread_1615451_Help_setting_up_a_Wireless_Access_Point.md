---
title: "Help setting up a Wireless Access Point"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by modomobo on 2010-11-07
I'm trying to set up a wireless access point and router using Ubuntu 10.10. My machine has an Atheros AR5001X+ PCI card, and eth0 is connected to an ADSL modem.

After literally days and days of going in circles, I'm hoping that somebody here can help get me on track. I've tried to follow the instructions here:

[http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283)

This sort of works, though I had to go through some other contortions to get the madwifi driver to finally compile on my machine.

At this point, I can see and connect to the WAP, but nothing more. When I try "sudo /etc/init.d/networking restart", I get this:

```
 * Reconfiguring network interfaces...                                                       
SIOCDELRT: No such process
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
ssh stop/waiting
ssh start/running, process 2701
ath0
ath0: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "testing".
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device ath0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; No such device.
SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
ath0: ERROR while getting interface flags: No such device
Failed to bring up ath0.
```The interface configuration looks like this:

```
ath0      Link encap:Ethernet  HWaddr 0a:0a:79:72:f9:7b  
          inet addr:172.16.1.5  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::80a:79ff:fe72:f97b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40 (40.0 B)  TX bytes:1691 (1.6 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-0A-79-72-F9-7B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1788 errors:0 dropped:0 overruns:0 frame:358
          TX packets:1277 errors:151 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:187918 (187.9 KB)  TX bytes:100242 (100.2 KB)
          Interrupt:19 
```My /etc/network/interfaces file looks like this:

```
auto lo
iface lo inet loopback

auto ppp0
iface ppp0 inet ppp
        pre-up /sbin/ifconfig eth0 up
        provider dsl-provider eth0

auto ath0
iface ath0 inet static
pre-up wlanconfig ath0 destroy || true
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode ap
wireless-mode master
wireless-essid MyWAP
wireless channel 1
wireless-key testing
# wireless-key XXXXXXXXXXX
wireless-keymode open
address 172.16.1.5
netmask 255.255.255.0
gateway 172.16.1.1

```Any suggestions?

I also have a second problem, which is that I want to use WebMin to manage this server, but I cannot figure out how to get the ADSL client module configured -- RP-PPPoE version 3. It seems to expect to work with pppoe-start, pppoe-stop, and pppoe-status, but when I try to run pppoe-status it says "Link is down", even though my ppp connection is actually working.

Is is possible to use the WebMin ADSL client module with Ubuntu? I spent a lot of time trying to get pppoe-start, stop, etc. working but it was a complete mess and never seemed to behave. Finally, I just put the ppp startup commands into the /etc/network/interfaces file and that worked, but now the pppoe-* commands no longer seem to function.

Any suggestions about this would also be greatly appreciated.

---

### Post by modomobo on 2010-11-07
Well, it seems that WebMin is no longer supported by Ubuntu, so I guess you can ignore the second part of my question.

---

### Post by modomobo on 2010-11-08
Update: I tried reinstalling the whole OS from scratch. I have gotten further, but there are still issues. 

I think what I find most disconcerting is that none of the Ubuntu documentation has really worked for me. It all seems either out of date or too vague. I have spent days reading various forums on this site, and different parts of the community documentation. Also, I've gone to the #ubuntu IRC channel a few times to ask for help but there is never any response. 

At the moment, I'm feeling pretty frustrated with Ubuntu. Unless somebody has some suggestions, I'm now thinking that tomorrow I should just wipe Ubuntu and try a different distro.

---

