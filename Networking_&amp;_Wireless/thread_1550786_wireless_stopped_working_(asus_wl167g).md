---
title: "wireless stopped working (asus wl167g)"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by Natasha D on 2010-08-11
Hi all!
I'm a fairly new ubuntu user..
I installed it on an old laptop recently.. The wireless adapte built into the laptop had stopped working a while ago, so after doing some research I bought an Asus WL167g adapter which worked pretty much out of the box.. It worked fine the first 2 times I used it, but I just plugged it in to my computer again..and while it is being recognized as a usb device, it doesn't seem to work any more.. In network manager it lists my device, but it's greyed out and says wireless is disabled..
I just tried the device on my desktop computer which is running Windows XP and it worked fine there, so does any one have any ideas as to what may be going on?
Thanks,
Natasha!

---

### Post by Kudak on 2010-08-11
can you write what ifconfig and iwconfig output is please

---

### Post by SaintDanBert on 2010-08-11
If you are using Intel wireless hardware and **iwlagn** you might be seeing a driver crash like I am.

Sadly, I'm finding little help and even less discussion of the issue.

~~~ 0;-/ Dan

Ubuntu Lucid on Intel 4965 AGN wifi parts.

---

### Post by Natasha D on 2010-08-12
Hi Kudak,
I've pasted the outputs below (but my dongle is currently working)...
I've realized that when I turn on my computer it won't work, but when I restart after that, it starts to work!
This seems kinda strange, any thoughts on that?

natasha@natasha-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"lrdnetwrk"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:21:29:CB:21:B3   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

natasha@natasha-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:4a:84:92:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 90:e6:ba:75:8f:0b  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::92e6:baff:fe75:8f0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:243983 (243.9 KB)  TX bytes:46570 (46.5 KB)

---

### Post by Kudak on 2010-08-12
i need to see the output while ur connection doesnt work :)

---

### Post by Natasha D on 2010-08-12
hey kudak, 
Here it is:

natasha@natasha-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID: off/any  
          Mode:Man****  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Man****  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on


------------------------------------------------------------------------------------------------------------------------------------
natasha@natasha-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:4a:84:92:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

-----------------------------------------------------------------------------------------------------------------------------------------

I appreciate the help  : )

---

### Post by Natasha D on 2010-08-15
Bump!

---

### Post by Natasha D on 2010-08-17
Anyone at all???

---

### Post by kiridude on 2010-08-17
How about if you right click on network manager and check "enable wireless"

---

### Post by Natasha D on 2010-08-17
> **kiridude said:**
> How about if you right click on network manager and check "enable wireless"

I only wish it was that easy -- that option is greyed out.

---

### Post by Natasha D on 2010-08-18
I hate that I keep doing this, but I need a solution...so..
BUMP!

---

### Post by SaintDanBert on 2010-08-19
> **Natasha D said:**
> Bump!

Okay, what does "bump" mean?

If this is something that I should have read about in the netiquette pages, I missed it.  Where should I go and read?

~~~ 0;-/ Dan

---

### Post by Natasha D on 2010-08-19
HAHA:

[http://en.wikipedia.org/wiki/Bump_%28Internet%29](http://en.wikipedia.org/wiki/Bump_%28Internet%29)

---

### Post by liquidfunk on 2010-08-19
I wonder if its a module issue. If you can find out what modules are loaded at present when its working, then when its not perhaps we can add a solution.

```
lsmod
```

Then

```
modinfo <name_of_driver
```

Maybe post the two outputs both working and not working.

---

