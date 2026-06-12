---
title: "rx_over_errors means what?"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by fuzzyworbles on 2011-07-28
Hi,

I've recently got gigabit piped from my imac to linux box. Everything is gigabit compliant: gigabit nics, cat6 and gigabit switch. After some trivial tweaking, I've gotten ~570mbit tx and 288mbit rx (relative to the linux box). 

I suspect the slowdown is related to the high number of "rx_over_errors" as shown by ethtool. My question for anybody who knows is: What in the blazes is an "rx_over" error? Exhaustive google and forum searches have turned up nothing. 

The only clue I have is that this error might be related a frame error and not overruns, as ifconfig shows an equal number of frame errors as ethtool shows "rx_over_errors." HOWEVER, ethtool shows no frame errors. Also, judging from the other ethtool output, "rx_over_errors" is not the same as a frame length error, as there is a specific field for that error. 

-Thanks

---

### Post by jmoorse on 2011-08-01
This is likely an 'overrun' error.  Does ifconfig show any overruns or just framing errors?

Overruns are not related to frame size, but rather the inability of the RX hardware to keep up with the TX stream.

Can you post the output including the ethtool command you ran?

Also, what does the following output show:

```

sudo ethtool -S [adapter]

```

---

### Post by fuzzyworbles on 2011-08-01
```
     tx_bytes: 8981223237
     tx_zero_rexmt: 52540499
     tx_one_rexmt: 0
     tx_many_rexmt: 0
     tx_late_collision: 0
     tx_fifo_errors: 0
     tx_carrier_errors: 0
     tx_excess_deferral: 0
     tx_retry_error: 0
     rx_frame_error: 0
     rx_extra_byte: 0
     rx_late_collision: 0
     rx_runt: 0
     rx_frame_too_long: 0
     rx_over_errors: 45637
     rx_crc_errors: 0
     rx_frame_align_error: 0
     rx_length_error: 0
     rx_unicast: 74731071
     rx_multicast: 9513
     rx_broadcast: 5814
     rx_packets: 74746398
     rx_errors_total: 45637
     tx_errors_total: 0
     tx_deferral: 0
     tx_packets: 52540499
     rx_bytes: 76998702487
     tx_pause: 99326
     rx_pause: 4
     rx_drop_frame: 497

```

My reasoning for not thinking "rx_over_error" is an overrun because 1) ifconfig says there are no overruns, but thinks it's a frame error:

```
eth1      Link encap:Ethernet  HWaddr 00:04:4b:11:22:33
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:74797253 errors:45637 dropped:0 overruns:0 frame:45637
          TX packets:52596245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3000
          RX bytes:76658031534 (76.6 GB)  TX bytes:9011899364 (9.0 GB)
          Interrupt:43 Base address:0x2000

```

yet as seen in the ethtool stats, there are no frame errors. And 2) tx and rx flow-control is enabled on both the server (linux) and client (os x). That flow control on linux is telling os x to slow it's roll is evident by the ethtool stats output above; rx_pause shows activity.

Is it possible that either ethtool or ifconfig are lying?

---

### Post by jmoorse on 2011-08-01
There are a couple of possibilities here:

1. To me framing errors, regardless of type, are almost always a hardware issue.  Can you try different ports on the switch or a direct xover connection to rule this out?

2. Are you sure that the ethernet driver is correct on the Ubuntu box?  If not, or if it is a crappy driver it could help cause this slower throughput.

3. Also, I noticed your txquelen is 3k, have you made any modifications to this or changed anything else in ethtool or in the proc dir?

4. Can you also post the output of sudo ethtool -k eth1?  I have seen LRO cause issues in certain circumstances.

Are you generating the traffic tests with iperf?  If so, can you share the parameters you are using?

---

### Post by fuzzyworbles on 2011-08-02
1. I have tried different ports on the switch with no difference, but have't tried by-passing the switch (reason: laziness)

2. I don't know of any other driver I could use than forcedeth. It's an on-board nVidia MCP73.

3. increasing the tx queue was an attempt to affect the *tx* speed. no change, and unrelated anyway.

4. all nic offloading is completely disabled. by default, GRO is enabled, but that slowed down things in both directions considerably, so that was disabled long ago.

5. iperf was one of the first things i did when looking for the bottleneck. tx and rx both get ~88MB/sec. rx_over_errors are exhibited, too. NFS sends from the linux box at ~77MB/sec which is expected, but receives at ~25MB/sec. dd test shows write speed at 108MB/sec, however, so i've ruled out sata. 

I'm 90% sure that either gigabit functionality or the sending imac is to blame because the linux box receives data from various computers including the router on a 100mbit link through the same switch and same port on the linux box and errors NEVER EVER increase unless the mac is sending data. i have no other gigabit devices to test in order to rule-out the mac.

finally, tcp tuning through sysctl.conf on both machines have been tried stock and modded, yielding only improved overall performance, but same error rate.

if i could just find some documentation on "rx_over_errors," i could figure out how to fix this. i say "could" because it might not even be the source of the rx slowdown, as iperf receives at 88MB/sec notwithstanding climbing rx_over_errors while iperf testing (i.e., slowdown only when using ftp/cifs/nfs/etc).

seeing how i've just talked myself into blaming the mac, here are the tcp tweaks i've made in case somebody wishes to ignore that this is a linux forum:

```
kern.ipc.maxsockbuf=800000
net.inet.tcp.delayed_ack=0
net.inet.tcp.mssdflt=1460
net.inet.tcp.sendspace=400000
net.inet.tcp.recvspace=400000
net.inet.tcp.rfc1323=1
```

my understanding is that Unix's tcp.send/recvspace is the same as linux's net.core.w/rmax. linux's buffers are set much larger than the mac's.. soo.. i don't think that's it either. any other thoughts? i appreciate your and others' input.

---

### Post by jmoorse on 2011-08-02
It looks like you have done your due diligence.  Those "BSD" parameters look fine.

Perhaps boot the iMac to a Ubuntu LiveCD and see if the issue re-occurs?

---

### Post by fuzzyworbles on 2011-08-02
Good idea. I booted w/ a ubuntu live cd, and got the same rx_over_errors on the linux box when sending data from the ubuntu-booted imac.

doing some more googling, i stumbled across a comment in some code for a different ethernet module. it labeled rx_over_errors as "ring buffer error." so i checked ethtool and got:```
Ring parameters for eth1:
Pre-set maximums:
RX:        16384
RX Mini:    0
RX Jumbo:    0
TX:        16384
Current hardware settings:
RX:        16384
RX Mini:    0
RX Jumbo:    0
TX:        256

``` i increased the current rx to the pre-set maximum, but with no effect, however. when i return, i'll see if i can increase it over the pre-set maximum.

---

