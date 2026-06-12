---
title: "Unusual network performance issues at smaller TCP window sizes"
date: 2013-05-08
forum: Networking &amp; Wireless
---

### Post by Wardrop on 2013-05-08
Hi All,

I'm hoping someone can shed some light on this bizarre issue we're experiencing. We've been experiencing slow network speeds between our Windows SQL servers and Ubuntu 12.04 application servers. Upon investigating with iperf, we found once the window size got down to 8k, performance dropped off extremely steeply, going from about 400Mbit/s at 9k window size, to about 10Mbit/s at 8k and under. I've observed a couple of weird things which may help identify the problem:


[LIST=1]
[*]The beginning of the iperf test (first second or so) runs at the expected 400Mbit/s, but after that drops to about 10Mbit/s for the remainder of the test, as if some kind of buffer filled out and refuses to flush properly.
[*]If `tcpdump -ni eth0` is running while the test is performed, network speed remains at 400Mbit/s+ for the duration of the test, even at 8k and under. Running tcpdump seems to improve network performance in general for any network transfers involving packets smaller than 128k. Is tcpdump flushing some kind of buffer?
[/LIST]

So what is going on here? Why does network performance drop off so sharply at 8k, and why does running tcpdump fix the problem. More importantly though, how do I fix this as it's killing our SQL performance.

Thanks

---

### Post by Wardrop on 2013-05-09
No one has any suggestions?

---

### Post by Doug S on 2013-05-09
Actually, I have been doing iperf tests off and on since your original posting, working towards trying to give some sort of reply.
It makes complete sense to me that net throughput would go down for small window sizes (buffer sizes), as there will end being more overhead packets and such.
For large window sizes, I got less than 1/3 of the total number of packets and a considerably higher percentage of payload packets, than for extremely small window sizes but the same amount of payload bytes sent.
Also, the payload packets per second were higher for the large window sizes. That is pretty much what I expected. I was not able to get as low as you though, and my maximum was also much higher than yours.

Oh, by the way tcpdump running or not didn't make any difference for my tests. However, I was mostly running tcpdump so I could count packets and times between packets, afterwards. Perhaps in your case tcpdump was adding some more buffering somewhere.

It is not clear to me that it is valid to compare iperf results with your actual senario. I wonder if increased buffering would help your case? If mysql server were running on ubuntu, I would suggest changes to the config files. Since yours is on windows, I don't know what to suggest. (actually, I know very little about MySQL anyhow.)

I realize my reply is not much help.

---

### Post by tgalati4 on 2013-05-09
Perhaps the routers have rate-limiting to improve Quality-of-Service (QoS).  Check the firmware of the routers and see if any custom policy has been set.  Since you are running Windows servers, I assume this is some sort of corporate environment, which means you probably have VOIP and video conferencing services running on the same LAN.  With QoS, other high-bandwidth requests (such as your SQL queries and iperf packets) will get pushed down so that voice and video can get through.

---

### Post by Wardrop on 2013-05-10
Thanks for the replies guys.

This is indeed a corporate network, and the SQL server is actually Microsoft SQL, not MySQL. I've tried iperf between the SQL servers are other Windows application servers on the same virtual hosts as the Ubuntu VM's, and they do not exhibit the same dramatic drop in network traffic. I think the fact that running `tcpdump` improves performance pretty much rules out any of the network infrastructure in-between. It does seem like some kind of buffer issue that `tcpdump` is somehow remedying by flushing it or something weird. I've already tweaked buffer sizes and such, but nothing's changed. 

Given that it's a virtual machine, I might try cloning it perhaps to my local workstation or some other server to see if anything changes. Also not that I've tried running iperf on the loopback and that seemed to run at the speed you'd expect (20Gbit/s).

---

### Post by Doug S on 2013-05-10
Oh..., the original posting didn't mention virtual machines. My tests were done on two real ubuntu 12.04.2 servers on a gigabit LAN and a single gigabit switch between the two, and the rest of the LAN was fairly quiet at the time.
I got 926 Mega Bits per second maximum, with very large window sizes, and ~50 Megabits per second minimum, with extremely small window sizes.

---

### Post by tgalati4 on 2013-05-10
If you are running virtual machines, what is the hypervisor being used?  This now looks like a hypervisor problem, not a network or SQL problem.  Unless you are running a single linux instance on bare metal, it's hard to pinpoint throughput issues without looking at IOWaits at the hypervisor level.

---

### Post by Doug S on 2013-05-10
O.K. when I run tcpdump on virtual machine doing these tests, I do see a significant improvement. As mentioned before, I still think due to some extra buffering when tcpdump is inserted in the chain of events.

Detail: One end of iperf test was a real 12.04 Ubuntu server; The other end was a virtual 12.04 server running on the first mentioned server.

Test 1: Large window sizes, no tcpdump running:```
doug@virt64-02:~$ [COLOR=#ff0000]iperf -s -w 1M[/COLOR]
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size:  256 KByte (WARNING: requested 1.00 MByte)
------------------------------------------------------------
[  4] local 192.168.122.250 port 5001 connected with 192.168.122.1 port 60017
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-60.0 sec  40.8 GBytes  [COLOR=#ff0000]5.85 Gbits/sec[/COLOR]
``````
doug@s15:~$ [COLOR=#ff0000]iperf -c 192.168.122.250 -w 1024k -t 60[/COLOR]
------------------------------------------------------------
Client connecting to 192.168.122.250, TCP port 5001
TCP window size:  256 KByte (WARNING: requested 1.00 MByte)
------------------------------------------------------------
[  3] local 192.168.122.1 port 60017 connected with 192.168.122.250 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-60.0 sec  40.8 GBytes  [COLOR=#ff0000]5.85 Gbits/sec[/COLOR]
```

Test 2: Small window sizes, no tcpdump running:```
doug@virt64-02:~$ [COLOR=#ff0000]iperf -s -w 1k[/COLOR]
WARNING: TCP window size set to 1024 bytes. A small window size
will give poor performance. See the Iperf documentation.
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 2.23 KByte (WARNING: requested 1.00 KByte)
------------------------------------------------------------
[  4] local 192.168.122.250 port 5001 connected with 192.168.122.1 port 60015
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-60.0 sec   326 MBytes[COLOR=#ff0000]  45.5 Mbits/sec[/COLOR]
``````
doug@s15:~$ [COLOR=#ff0000]iperf -c 192.168.122.250 -w 1k -t 60[/COLOR]
WARNING: TCP window size set to 1024 bytes. A small window size
will give poor performance. See the Iperf documentation.
------------------------------------------------------------
Client connecting to 192.168.122.250, TCP port 5001
TCP window size: 2.00 KByte (WARNING: requested 1.00 KByte)
------------------------------------------------------------
[  3] local 192.168.122.1 port 60015 connected with 192.168.122.250 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-60.0 sec   326 MBytes  [COLOR=#ff0000]45.5 Mbits/sec[/COLOR]

```Test 3: Small window sizes, tcpdump running:```
doug@virt64-02:~$ [COLOR=#ff0000]iperf -s -w 1k[/COLOR]
``````
doug@virt64-02:~$ [COLOR=#ff0000]sudo tcpdump -n -nn -tttt -i eth0 port 5001 > /dev/null[/COLOR]
``````
doug@s15:~$ [COLOR=#ff0000]iperf -c 192.168.122.250 -w 1k -i 2 -t 60[/COLOR]
WARNING: TCP window size set to 1024 bytes. A small window size
will give poor performance. See the Iperf documentation.
------------------------------------------------------------
Client connecting to 192.168.122.250, TCP port 5001
TCP window size: 2.00 KByte (WARNING: requested 1.00 KByte)
------------------------------------------------------------
[  3] local 192.168.122.1 port 60012 connected with 192.168.122.250 port 5001
[ ID] Interval       Transfer     Bandwidth
...
[  3]  0.0-60.0 sec   675 MBytes  [COLOR=#ff0000]94.4 Mbits/sec[/COLOR]
```

---

### Post by tgalati4 on 2013-05-10
So it looks like the default Ubuntu tcp stack accepts window sizes between 256KB and 2KB.  Anything larger or smaller will get set to their respective limit.  Although I didn't see anything in the *iperf* man page, the warning is that small windows will reduce performance.  More data needs to be taken between these two points (128KB, 64KB, 32KB) to determine if there is a steep drop off or if it is a linear relationship.  Again, with SQL queries, it shouldn't make a difference because the search time to assemble the query should be much larger than any network latency.

Don't forget to clear caches between searches or use unique searches each time, because everything gets cached to RAM which will make the repeated queries seem much faster than they really are.

---

### Post by Doug S on 2013-05-11
While perhaps of limited value towards the OP, here are some more data points, for the test setup I used in my previous post. Myself, I did not expect the benifit from running tcpdump to continue up the larger window sizes.
While iperf used CPU resources, on both the VM and the host, they never even nearly limited. KVM, however, always seemed to use around 160%. 

[ATTACH=CONFIG]242464[/ATTACH]

---

### Post by tgalati4 on 2013-05-11
Interesting.  Without tcpdump, it's almost linear.  With tcpdump there is quite an increase in throughput, which may or may not be real with an actual web application.  It's possible that tcpdump is acting as a dynamic buffer since all data is residing in RAM, at the expense of more bus traffic and CPU consumption.

I'm not familiar with the internals of* iperf*, but the default read buffer is 8KB, so that may be related to the performance drop off that the OP experienced.  It can be changed with the *-l 16* switch (16KB instead of 8KB).

---

### Post by Doug S on 2013-05-11
> **tgalati4 said:**
> ...but the default read buffer is 8KB, so that may be related to the performance drop off that the OP experienced.  It can be changed with the *-l 16* switch (16KB instead of 8KB).Ya, I know the man pages and such say the default is 8k, but I do not believe it. Why? Because then I would expect no difference between:```
 iperf -c 192.168.122.250 -w 128k -t 30
```and```
 iperf -c 192.168.122.250 -w 128k -l 8k -t 30
```but there is significant difference. I think the default buffer size is much larger.

---

### Post by Wardrop on 2013-05-12
Thanks for the time you've already put into this guys. Much appreciated.

@tgalati4 Generally, SQL queries are not affected a great deal, though I store BLOB data such as images in the database, in which case the slow down is very noticeable. Each ~4MB image takes at least 5 seconds to be served which is unacceptable.

I plan to do some further troubleshooting today. I want to clone or build another Ubuntu server, and try running it from various hosts to see what I get.

---

### Post by Wardrop on 2013-05-12
After trying another virtual NIC (VMware's E1000 NIC , as opposed to VMXNET3) which didn't seem to exhibit the same problem, a colleague found this article which resolves the issue: [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1027511](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1027511)

Pretty funny how one setting can increase performance by 10,000%.

Again, thanks for your help everyone.

---

