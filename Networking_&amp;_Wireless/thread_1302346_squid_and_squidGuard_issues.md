---
title: "squid and squidGuard issues"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by spydr98 on 2009-10-27
I have a problem with squid dieing when using squidGuard as a redirector.
Squid on its own runs just fine.
 And squidGuard testing on its own is also fine.

```

squid -NCd1
2009/10/27 00:18:28| Starting Squid Cache version 2.7.STABLE3 for i386-debian-linux-gnu...
2009/10/27 00:18:28| Process ID 32075
2009/10/27 00:18:28| With 1024 file descriptors available
2009/10/27 00:18:28| Using epoll for the IO loop
2009/10/27 00:18:28| Performing DNS Tests...
2009/10/27 00:18:28| Successful DNS name lookup tests...
2009/10/27 00:18:28| DNS Socket created at 0.0.0.0, port 53657, FD 6
2009/10/27 00:18:28| Adding domain -----.com from /etc/resolv.conf
2009/10/27 00:18:28| Adding nameserver 192.168.10.100 from /etc/resolv.conf
2009/10/27 00:18:28| logfileOpen: opening log /var/log/squid/user_agent.log
2009/10/27 00:18:28| Referer logging is disabled.
2009/10/27 00:18:28| logfileOpen: opening log /var/log/squid/access.log
2009/10/27 00:18:28| Unlinkd pipe opened on FD 12
2009/10/27 00:18:28| Swap maxSize 102400 KB, estimated 7876 objects
2009/10/27 00:18:28| Target number of buckets: 393
2009/10/27 00:18:28| Using 8192 Store buckets
2009/10/27 00:18:28| Max Mem  size: 10240 KB
2009/10/27 00:18:28| Max Swap size: 102400 KB
2009/10/27 00:18:28| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
2009/10/27 00:18:28| Store logging disabled
2009/10/27 00:18:28| Rebuilding storage in /var/spool/squid (CLEAN)
2009/10/27 00:18:28| Using Least Load store dir selection
2009/10/27 00:18:28| Current Directory is /etc/squid
2009/10/27 00:18:28| Loaded Icons.
2009/10/27 00:18:29| Accepting transparently proxied HTTP connections at 0.0.0.0, port 3182, FD 13.
2009/10/27 00:18:29| HTCP Disabled.
2009/10/27 00:18:29| WCCP Disabled.
2009/10/27 00:18:29| Ready to serve requests.
2009/10/27 00:18:29| Done reading /var/spool/squid swaplog (223 entries)
2009/10/27 00:18:29| Finished rebuilding storage from disk.
2009/10/27 00:18:29|       223 Entries scanned
2009/10/27 00:18:29|         0 Invalid entries.
2009/10/27 00:18:29|         0 With invalid flags.
2009/10/27 00:18:29|       223 Objects loaded.
2009/10/27 00:18:29|         0 Objects expired.
2009/10/27 00:18:29|         0 Objects cancelled.
2009/10/27 00:18:29|         0 Duplicate URLs purged.
2009/10/27 00:18:29|         0 Swapfile clashes avoided.
2009/10/27 00:18:29|   Took 0.3 seconds ( 721.0 objects/sec).
2009/10/27 00:18:29| Beginning Validation Procedure
2009/10/27 00:18:29|   Completed Validation Procedure
2009/10/27 00:18:29|   Validated 223 Entries
2009/10/27 00:18:29|   store_swap_size = 9796k
2009/10/27 00:18:29| storeLateRelease: released 0 objects
^C
2009/10/27 00:18:33| Preparing for shutdown after 0 requests
2009/10/27 00:18:33| Waiting 0 seconds for active connections to finish
2009/10/27 00:18:33| FD 13 Closing HTTP connection
2009/10/27 00:18:33| Shutting down...
2009/10/27 00:18:33| Closing unlinkd pipe on FD 12
2009/10/27 00:18:33| storeDirWriteCleanLogs: Starting...
2009/10/27 00:18:33|   Finished.  Wrote 223 entries.
2009/10/27 00:18:33|   Took 0.0 seconds (547911.5 entries/sec).
2009/10/27 00:18:33| logfileClose: closing log /var/log/squid/access.log
2009/10/27 00:18:33| logfileClose: closing log /var/log/squid/user_agent.log
2009/10/27 00:18:33| Squid Cache (Version 2.7.STABLE3): Exiting normally.

``````

echo "http://www.google.com/ 192.168.10.21 - - GET" | squidGuard -d -c /etc/squid/squidGuard.conf
2009-10-26 23:26:14 [15942] init domainlist /var/lib/squidguard/db/ads/domains
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/ads/domains.db
2009-10-26 23:26:14 [15942] init urllist /var/lib/squidguard/db/ads/urls
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/ads/urls.db
2009-10-26 23:26:14 [15942] init domainlist /var/lib/squidguard/db/ads2/domains
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/ads2/domains.db
2009-10-26 23:26:14 [15942] init urllist /var/lib/squidguard/db/ads2/urls
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/ads2/urls.db
2009-10-26 23:26:14 [15942] init domainlist /var/lib/squidguard/db/dymanic/domains
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/dymanic/domains.db
2009-10-26 23:26:14 [15942] init domainlist /var/lib/squidguard/db/jean/domains
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/jean/domains.db
2009-10-26 23:26:14 [15942] init domainlist /var/lib/squidguard/db/lizzy/domains
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/lizzy/domains.db
2009-10-26 23:26:14 [15942] init domainlist /var/lib/squidguard/db/marketingware/domains
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/marketingware/domains.db
2009-10-26 23:26:14 [15942] init domainlist /var/lib/squidguard/db/phishing/domains
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/phishing/domains.db
2009-10-26 23:26:14 [15942] init domainlist /var/lib/squidguard/db/porn/domains
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/porn/domains.db
2009-10-26 23:26:14 [15942] init domainlist /var/lib/squidguard/db/sect/domains
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/sect/domains.db
2009-10-26 23:26:14 [15942] init domainlist /var/lib/squidguard/db/spyware/domains
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/spyware/domains.db
2009-10-26 23:26:14 [15942] init urllist /var/lib/squidguard/db/spyware/urls
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/spyware/urls.db
2009-10-26 23:26:14 [15942] init domainlist /var/lib/squidguard/db/tracker/domains
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/tracker/domains.db
2009-10-26 23:26:14 [15942] init urllist /var/lib/squidguard/db/tracker/urls
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/tracker/urls.db
2009-10-26 23:26:14 [15942] init domainlist /var/lib/squidguard/db/custom/allowed/domains
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/custom/allowed/domains.db
2009-10-26 23:26:14 [15942] init urllist /var/lib/squidguard/db/custom/allowed/urls
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/custom/allowed/urls.db
2009-10-26 23:26:14 [15942] init domainlist /var/lib/squidguard/db/custom/blocked/domains
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/custom/blocked/domains.db
2009-10-26 23:26:14 [15942] init urllist /var/lib/squidguard/db/custom/blocked/urls
2009-10-26 23:26:14 [15942] loading dbfile /var/lib/squidguard/db/custom/blocked/urls.db
2009-10-26 23:26:14 [15942] squidGuard 1.2.0 started (1256613974.940)
2009-10-26 23:26:14 [15942] recalculating alarm in 2026 seconds
2009-10-26 23:26:14 [15942] squidGuard ready for requests (1256613974.998)

2009-10-26 23:26:14 [15942] squidGuard stopped (1256613974.999)

``````

echo "http://www.sex.com/ 192.168.10.21 - - GET" | squidGuard -d -c /etc/squid/squidGuard.conf      2009-10-27 00:06:19 [28911] init domainlist /var/lib/squidguard/db/ads/domains
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/ads/domains.db
2009-10-27 00:06:19 [28911] init urllist /var/lib/squidguard/db/ads/urls
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/ads/urls.db
2009-10-27 00:06:19 [28911] init domainlist /var/lib/squidguard/db/ads2/domains
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/ads2/domains.db
2009-10-27 00:06:19 [28911] init urllist /var/lib/squidguard/db/ads2/urls
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/ads2/urls.db
2009-10-27 00:06:19 [28911] init domainlist /var/lib/squidguard/db/dymanic/domains
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/dymanic/domains.db
2009-10-27 00:06:19 [28911] init domainlist /var/lib/squidguard/db/jean/domains
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/jean/domains.db
2009-10-27 00:06:19 [28911] init domainlist /var/lib/squidguard/db/lizzy/domains
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/lizzy/domains.db
2009-10-27 00:06:19 [28911] init domainlist /var/lib/squidguard/db/marketingware/domains
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/marketingware/domains.db
2009-10-27 00:06:19 [28911] init domainlist /var/lib/squidguard/db/phishing/domains
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/phishing/domains.db
2009-10-27 00:06:19 [28911] init domainlist /var/lib/squidguard/db/porn/domains
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/porn/domains.db
2009-10-27 00:06:19 [28911] init domainlist /var/lib/squidguard/db/sect/domains
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/sect/domains.db
2009-10-27 00:06:19 [28911] init domainlist /var/lib/squidguard/db/spyware/domains
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/spyware/domains.db
2009-10-27 00:06:19 [28911] init urllist /var/lib/squidguard/db/spyware/urls
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/spyware/urls.db
2009-10-27 00:06:19 [28911] init domainlist /var/lib/squidguard/db/tracker/domains
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/tracker/domains.db
2009-10-27 00:06:19 [28911] init urllist /var/lib/squidguard/db/tracker/urls
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/tracker/urls.db
2009-10-27 00:06:19 [28911] init domainlist /var/lib/squidguard/db/custom/allowed/domains
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/custom/allowed/domains.db
2009-10-27 00:06:19 [28911] init urllist /var/lib/squidguard/db/custom/allowed/urls
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/custom/allowed/urls.db
2009-10-27 00:06:19 [28911] init domainlist /var/lib/squidguard/db/custom/blocked/domains
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/custom/blocked/domains.db
2009-10-27 00:06:19 [28911] init urllist /var/lib/squidguard/db/custom/blocked/urls
2009-10-27 00:06:19 [28911] loading dbfile /var/lib/squidguard/db/custom/blocked/urls.db
2009-10-27 00:06:19 [28911] squidGuard 1.2.0 started (1256616379.624)
2009-10-27 00:06:19 [28911] recalculating alarm in 21221 seconds
2009-10-27 00:06:19 [28911] squidGuard ready for requests (1256616379.681)
2009-10-27 00:06:19 [28911] Request(Adults/custom-blocked/-) http://www.sex.com/ 192.168.10.21/- - -
http://tartarus.-----.com/firewall/index.php?caddr=192.168.10.21&cname=&target=custom-blocked&url=http://www.sex.com/&source=Adults 192.168.10.21/- - -
2009-10-27 00:06:19 [28911] squidGuard stopped (1256616379.682)

```It's just when squid is configured with squidGuard
```

squid -NCd1
 2009/10/26 23:25:22| Starting Squid Cache version 2.7.STABLE3 for i386-debian-linux-gnu...
 2009/10/26 23:25:22| Process ID 15673
 2009/10/26 23:25:22| With 1024 file descriptors available
 2009/10/26 23:25:22| Using epoll for the IO loop
 2009/10/26 23:25:22| Performing DNS Tests...
 2009/10/26 23:25:22| Successful DNS name lookup tests...
 2009/10/26 23:25:22| DNS Socket created at 0.0.0.0, port 49187, FD 6
 2009/10/26 23:25:22| Adding domain -----.com from /etc/resolv.conf
 2009/10/26 23:25:22| Adding nameserver 192.168.10.100 from /etc/resolv.conf
 2009/10/26 23:25:22| helperOpenServers: Starting 5 'squidGuard' processes
 2009/10/26 23:25:22| logfileOpen: opening log /var/log/squid/user_agent.log
 2009/10/26 23:25:22| Referer logging is disabled.
 2009/10/26 23:25:22| logfileOpen: opening log /var/log/squid/access.log
 2009/10/26 23:25:22| Unlinkd pipe opened on FD 17
 2009/10/26 23:25:22| Swap maxSize 102400 KB, estimated 7876 objects
 2009/10/26 23:25:22| Target number of buckets: 393
 2009/10/26 23:25:22| Using 8192 Store buckets
 2009/10/26 23:25:22| Max Mem  size: 10240 KB
 2009/10/26 23:25:22| Max Swap size: 102400 KB
 2009/10/26 23:25:22| Local cache digest enabled; rebuild/rewrite every 3600/3600 sec
 2009/10/26 23:25:22| Store logging disabled
 2009/10/26 23:25:22| Rebuilding storage in /var/spool/squid (CLEAN)
 2009/10/26 23:25:22| Using Least Load store dir selection
 2009/10/26 23:25:22| Current Directory is /etc/squid
 2009/10/26 23:25:22| Loaded Icons.
 2009/10/26 23:25:22| Accepting transparently proxied HTTP connections at 0.0.0.0, port 3182, FD 18.
 2009/10/26 23:25:22| HTCP Disabled.
 2009/10/26 23:25:22| WCCP Disabled.
 2009/10/26 23:25:22| Ready to serve requests.
 2009/10/26 23:25:22| WARNING: url_rewriter #1 (FD 7) exited
 2009/10/26 23:25:22| Done reading /var/spool/squid swaplog (0 entries)
 2009/10/26 23:25:22| Finished rebuilding storage from disk.
 2009/10/26 23:25:22|         0 Entries scanned
 2009/10/26 23:25:22|         0 Invalid entries.
 2009/10/26 23:25:22|         0 With invalid flags.
 2009/10/26 23:25:22|         0 Objects loaded.
 2009/10/26 23:25:22|         0 Objects expired.
 2009/10/26 23:25:22|         0 Objects cancelled.
 2009/10/26 23:25:22|         0 Duplicate URLs purged.
 2009/10/26 23:25:22|         0 Swapfile clashes avoided.
 2009/10/26 23:25:22|   Took 0.1 seconds (   0.0 objects/sec).
 2009/10/26 23:25:22| Beginning Validation Procedure
 2009/10/26 23:25:22|   Completed Validation Procedure
 2009/10/26 23:25:22|   Validated 0 Entries
 2009/10/26 23:25:22|   store_swap_size = 0k
 2009/10/26 23:25:22| WARNING: url_rewriter #3 (FD 9) exited
 2009/10/26 23:25:22| WARNING: url_rewriter #2 (FD 8) exited
 2009/10/26 23:25:22| Too few url_rewriter processes are running
 2009/10/26 23:25:22| storeDirWriteCleanLogs: Starting...
 2009/10/26 23:25:22|   Finished.  Wrote 0 entries.
 2009/10/26 23:25:22|   Took 0.0 seconds (   0.0 entries/sec).
 FATAL: The url_rewriter helpers are crashing too rapidly, need help!
 
 Aborted

```I'm running Ubuntu 9.04 on kernel 2.6.28-16-generic
squid and squidGuard both came from the standard apt-get repositories.
This configuration was running until I updated one of the destinations in squidGuard.

Can someone point me in the right direction to fix this.
Thanks

P.S.  If more information is need about my config I can post that too.

---

### Post by spydr98 on 2009-10-27
<bump>


Any help?

---

### Post by spydr98 on 2009-10-29
This is what I've done so far.

squidGuard with all the only rule as default and no destination groups defined and pass ALL (or !ALL) works just fine.
squidGuard with just one destination group, test, and one domain entry test.com causes squid to die with the error url redirectors are dieing.  squidGuard test on it's own are fine.

Next I did a "apt-get purge squid squidGuard" and then I deleted any directories for squid and squidGuard left behind and deleted the sqiud.conf left behind.  I then re-installed squid and squidGuard "apt-get install squid squidGuard", did up a new config and squid still dies when I try to use squidGuard as the redirector with any destination groups defined.

Any help at all?

---

### Post by silence444 on 2009-12-14
Hi there. don't know if you got it sorted out but usually its a permissions issue.
On my server, once i have run the 'sudo squidGuard -C all', i have to run 'sudo chown -R proxy: proxy /var/lib/squidguard/db' ,  and then 'sudo chmod -R 777 /var/lib/squidguard/db'.

then i can start squid and it works
Hope this helps

regards,
Adrian

---

