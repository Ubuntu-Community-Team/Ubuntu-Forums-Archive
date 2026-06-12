---
title: "Squid choking connection"
date: 2012-09-12
forum: Networking &amp; Wireless
---

### Post by NeilCotton on 2012-09-12
Hi all, 
We are having a problem with traffic passing through our Squid proxy server, where by it is reducing the bandwidth of clients passing through it to 10% of that of clients NOT passing through it's proxy.
 
The ONLY function of this is URL filtering. There is no user management, reporting, bandwidth allocation etc on this. The server isn't used for anything else.
 
I've been through pretty much everything, and can't see any reason why this may be like this. We were not having any problems with this before summer. (PS. We are a high school). The squid proxy is only applied to student profiles. Some flash heavy sites are just not functioning at all (on a vast majority of instances), but they are not binary failures (hardware/software), because it is completely intermittant (just majority of instances are failing)
 
_**ADMISSION**_
I know very little about it, but I know that 95% of the config is completely default. I administer the squid remotely through Webmin GUI interface. My unix skills are very limited/near non existant.
 
_**NOT NETWORKING**_
This isn't a topographical network issue, as logging on to a machine and diverting the http requests directly to DG gets the speed back to normal.
 
_**CHANGES**_
The only change I made was to switch the eth0 from static to reserved DHCP. Same address, same physical port, same port/vlan config.
 
**System : Webmin 1.510 | Squid 2.7 | ~800 Users | ~200 Consecutive Users max | ~120 Consecutive Users norm**
 
If anyone has ANY IDEA of something I can check, or ammend, please let me know.
 
Your time and expertise is greatly appreciated.
 
Have a good day all. ):P
 
*Many regards*
***Neil Cotton***

---

