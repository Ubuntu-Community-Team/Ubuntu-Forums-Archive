---
title: "Issue with WUSB600N in Ubuntu 11.04"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by kedarkekan on 2011-05-09
Hello,

I was able to successfully install the module for rt3572sta and create a interface ra0.
Unfortunately I don't see this interface in my Ubuntu network manager.

kedar@Optiplex:~$ ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:25:9c:01:28:6e  
          inet6 addr: fe80::225:9cff:fe01:286e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:7028 errors:20 dropped:0 overruns:0 frame:0
          TX packets:1217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1115338 (1.1 MB)  TX bytes:125812 (125.8 KB)

kedar@Optiplex:~$ iwconfig ra0
ra0       Ralink STA  ESSID:"gems*4WWaccess"  Nickname:"RT3572STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=46/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Did i miss anything in particular ?

I also see the right module when from lsmod:

rt3572sta             618810  1

Any help will be appreciated.
Thanks, Kedar

---

### Post by kedarkekan on 2011-05-10
ra0       Link encap:Ethernet  HWaddr 00:25:9c:00:1f:09  
          inet6 addr: fe80::225:9cff:fe00:1f09/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:109898 errors:319 dropped:0 overruns:0 frame:0
          TX packets:3124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15603182 (15.6 MB)  TX bytes:307588 (307.5 KB)


ra0       Ralink STA  ESSID:"safari"  Nickname:"RT3572STA"
          Mode:Auto  Frequency=2.437 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=70/100  Signal level:-23 dBm  Noise level:-23 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by iponeverything on 2011-05-10
does it exist in your /etc/network/interfaces file? if it does, then it will not be managed by NM.

---

### Post by Gunner2677 on 2011-05-12
Any luck on this yet?

---

### Post by el1te on 2011-05-12
i also have wusb600n v2 and would like to know if anyone has got this working in 11.04

right now i have it working in ubuntu 10.10 i386 desktop blocking the rt2800 and rt2x00 modules and using the rt3572sta

works great in 10.10 but would like to upgrade to 11.04

---

### Post by kittkatt on 2011-05-12
> i also have wusb600n v2 and would like to know if anyone has got this working in 11.04


Yes, I've gotten it working in 11.04 64-bit.  You can find out instructions in my [comment #108 on the bugtracker]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165").  

Hopefully I can whip up a script soon to automate the whole thing and add it to the community docs.

---

### Post by el1te on 2011-05-13
i installed 11.04 i386 Desktop today and can verify that if you blacklist these

blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

and then build the driver according to this guide:
[https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WUSB600N]("https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WUSB600N")

then it will work

i cant seem to figure out if it works in monitor mode
can someone give me the command to check or procedure and i will post back saying if it works with the procedure outlined in this post

---

### Post by chili555 on 2011-05-13
> can someone give me the command to check or procedure ```
sudo ifconfig ra0 down
sudo iwconfig ra0 mode monitor
```It will error out if monitor mode is not supported. I have a rt3572sta device and will try it now.

Edit: Works for me:> chili@LAPTOP60:~$ sudo iwconfig ra0 mode monitor
chili@LAPTOP60:~$ sudo iwconfig ra0 
ra0       Ralink STA  ESSID:""  Nickname:"RT3572STA"
          Mode:[COLOR="Red"]Monitor[/COLOR]  Frequency=2.462 GHz  Access Point: 00:24:56:2A:D7:29   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off


---

### Post by el1te on 2011-05-14
> **chili555 said:**
> ```
sudo ifconfig ra0 down
sudo iwconfig ra0 mode monitor
```It will error out if monitor mode is not supported. I have a rt3572sta device and will try it now.

Edit: Works for me:

yea i had already tried that.
i want to know the command or app that i need to run to actually make sure it works correctly

---

### Post by da ghost on 2011-06-11
El1te and chili555

I am also running Ubuntu 11.04 64bit with a WUSB600N v1

did you guys find a solution to this problem, that works 100%.

I may have missed it here on the forum because some of the technical terms are way over my head. I am a rookie, gave windows the heave ho!!

any assistance would be greatly appreciated.

---

### Post by da ghost on 2011-06-11
i did lsusb in the terminal window, and i got:

Bus 001 Device 002: ID 1737:0071 Linksys WUSB600N Dual-Band Wireless-N USB Network Adaptor.

---

### Post by jith911 on 2011-08-05
> **chili555 said:**
> ```
sudo ifconfig ra0 down
sudo iwconfig ra0 mode monitor
```It will error out if monitor mode is not supported. I have a rt3572sta device and will try it now.

Edit: Works for me:

I am also trying to bring up wusb600nv2[rt3572sta driver] card in monitor mode. I was able to set monitor mode for interfaces via iwconfig/iw utility.iwconfig returns that the interface is in Monitor mode. But the rx packets counters are not increasing + coulcdn't find any packets on the sniffer(wireshark). Anybody seen this issue before? Btw i am using ubuntu 11.04 64bit.


ra0       Ralink STA  ESSID:""  Nickname:"RT3572STA"
          Mode:Monitor  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11abgn  Mode:Monitor  Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off



Thanx in Adv,

Jithu Jance.

---

