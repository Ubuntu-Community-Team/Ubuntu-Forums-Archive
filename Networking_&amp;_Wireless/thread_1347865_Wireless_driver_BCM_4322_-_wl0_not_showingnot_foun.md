---
title: "Wireless driver BCM 4322 - wl0 not showing/not found."
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by Pranccc on 2009-12-06
Hello,
I am new to Ubuntu (v. 9.10), and have spent the last couple of days trying to figure out how to set up the Wi-Fi. I was really hoping I could figure it out myself, but now I'm at a complete loss. Possibly just stupidly missing something obvious.

The machine - Compaq 6735b laptop (32-bit)

The driver:

 *lscpi*
 > 09:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)




  *ifconfig*
>     eth0      Link encap:Ethernet  HWaddr 00:1f:29:b5:79:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

  


I followed thoroughly the steps found here - [http://ubuntuforums.org/showthread.php?t=896713&highlight=BCM4322](http://ubuntuforums.org/showthread.php?t=896713&highlight=BCM4322) ...but to no avail.

I want to get the system to detect WiFi, which it doesn't.

When I go to the 'Hardware Drivers' it tells me that *No proprietary drivers are in use on this system*.

Last of all (I THINK this is where the problem lies, but not really sure), when I type *iwconfig*, it produces this:

>     lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


  

As far as I understand, wl0 should appear here as well?

From the research I've done so far, I understand that the BCM4322 driver is problematic. I did find some hopeful info in the thread quoted above, but since that didn't work, I've no idea where else to go. What am I missing?

Any help/direction is greatly appreciated.

---

### Post by Pranccc on 2009-12-06
I just found this [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_(all%2C_ndiswrapper/firmware)]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_%28all%2C_ndiswrapper/firmware%29") , which might be helpful. It requires me to be connected to a hard-line though, but I suppose I can use one tomorrow. Sorry if this thread is redundant.

---

### Post by northd_tech on 2009-12-06
The "b43" and "fwcutter" stuff is mainly for the older Broadcom 4311, 4312 (and apparently 4318) WiFi interfaces.  Your 4322 (and my 4321AG Broadcom) actually prefer the "STA" driver for the 802.11n speeds, from what most people have posted here.  See this thread:

[http://ubuntuforums.org/showthread.php?t=1336676](http://ubuntuforums.org/showthread.php?t=1336676)

That "STA" fix is rumored to work for the whole family of Broadcoms (and mine could use the older 4311/4312 windows drivers fine under ndiswrapper, but most people have moved away from that to the proprietary "STA" driver).

You might be able to see that under System>Administration>Hardware Drivers (or see the thread(s) linked if it's not there.

---

### Post by Pranccc on 2009-12-07
Thank you very much. It's up and working now. An update basically sorted it. It is unfourtunate though that one needs to be hard-wired in order to set up the wireless (or at least to make things easier).

Either way, thanks a lot.

---

