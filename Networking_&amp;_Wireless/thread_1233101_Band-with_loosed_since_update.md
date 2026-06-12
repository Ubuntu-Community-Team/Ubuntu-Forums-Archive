---
title: "Band-with loosed since update"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by goldead on 2009-08-06
Hello,
 
 I'm using Ubuntu jaunty since a couple of weeks. Ufortunatly i now face a problem
 
 Since an update of some of the system's files two weeks ago i've loosed close to 75 % of my band-width. While update with update-manager are done at full speed download with bittorrent or firefox are slow down at just 25 % of the band-width.
 
 Can someone explain me why ?
 Can you also tell me what are the protocol and port used by download manager ?
 
 Here some network infos :
 
 ifconfig
 ```
wlan0     Link encap:Ethernet  HWaddr 00:08:d3:3b:c5:ef  
           inet adr:78.251.236.245  Bcast:78.251.255.255  Masque:255.255.128.0
           adr inet6: fe80::208:d3ff:fe3b:c5ef/64 Scope:Lien
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           Packets reçus:1183560 erreurs:0 :0 overruns:0 frame:0
           TX packets:1308462 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 lg file transmission:1000 
           Octets reçus:868666326 (868.6 MB) Octets transmis:379510116 (379.5 MB)
``` iwconfig
 ```
wlan0     IEEE 802.11bg  ESSID:"FreeWifi"  
           Mode:Managed  Frequency:2.412 GHz  Access Point: 46:1F:BB:08:B9:12   
           Bit Rate=5.5 Mb/s   Tx-Power=4 dBm   
           Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
           Power Management:off
           Link Quality=66/100  Signal level:-62 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``` iptables -L
 ```
Chain INPUT (policy ACCEPT)
 target     prot opt source               destination         
 
 Chain FORWARD (policy ACCEPT)
 target     prot opt source               destination         
 
 Chain OUTPUT (policy ACCEPT)
 target     prot opt source               destination
``` contain of /etc/hosts :
 ```
127.0.0.1 localhost
 127.0.1.1 ARCHI
 
 # The following lines are desirable for IPv6 capable hosts
 ::1 ip6-localhost ip6-loopback
 fe00::0 ip6-localnet
 ff00::0 ip6-mcastprefix
 ff02::1 ip6-allnodes
 ff02::2 ip6-allrouters
 ff02::3 ip6-allhosts
``` Thanx in advance :D

---

### Post by superprash2003 on 2009-08-06
try disabling ipv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by goldead on 2009-08-06
Thanx to reply,

I've allready tryed to disabled ipv6 but i didn't see any improvement since it also made transmission bittorrent software buggy i wen't back to ipv6 enabled.

Anyway i will try your way of disabling ipv6.

---

### Post by goldead on 2009-08-06
Did the change to disable ipv6, after done i've rebooted... but still the same s@*t.

---

### Post by broquea on 2009-08-06
That's because disabling IPv6 has nothing to do with IPv4 throughput, and everyone really needs to stop thinking that is a valid fix.

Have you contacted your actual provider to see if they have noticed any degradation in service, or changes on their side? I remember when Speakeasy changed from using MCI to Covad for last mile provisioning of DSL, I lost my 1.5/1.5 and ended up with 768/256 without any notification of that change (until I called and complained).

---

### Post by lisati on 2009-08-06
<aside>
Apologies if this sounds like the grammar police are stepping in, please don't be offended.
"Loosed" says to me that bandwidth has improved (in the sense "let loose") "Lost" might be a better word to use in the context of this thread.
Back to reading what has already been said so we can keep focus on helping the OP.
</aside>

---

### Post by doas777 on 2009-08-06
have you rebooted the upstream devices (router/cable/dsl modem)? keep them unplugged for at least 60 seconds, so the capacitors clear, and the memory contents degrade naturally.

these look a bit off. power seems low and signal seems too low. no idea what to do about it. do you have any analog RF devices that may be interfering?
> Tx-Power=4 dBm   
           Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
           Power Management:off
           Link Quality=66/100  Signal level:-62 dBm  


---

### Post by goldead on 2009-08-07
hello guys,

broquea i'm using a free wifi connection so i can't complain at any provider.

lisati english isn't my mother tongue so thanx for the grammar correction... if i don't improve my band-width at least i improve my english :D

doas 777 i did reboot, the computer was even off all night and no positive change.

What i really don't understand if you put away the signal quality or the provider side is why download via update-notifier or synaptic are still done at full speed and others ways not.

---

### Post by Rich_B_uk on 2009-08-07
Hmm, a lot of variables here. If you have the resources I would simply pop in a LiveCD of 8.04 and do some benchmarks with that. You need to pin down that it's definitely an update causing your issues.

Edit: Also, I would have thought that updates are just done via vanilla HTTP/80, but I see what you're getting at. Anyone confirm this?

---

### Post by goldead on 2009-08-07
hello Rich_B_uk,

don't have the 8.04 live cd only 9.04. can i do the benchmark with it and if yes can you give me a link to learn how.

THX

---

### Post by goldead on 2009-08-07
Strange thing just happened

While i was downloading a file under firefox at only 25 % of my band-width (as usual) i start downloading a .deb from sourceforge and it did used all the rest of the band-width. I mean that i was downloading at full speed.

Does ubuntu have a way to filter "non system files" and slow them down. I've done lots of tweaks (i can't even remember all of them) maybe i've done something wrong.

---

### Post by doas777 on 2009-08-07
usually that is a sign of one of two things: ISP whitelisting, or remote server bandwidth. I've only every gotten full bandwidth from my ISP when hitting sites on MS, Cannonical, Sun, Novel, and a few other big name Tech vendors sites. partly because the sites are well provisioned, and partly because the ISP trusts those sites.

---

### Post by goldead on 2009-08-07
do you know any trick to bypass this ?

---

### Post by doas777 on 2009-08-07
> **goldead said:**
> do you know any trick to bypass this ?

nope. that would be like asking water in a pipe to flow faster.

---

### Post by goldead on 2009-08-13
hello,

it seems that i've resolved this trouble by changing RWIN value like said in those explaination [http://swik.net/Ubuntu/Only+Ubuntu/How+to+Optimize+your+Internet+Connection+using+MTU+and+RWIN/cbnda](http://swik.net/Ubuntu/Only+Ubuntu/How+to+Optimize+your+Internet+Connection+using+MTU+and+RWIN/cbnda).

hope it'll work allways.

---

