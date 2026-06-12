---
title: "squid 3 problem"
date: 2013-01-25
forum: Networking &amp; Wireless
---

### Post by okidokios on 2013-01-25
Hello guys if somebody can help me please i installed squid3 proxy but when i configure and start the service it just start but end at the same time cuz i check process and theres no squid on it i was wondering if probably is something with my ip's configuration im noob on this so if you can help me please this is my ifconfig 


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:400 (400.0 B)  TX bytes:400 (400.0 B)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00                      
          inet addr:127.0.0.2  P-t-P:127.0.0.2  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:72145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:67392442 (64.2 MiB)  TX bytes:4879042 (4.6 MiB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00                      
          inet addr:37.220.7.130  P-t-P:37.220.7.130  Bcast:0.0.0.0  Mask:255.255.25                     5.255


how should my squid.conf file looks like?

---

### Post by SeijiSensei on 2013-01-25
What does /var/log/squid/cache.log show?  Any errors will be logged there.

---

### Post by okidokios on 2013-01-26
FATAL: Cannot open HTTP Port
Squid Cache (Version 3.1.19): Terminated abnormally.
CPU Usage: 0.009 seconds = 0.005 user + 0.004 sys
Maximum Resident Size: 64976 KB
Page faults with physical i/o: 0
Memory usage for squid via mallinfo():
        total space in arena:    2396 KB
        Ordinary blocks:         2366 KB      3 blks
        Small blocks:               0 KB      1 blks
        Holding blocks:         35100 KB      9 blks
        Free Small blocks:          0 KB
        Free Ordinary blocks:      29 KB
        Total in use:           37466 KB 1564%
        Total free:                29 KB 1%

im using port 53

---

### Post by okidokios on 2013-01-26
here is more info 

2013/01/26 12:42:16| Starting Squid Cache version 3.1.19 for x86_64-pc-linux-gn$
2013/01/26 12:42:16| Process ID 2754
2013/01/26 12:42:16| With 65535 file descriptors available
2013/01/26 12:42:16| Initializing IP Cache...
2013/01/26 12:42:16| DNS Socket created at [::], FD 5
2013/01/26 12:42:16| DNS Socket created at 0.0.0.0, FD 6
2013/01/26 12:42:16| Adding nameserver 80.84.58.27 from /etc/resolv.conf
2013/01/26 12:42:16| Adding nameserver 80.84.58.28 from /etc/resolv.conf
2013/01/26 12:42:16| Unlinkd pipe opened on FD 11
2013/01/26 12:42:16| Local cache digest enabled; rebuild/rewrite every 3600/360$
2013/01/26 12:42:16| Store logging disabled
2013/01/26 12:42:16| Swap maxSize 0 + 262144 KB, estimated 20164 objects
2013/01/26 12:42:16| Target number of buckets: 1008
2013/01/26 12:42:16| Using 8192 Store buckets
2013/01/26 12:42:16| Max Mem  size: 262144 KB
2013/01/26 12:42:16| Max Swap size: 0 KB
2013/01/26 12:42:16| Using Least Load store dir selection
2013/01/26 12:42:16| Set Current Directory to /var/spool/squid3
2013/01/26 12:42:16| Loaded Icons.
2013/01/26 12:42:16| commBind: Cannot bind socket FD 12 to [::]:53: (98) Addres$
2013/01/26 12:42:16| storeDirWriteCleanLogs: Starting...
2013/01/26 12:42:16|   Finished.  Wrote 0 entries.
2013/01/26 12:42:16|   Took 0.00 seconds (  0.00 entries/sec).

---

### Post by SeijiSensei on 2013-01-26
> **okidokios said:**
> im using port 53

You can't use port 53; it's reserved for DNS services.  Why aren't you using the standard 3128 or some other arbitrary high (>1023) port?  If you are running a nameserver of some type, either BIND or dnsmasq, chances are good that it's already listening on 53.

In general, all the ports below 1024 have well-defined services assigned to them.  That's why Squid uses 3128 by default.

---

### Post by okidokios on 2013-01-26
ohh :/ cuz i use the proxy for my cellphone and only accepts port 53 thats why, so theres no chance to fix it? even if i ask the vps provider?

---

### Post by SeijiSensei on 2013-01-26
If 37.220.7.130 is your machine I see a lot of open ports -- 

FTP 21, 
SSH 22, 
DNS 53, 
HTTP 80, 
VNC 5901 (!), and 
X11 6001 (!).  

Those last two are really insecure, particularly VNC.  If you want to use X applications, don't open 6001 but run an X tunnel over SSH using "ssh -X user@host" when you log in.

Something, probably a DNS server, is listening on port 53 already, so Squid cannot bind to that port.

So if this is your own server, why can't you run Squid on 3128?  Is this a limitation of your phone?  On an Android phone you can use a [proxy with Firefox]("http://support.mozilla.org/en-US/questions/757976") and choose an arbitrary port.

---

### Post by okidokios on 2013-01-30
ohh well i finally got working the port53 i stoped the dns service and it works now but now i have a problem it connect to some sites and somes not the ones that won't load are facebook google youtube and many others any reason why won't load these sites?

this is what i got on cache log


2013/01/30 07:35:19|   Finished.  Wrote 0 entries.
2013/01/30 07:35:19|   Took 0.00 seconds (  0.00 entries/sec).
2013/01/30 07:35:19| logfileRotate: /var/log/squid3/access.log
2013/01/30 07:45:13| Failure Ratio at 1.016
2013/01/30 07:45:13| Going into hit-only-mode for 5 minutes...
2013/01/30 08:32:00| errorpage.cc(293) errorTryLoadText: '/usr/share/squid3/err$
2013/01/30 08:32:00| WARNING: Error Pages Missing Language: es-us
2013/01/30 11:11:15| Preparing for shutdown after 1705 requests
2013/01/30 11:11:15| Waiting 30 seconds for active connections to finish
2013/01/30 11:11:15| FD 12 Closing HTTP connection
2013/01/30 11:11:21| Starting Squid Cache version 3.1.19 for x86_64-pc-linux-gn$
2013/01/30 11:11:21| Process ID 13569
2013/01/30 11:11:21| With 65535 file descriptors available
2013/01/30 11:11:21| Initializing IP Cache...
2013/01/30 11:11:21| DNS Socket created at [::], FD 5
2013/01/30 11:11:21| DNS Socket created at 0.0.0.0, FD 6
2013/01/30 11:11:21| Adding nameserver 80.84.58.27 from /etc/resolv.conf
2013/01/30 11:11:21| Adding nameserver 80.84.58.28 from /etc/resolv.conf

---

### Post by furything on 2013-01-30
I agree with SeijiSensei

Firstly squid3 should be binding to port 80 for web traffic and listen by default to port 3128 (although this can be reconfigured).

What exactly are you trying to do with your cell phone and what is it?

I have four android phones in the house which I connect quite happily to my server in fact they run through dansguardian web filter as well.

If you just want to connect your phone to wifi then running squid at defaults is the correct way to go.

When I say defaults, I mean the port settings not the local lan ip range as this is specific to your network.

---

