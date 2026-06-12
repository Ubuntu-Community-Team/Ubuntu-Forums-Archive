---
title: "Wireless inactive on fujitsu siemens"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by timmyhiggy on 2009-10-12
Hi Everyone,

I'm a complete ubuntu novice, and have just installed 9.04 on my fujitsu siemens amilo L7320GW. After a bit of help I got the screen resolution sorted out, but I've now unearthed a problem with the wireless card. Namely, I can't use it!

As I say, I'm a novice hence my being uncertain as to what information would be useful other than that i have followed the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=1180170") but they did nothing. Any help would be much appreciated. If any extra information would be useful then please tell me so I can provide it rather than just skim past!!

Cheers
Tim

---

### Post by timmyhiggy on 2009-10-13
Here is the output for the wifi part of ifconfig

> wifi0     Link encap:UNSPEC  HWaddr 00-C0-A8-BE-56-96-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:199
RX bytes:0 (0.0 B)  TX bytes:4600 (4.6 KB)
Interrupt:18

and windows device manager lists the network adaptor as "atheros AR5005G Wireless Network Adaptor"

iwconfig outputs this

> 
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""

          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
Apologies for the smilies...

---

### Post by timmyhiggy on 2009-10-14
A further issue i have just discovered:
Headphones output doesn't work.

---

### Post by timmyhiggy on 2009-10-18
after installing UNR on my netbook, it has become clear that ubuntu isn't turning the wireless card on and off, only enabling and disabling connections through it... This could well be the source of the problem on my ubuntu desktop install on my laptop as the card is always off at startup, and there is no bios option for "always on at startup"...
I don't suppose anybody knows how to switch the card on and off in ubuntu??

---

### Post by tgulen on 2009-10-21
Hi everyone,

I have Fujitsu Siemens Amilo A 1650G Laptop also. I installed Ubuntu 9.04 2 weeks ago but I couldn't run my wireless button. For this reason I have to connect Internet via cable. 

Is there anybody found the solution before? 

For now, Thans... 

TG

---

### Post by safetycritical on 2009-10-30
I've got a Fujitsu Siemens Amilo A1650G. I've had the wireless working very intermittently with 9.04. You don't need to turn it on as with Windows!! And not at all with 9.10. There's plenty of people who have suggested ways to try and fix it. The only thing I haven't tried is a backport of the kernel. I'm not sure how to do it though. 

Don't give up!! And let me know if you fix it.


= = = = =
Advice here:
[http://ubuntuforums.org/showthread.php?t=1543006&page=147&p=12859180&viewfull=1#post12859180](http://ubuntuforums.org/showthread.php?t=1543006&page=147&p=12859180&viewfull=1#post12859180)
Mörgæs 2013-11-27

---

