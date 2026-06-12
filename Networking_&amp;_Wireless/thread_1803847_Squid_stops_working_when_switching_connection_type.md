---
title: "Squid stops working when switching connection type."
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by Mr. Shannon on 2011-07-13
Hello everyone, this is the first true question I have asked on this forum.

I have squid and dansguardian installed on my laptop.  What seems to be happening is when I go from home (ethernet) to school (wireless), or from school to home, squid stops working (sites don't load - at least some don't).  My fix was to shutdown squid with
```
sudo squid -k shutdown
```
delete the cache folder and then recreate it with
```
sudo squid -z
```
The problem is that this keeps happening and it is becoming a hassle to have to go through the 1-2 minute process every time I change my connection.  

I had squid and dansguardian set up and working for about a month on this installation and since Christmas on my old installation.  This problem has only started recently.  Occasionally, I would have to restart my computer because of DNS issues but I did not have to do so every time I changed connections.

Thanks in advance for any help.

---

### Post by Mr. Shannon on 2011-07-14
Does no one have any ideas?  Thanks again for any future help.

---

### Post by Mr. Shannon on 2011-07-19
I'm not sure if this is related since clearing the squid cache and restarting squid does not seem to always fix this but I am also getting this sometimes.

```
ERROR

The requested URL could not be retrieved

The following error was encountered while trying to retrieve the URL: http://dictionary.reference.com/

Unable to determine IP address from host name dictionary.reference.com

The DNS server returned:

Refused: The name server refuses to perform the specified operation.
This means that the cache was not able to resolve the hostname presented in the URL. Check if the address is correct.

Your cache administrator is webmaster.


Generated Tue, 19 Jul 2011 05:59:41 GMT by COMPUTER_NAME (squid/2.7.STABLE9)
```

What is wrong here and how do I fix it.

---

### Post by Mr. Shannon on 2011-07-21
bump

---

### Post by Mr. Shannon on 2011-07-25
bump

---

### Post by jmoorse on 2011-07-26
Please post the output of your squid.conf file

---

### Post by Mr. Shannon on 2011-07-26
Here is the my squid.conf file:

```

acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32
acl localnet src 10.0.0.0/8	# RFC1918 possible internal network
acl localnet src 172.16.0.0/12	# RFC1918 possible internal network
acl localnet src 192.168.0.0/16	# RFC1918 possible internal network
acl SSL_ports port 443		# https
acl SSL_ports port 563		# snews
acl SSL_ports port 873		# rsync
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl Safe_ports port 631		# cups
acl Safe_ports port 873		# rsync
acl Safe_ports port 901		# SWAT
acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
icp_access allow localnet
icp_access deny all
http_port 3128 transparent
hierarchy_stoplist cgi-bin ?
access_log /var/log/squid/access.log squid
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440

refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern (Release|Packages(.gz)*)$	0	20%	2880
refresh_pattern .		0	20%	4320
acl shoutcast rep_header X-HTTP09-First-Line ^ICY.[0-9]
upgrade_http0.9 deny shoutcast
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache
extension_methods REPORT MERGE MKACTIVITY CHECKOUT
hosts_file /etc/hosts
coredump_dir /var/spool/squid

```

I hope it's safe to post this with IP addresses in it.

---

### Post by jmoorse on 2011-07-26
Yes, those IPs are all private.  No risk there.

Are there any entries in /var/log/squid/cache.log during the time of the errors that you can post?

Edit: What is your IP address when at school?  You may need to add it to:

```

acl localnet src [school subnet IP]

```

---

### Post by Mr. Shannon on 2011-07-26
Here is a section of my /var/log/squid/cache.log from when I booted my computer this morning (at home) to when the squid cache had to be cleared at 8:00, when I turned my computer on at school.  At the end of the section (around 9:00) there are more errors but I think that is when I packed up my laptop (suspend) and carried it to lab.

```

2011/07/26 06:08:02| storeDirWriteCleanLogs: Starting...
2011/07/26 06:08:02|   Finished.  Wrote 130 entries.
2011/07/26 06:08:02|   Took 0.0 seconds (601851.9 entries/sec).
2011/07/26 06:08:02| logfileRotate: /var/log/squid/store.log
2011/07/26 06:08:02| logfileRotate (stdio): /var/log/squid/store.log
2011/07/26 06:08:02| logfileRotate: /var/log/squid/access.log
2011/07/26 06:08:02| logfileRotate (stdio): /var/log/squid/access.log
2011/07/26 06:21:42| Preparing for shutdown after 100 requests
2011/07/26 06:21:42| Waiting 30 seconds for active connections to finish
2011/07/26 06:21:42| FD 14 Closing HTTP connection
2011/07/26 06:21:42| Shutting down...
2011/07/26 06:21:42| FD 15 Closing ICP connection
2011/07/26 06:21:42| Closing unlinkd pipe on FD 11
2011/07/26 06:21:42| storeDirWriteCleanLogs: Starting...
2011/07/26 06:21:42|   Finished.  Wrote 130 entries.
2011/07/26 06:21:42|   Took 0.0 seconds (539419.1 entries/sec).
CPU Usage: 0.372 seconds = 0.188 user + 0.184 sys
Maximum Resident Size: 21712 KB
Page faults with physical i/o: 0
Memory usage for squid via mallinfo():
	total space in arena:    2684 KB
	Ordinary blocks:         2476 KB     27 blks
	Small blocks:               0 KB      5 blks
	Holding blocks:           280 KB      1 blks
	Free Small blocks:          0 KB
	Free Ordinary blocks:     207 KB
	Total in use:            2756 KB 93%
	Total free:               207 KB 7%
2011/07/26 06:21:42| logfileClose: closing log /var/log/squid/store.log
2011/07/26 06:21:42| logfileClose: closing log /var/log/squid/access.log
2011/07/26 06:21:42| Squid Cache (Version 2.7.STABLE9): Exiting normally.
2011/07/26 08:00:12| Starting Squid Cache version 2.7.STABLE9 for i386-debian-linux-gnu...
2011/07/26 08:00:12| Process ID 1101
2011/07/26 08:00:12| With 1024 file descriptors available
2011/07/26 08:00:12| Using epoll for the IO loop
2011/07/26 08:00:12| DNS Socket created at 0.0.0.0, port 50669, FD 6
2011/07/26 08:00:12| Adding domain domain.actdsltmp from /etc/resolv.conf
2011/07/26 08:00:12| Adding domain domain.actdsltmp from /etc/resolv.conf
2011/07/26 08:00:12| Adding nameserver 192.168.1.1 from /etc/resolv.conf
2011/07/26 08:00:12| User-Agent logging is disabled.
2011/07/26 08:00:12| Referer logging is disabled.
2011/07/26 08:00:12| logfileOpen: opening log /var/log/squid/access.log
2011/07/26 08:00:12| Unlinkd pipe opened on FD 11
2011/07/26 08:00:12| Swap maxSize 102400 + 8192 KB, estimated 8507 objects
2011/07/26 08:00:12| Target number of buckets: 425
2011/07/26 08:00:12| Using 8192 Store buckets
2011/07/26 08:00:12| Max Mem  size: 8192 KB
2011/07/26 08:00:12| Max Swap size: 102400 KB
2011/07/26 08:00:12| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2011/07/26 08:00:12| logfileOpen: opening log /var/log/squid/store.log
2011/07/26 08:00:12| Rebuilding storage in /var/spool/squid (CLEAN)
2011/07/26 08:00:12| Using Least Load store dir selection
2011/07/26 08:00:12| Set Current Directory to /var/spool/squid
2011/07/26 08:00:12| Loaded Icons.
2011/07/26 08:00:13| Accepting transparently proxied HTTP connections at 0.0.0.0, port 3128, FD 14.
2011/07/26 08:00:13| Accepting ICP messages at 0.0.0.0, port 3130, FD 15.
2011/07/26 08:00:13| HTCP Disabled.
2011/07/26 08:00:13| WCCP Disabled.
2011/07/26 08:00:13| Ready to serve requests.
2011/07/26 08:00:13| Done reading /var/spool/squid swaplog (130 entries)
2011/07/26 08:00:13| Finished rebuilding storage from disk.
2011/07/26 08:00:13|       130 Entries scanned
2011/07/26 08:00:13|         0 Invalid entries.
2011/07/26 08:00:13|         0 With invalid flags.
2011/07/26 08:00:13|       130 Objects loaded.
2011/07/26 08:00:13|         0 Objects expired.
2011/07/26 08:00:13|         0 Objects cancelled.
2011/07/26 08:00:13|         0 Duplicate URLs purged.
2011/07/26 08:00:13|         0 Swapfile clashes avoided.
2011/07/26 08:00:13|   Took 0.7 seconds ( 183.8 objects/sec).
2011/07/26 08:00:13| Beginning Validation Procedure
2011/07/26 08:00:13|   Completed Validation Procedure
2011/07/26 08:00:13|   Validated 130 Entries
2011/07/26 08:00:13|   store_swap_size = 90932k
2011/07/26 08:00:13| storeLateRelease: released 0 objects
2011/07/26 08:00:22| comm_udp_sendto: FD 6, 192.168.1.1, port 53: (101) Network is unreachable
2011/07/26 08:00:22| idnsSendQuery: FD 6: sendto: (101) Network is unreachable
2011/07/26 08:00:27| comm_udp_sendto: FD 6, 192.168.1.1, port 53: (101) Network is unreachable
2011/07/26 08:00:27| idnsSendQuery: FD 6: sendto: (101) Network is unreachable
2011/07/26 08:00:37| comm_udp_sendto: FD 6, 192.168.1.1, port 53: (101) Network is unreachable
2011/07/26 08:00:37| idnsSendQuery: FD 6: sendto: (101) Network is unreachable
2011/07/26 08:02:00| Preparing for shutdown after 4 requests
2011/07/26 08:02:00| Waiting 30 seconds for active connections to finish
2011/07/26 08:02:00| FD 14 Closing HTTP connection
2011/07/26 08:02:27| Starting Squid Cache version 2.7.STABLE9 for i386-debian-linux-gnu...
2011/07/26 08:02:27| Process ID 2438
2011/07/26 08:02:27| With 1024 file descriptors available
2011/07/26 08:02:27| Using epoll for the IO loop
2011/07/26 08:02:27| Performing DNS Tests...
2011/07/26 08:02:27| Successful DNS name lookup tests...
2011/07/26 08:02:27| DNS Socket created at 0.0.0.0, port 34522, FD 6
2011/07/26 08:02:27| Adding domain int.Colorado.EDU from /etc/resolv.conf
2011/07/26 08:02:27| Adding domain int.Colorado.EDU from /etc/resolv.conf
2011/07/26 08:02:27| Adding nameserver 128.138.129.76 from /etc/resolv.conf
2011/07/26 08:02:27| Adding nameserver 128.138.130.30 from /etc/resolv.conf
2011/07/26 08:02:27| Adding nameserver 128.138.240.1 from /etc/resolv.conf
2011/07/26 08:02:27| User-Agent logging is disabled.
2011/07/26 08:02:27| Referer logging is disabled.
2011/07/26 08:02:27| logfileOpen: opening log /var/log/squid/access.log
2011/07/26 08:02:27| Unlinkd pipe opened on FD 11
2011/07/26 08:02:27| Swap maxSize 102400 + 8192 KB, estimated 8507 objects
2011/07/26 08:02:27| Target number of buckets: 425
2011/07/26 08:02:27| Using 8192 Store buckets
2011/07/26 08:02:27| Max Mem  size: 8192 KB
2011/07/26 08:02:27| Max Swap size: 102400 KB
2011/07/26 08:02:27| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2011/07/26 08:02:27| logfileOpen: opening log /var/log/squid/store.log
2011/07/26 08:02:27| Rebuilding storage in /var/spool/squid (DIRTY)
2011/07/26 08:02:27| Using Least Load store dir selection
2011/07/26 08:02:27| Set Current Directory to /var/spool/squid
2011/07/26 08:02:27| Loaded Icons.
2011/07/26 08:02:27| Accepting transparently proxied HTTP connections at 0.0.0.0, port 3128, FD 12.
2011/07/26 08:02:27| Accepting ICP messages at 0.0.0.0, port 3130, FD 13.
2011/07/26 08:02:27| HTCP Disabled.
2011/07/26 08:02:27| WCCP Disabled.
2011/07/26 08:02:27| Ready to serve requests.
2011/07/26 08:02:27| Done scanning /var/spool/squid (0 entries)
2011/07/26 08:02:27| Finished rebuilding storage from disk.
2011/07/26 08:02:27|         0 Entries scanned
2011/07/26 08:02:27|         0 Invalid entries.
2011/07/26 08:02:27|         0 With invalid flags.
2011/07/26 08:02:27|         0 Objects loaded.
2011/07/26 08:02:27|         0 Objects expired.
2011/07/26 08:02:27|         0 Objects cancelled.
2011/07/26 08:02:27|         0 Duplicate URLs purged.
2011/07/26 08:02:27|         0 Swapfile clashes avoided.
2011/07/26 08:02:27|   Took 0.4 seconds (   0.0 objects/sec).
2011/07/26 08:02:27| Beginning Validation Procedure
2011/07/26 08:02:27|   Completed Validation Procedure
2011/07/26 08:02:27|   Validated 0 Entries
2011/07/26 08:02:27|   store_swap_size = 0k
2011/07/26 08:02:28| storeLateRelease: released 0 objects
2011/07/26 08:56:16| comm_udp_sendto: FD 6, 128.138.129.76, port 53: (101) Network is unreachable
2011/07/26 08:56:16| idnsSendQuery: FD 6: sendto: (101) Network is unreachable
2011/07/26 08:56:16| comm_udp_sendto: FD 6, 128.138.130.30, port 53: (101) Network is unreachable

```

> Edit: What is your IP address when at school? You may need to add it to:
```
acl localnet src [school subnet IP]
```


I was at school when I posted the squid.conf file, so are you saying to manually add the internal IP address of the school?  How would I go about finding it?  Forgive my network knowledge, I'm almost completely clueless when it comes to networks.

Thanks for all your help.

---

### Post by Mr. Shannon on 2011-07-29
bump

---

### Post by jmoorse on 2011-08-01
To find your subnet, when at school please post the output of:

```

ifconfig -a

```

If the addresses are not 10.x.x.x, 192.168.x.x or 172.x.x.x please post only the numbers in the first octet (before the first period)

---

### Post by Mr. Shannon on 2011-08-02
Below is the result of
```
ifconfig -a
```
when run at school after squid has been reset and is running.
Note: Some numbers have been crossed out.

```

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.x.x.x
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8422137 (8.4 MB)  TX bytes:8422137 (8.4 MB)

vboxnet0  Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:172.23.198.119  Bcast:172.23.199.255  Mask:255.xxx.xxx.x
          inet6 addr: fe80::xxx:xxxx:xxxx:eec2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6623154 (6.6 MB)  TX bytes:1157094 (1.1 MB)


```

---

### Post by jmoorse on 2011-08-02
Ok, that is all fine.  FYI you do not need to blank out MACs, masks or IPv6 with prefix fe80 (link local).

Also when reviewing the cache logs I noticed when you suspended it looks like it killed the process.  Are you sure squid is running when you resume from suspend?  What if you shutdown when you leave home and start up fresh @ school?

---

### Post by Mr. Shannon on 2011-08-04
> **jmoorse said:**
> Also when reviewing the cache logs I noticed when you suspended it looks like it killed the process.  Are you sure squid is running when you resume from suspend?  What if you shutdown when you leave home and start up fresh @ school?

I tried that this morning and squid still does not work until after I remove the cache.

---

