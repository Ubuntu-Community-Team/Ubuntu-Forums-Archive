---
title: "Can't Enable Wireless, best solution? Intel 3945ABG/8.10 Intrepid/Lenovo T61"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by HamaLee on 2009-02-28
Yup, yup--issues with my wireless.  Things were humming along beautifully until an update last week.  When I rebooted my computer, no wireless and I haven't been able to get it back since.  I've tried many of the suggested fixes: backports, getting rid of network manager, WICD, ndiswrapper, etc.  I ran into problems with all of them (I imagine I mucked things trying fixes I don't much understand). Wired internet does work fine.

So...I appreciate any advice!  I'm currently running a brand spankin' new 8.10 installation, current updates, kernel 2.6.27-11-generic

**ifconfig output:**
> eth0      Link encap:Ethernet  HWaddr 00:1e:37:88:ca:25  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:37ff:fe88:ca25/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2904124 (2.9 MB)  TX bytes:542825 (542.8 KB)
          Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

**iwconfig output:** 
> 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


**iwlist scan output:**
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.


All help much appreciated, I'll post more information if you need.  Be gentle--my terminal skillzzzz are all cut&paste.

Thank you!

---

### Post by HamaLee on 2009-03-01
*bump*
Pretty please?

---

### Post by newb85 on 2009-05-21
Were you able to find a fix to this?  I'm having the same issue (along with a lot of other people, from what I gather).  Was working great on Jaunty until I did a reinstall (for graphics card issues).  WICD, ndiswrapper, and other approaches have not fixed anything.

---

### Post by jsegel on 2009-05-21
same problem. hp bc6320. the wireless killswitch is engaged and cannot be unengaged in ubuntu.
TX-power: 0   should be 20

---

### Post by ashu2188 on 2011-10-18
Hey...anybody found solution to this problem? I have the same issue. I am using HP dv 2500 series laptop.

I found some link which i haven't tried yet. here are these

[https://lists.ubuntu.com/archives/ubuntu-users/2010-July/224000.html](https://lists.ubuntu.com/archives/ubuntu-users/2010-July/224000.html)

[http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html](http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html)  

I will try asap..do post here if anyone finds any solution.

---

