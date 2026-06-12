---
title: "DNS Resolution Problem(?) / Websites are SLOW"
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by KrisDouglas on 2012-01-04
**Solution Below**

Hello, 

I am experiencing a problem with my machine at the moment which is driving me insane :)

Basically, I have an xubuntu 11.10 AMD64 machine, it has been working perfectly for ages. Yesterday there was a powercut, I rebooted my machine after and it all came back on absolutely fine.

Next thing I know, web pages are loading ridiculously slowly in Chrome, Firefox and Chromium. 

So I thought there was something wrong with the network. I booted up my Windows 7 VirtualBox guest, and boom, pages load fine on that machine. Still slow on my Ubuntu Box.

So I thought, maybe it's something to do with the DNS, changed to Google's DNS, OpenDNS and a couple of others and the problem was not resolved. Now I have a question mark in the title of this thread because I don't think it's actually the DNS, I can resolve hostnames to IP addresses fine using the dig command, and it works very quickly. Whereas in Lynx, Chromium and Firefox is honorificly slow. 

I have checked all my settings, and I was used to a while ago having to disable IPV6, I did that, to no avail. 

I have asked on the IRC and was helped by a couple of people running diagnostics, and little came of it. 

I would really appreciate some help/input. I'm sorry this post is so long :)

--- **Solution** ---

Well, it's solved. I have never ever had this problem before.

I checked my /etc/nsswitch.conf file to see if there were any errors...

```

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

```

Within that line, "wins" is mentioned. A samba tool for resolving Windows network names. 

I removed that from the file:

```

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```

System is back to normal, other than the fact I have to remember IPs of Windows machines now. How messed up is that :(

---

### Post by spacecheck on 2012-01-04
How are you connected to the web? Router? DSL or Cable modem? They will both have also suffered the same power cut (unless tied to a UPS). Try a reboot of these, to see if the problem is resolved (first the dsl/cable modem, then when they are stable, restart the router).

Good luck!

---

### Post by KrisDouglas on 2012-01-04
Hello, thanks for the reply, sorry if I didn't make it clear.

It's a bonded ADSL2 line synced at about 32meg

All of the router equipment is functioning fine, we have a PFSense box which is functioning perfectly. 

There are 20+ windows 7 PC's on the network (I'm one of the sysadmins) and they are all working perfectly.

---

### Post by kforum on 2012-01-04
i had similar problems with my router, specially when stressed, till i did this: [http://ubuntuforums.org/showthread.php?t=1900140](http://ubuntuforums.org/showthread.php?t=1900140)

best of luck!

---

### Post by spacecheck on 2012-01-04
Yeah, I overlooked it working fine under Win7, too. That's ok, sysads are people, too! ;-)

Did the cache files for these browsers perhaps get corrupted by the outage? Might clearing the cache help?

Good kuck!

---

### Post by KrisDouglas on 2012-01-04
> **spacecheck said:**
> Yeah, I overlooked it working fine under Win7, too. That's ok, sysads are people, too! ;-)

Did the cache files for these browsers perhaps get corrupted by the outage? Might clearing the cache help?

Good kuck!

Thanks for your reply again :)

I have reset the profiles on Firefox and Chromium (I haven't used chrome before.) As for Lynx, that has a cache?

Progress so far: Nil.

---

### Post by spacecheck on 2012-01-04
In order to ensure it is related to DNS, you should perhaps try pinging a few of the sites to get their IP addresses (and response times) then ping just the IP addresses, to see if the response is faster. Then, see if they respond just as slowly using the IP address in the browser. This effort would not rely upon DNS resolution, so if still responding slowly, it may be an entirely different problem altogether.  

Good luck!

---

### Post by KrisDouglas on 2012-01-05
IP addresses resolve directly perfectly, makes me lean towards the DNS issue again.

Ping holds for about 10-30 seconds before showing results. The ping result itself is very good, but the initial time to resolve the name takes a long time.

Pinging an IP instantly returns identical results as above, without the delay obviously.

---

### Post by KrisDouglas on 2012-01-05
I have just gone through the update information on my PC. It seems that the only update between those reboots was one to binutils, hardly something that would impede DNS resolution.

---

### Post by chili555 on 2012-01-05
In order to narrow the search, I suggest namebench: [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

It's in the repos:```
sudo apt-get install namebench
```Then just run it from the terminal and it's pretty much self-explanatory.

---

### Post by KrisDouglas on 2012-01-05
I am presently running a benchmark.

I will post results here.

Thank you very much :)

---

### Post by KrisDouglas on 2012-01-05
Ok, I have completed the DNS benchmark.

What an awesome application is my first note. However, I changed to a name server which was supposedly "75% faster" and it's not solved the problem.

I have loaded the results onto my site:

[http://krisd.eu/namebench_2012-01-05_1705.html](http://krisd.eu/namebench_2012-01-05_1705.html)

Resolv.conf
```

kris@kris-pc:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 194.73.82.242
nameserver 10.10.8.2 #This is my office server, it's basically caching results and forwarding OpenDNS
nameserver 194.74.65.69

```
 
*sad face*

---

### Post by spacecheck on 2012-01-05
If I understand correctly, you have xx Windows systems operating without problems and you have an alternative Linux responding properly in a VM, all attached to the office router.
Can you compare functional settings against those in the dysfunctional system?
Which DNS-servers are being used by the functional systems? Are the functional DNS-server addresses being automatically delivered per stand-alone DHCP-server, or directly by router's DHCP-server?
Is your defective box manually set to use specified DNS-servers, or is it set to automatically pull the same DNS-servers as the functional systems, via DHCP? If the latter & if pulling from a stand-alone DHCP server, has the (windows?) DHCP server been trained to give your linux box the data?
Have you made any manual routing entries? Might there be old, undeleted proxy entries?

---

### Post by KrisDouglas on 2012-01-06
> **spacecheck said:**
> If I understand correctly, you have xx Windows systems operating without problems and you have an alternative Linux responding properly in a VM, all attached to the office router.
Can you compare functional settings against those in the dysfunctional system?
Which DNS-servers are being used by the functional systems? Are the functional DNS-server addresses being automatically delivered per stand-alone DHCP-server, or directly by router's DHCP-server?
Is your defective box manually set to use specified DNS-servers, or is it set to automatically pull the same DNS-servers as the functional systems, via DHCP? If the latter & if pulling from a stand-alone DHCP server, has the (windows?) DHCP server been trained to give your linux box the data?
Have you made any manual routing entries? Might there be old, undeleted proxy entries?

My desktop PC at my office is a Linux box, with one windows 7 VM. Windows 7 is working fine, Linux is not. 

The Windows DHCP server is working perfectly and there are no address conflicts. This system has been working for almost 2 years (with reinstalls). Just now it has started to have a problem. 

As in the posts above, I have manual DNS servers set, but have tried getting them automatically from the DHCP as with the Windows VM to no avail. 

Any proxy server details have been cleared out from the system in an effort to sort this problem, but none were in use at the time. 

Thanks :)

---

### Post by spacecheck on 2012-01-06
There remains an additional consideration, which could apply only to the one Linux system having the problem. The browser. Have you installed any plug-ins, extensions or add-ins ? If so, disable them and see if the problem remains.

Good luck!

---

### Post by KrisDouglas on 2012-01-09
Well, it's solved. I have never ever had this problem before.

I checked my /etc/nsswitch.conf file to see if there were any errors...

```

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

```

Within that line, "wins" is mentioned. A samba tool for resolving Windows network names. 

I removed that from the file:

```

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```

System is back to normal, other than the fact I have to remember IPs of Windows machines now. How messed up is that :(

---

### Post by spacecheck on 2012-01-09
Did you try simply changing the position a la "first come, first served", i.e putting WINS last, to see if the results are better than havng WINS resolution first in line?

Might be worth a try and solve both problems. Let us know. If so, you'd probably want to mark it solved. 

Good Luck!

---

### Post by chili555 on 2012-01-09
> I have to remember IPs of Windows machines now. How messed up is thatIf they are static, can you load them in to /etc/hosts?```
127.0.0.1	localhost
127.0.1.1	MYBOX
192.168.1.105   windows1
192.168.1.108   windows2
etc.

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

---

### Post by spectraphysics on 2012-01-10
> **spacecheck said:**
> Did you try simply changing the position a la "first come, first served", i.e putting WINS last, to see if the results are better than havng WINS resolution first in line?

Might be worth a try and solve both problems. Let us know. If so, you'd probably want to mark it solved. 

Good Luck!


I was having this same problem as OP and found this thread. I modified my nsswitch.conf file in the order you suggest... "dns mdns4 wins" and found you were right.  DNS now resolves quickly AND I can still browse Windows networks without knowing the IPs.  Thanks!

---

### Post by spacecheck on 2012-01-11
> **spectraphysics said:**
> I was having this same problem as OP and found this thread. I modified my nsswitch.conf file in the order you suggest... "dns mdns4 wins" and found you were right.  DNS now resolves quickly AND I can still browse Windows networks without knowing the IPs.  Thanks!

Great! Glad to learn it worked! Hopefully it also solves KrisDouglas' problem remembering IPs. ;-)

Have fun!

---

### Post by sharkey77 on 2012-04-26
Not solved for me:

I've turned off IP6
modified nsswitch.conf, resolv.conf, NetworkManager.conf, dhclient.conf all to no avail.

Timeouts, slow connections, this computer works fine with Windows 7.






```
eth0      Link encap:Ethernet  HWaddr d4:be:d9:bc:23:48  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::d6be:d9ff:febc:2348/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36241 errors:0 dropped:36241 overruns:0 frame:36241
          TX packets:33081 errors:0 dropped:349 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45090932 (45.0 MB)  TX bytes:5788785 (5.7 MB)
          Interrupt:43 Base address:0xc000 



03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Dell Device [1028:04ed]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 43
	Region 0: I/O ports at e000 [size=256]
	Region 2: Memory at d0004000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at d0000000 (64-bit, prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169
```

---

### Post by sharkey77 on 2012-04-26
I will try this and report back;

[http://amk1.wordpress.com/2009/06/09/realtek-8168-module-issue/](http://amk1.wordpress.com/2009/06/09/realtek-8168-module-issue/)

---

### Post by sharkey77 on 2012-04-26
Now I have no ethernet.  That was a fail.

FATAL: Module r8168 not found

---

