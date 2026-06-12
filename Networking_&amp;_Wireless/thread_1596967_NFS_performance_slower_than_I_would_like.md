---
title: "NFS performance slower than I would like"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by annoyingrob on 2010-10-14
The setup in question consists of my server running 10.04, and my desktop running 10.10. The server exports an NFSv3 share which I have mounted on my desktop. Copying things to and from this share results in speeds roughly 30-35MB/s. I think it should be higher, something's limiting it. Ideally, I want to be seeing 70.

NFS is mounted with the following options:
```
intr,noatime,user,tcp,rsize=32768,wsize=32768
```
Playing around with tcp/udp, rsize, wsize, noatime, etc don't make any difference on performance.

The two machines are connected via a gigabit switch. Both network cards are running an MTU of 9000. Pinging a packet of 8972 confirms that jumbo frames can reach across the network unfragmented. Running iperf, I can achieve 600-700 megabit throughput between the two machines, so I don't think that the network is limiting it.

Testing by writing a bunch of zeros to the hard drive directly on the server:
```
dd if=/dev/zero of=test bs=16k count=32k
```
I can achieve roughly 70-85MB/sec write speed.

Testing the same command on my desktop over nfs (which points to the same folder as tested on the server), I only get 30-35MB/sec. Watching the network traffic, you can see it's quite "peaky". It will jump up to 600 mbits, then fall down to almost nothing, then jump up again, etc. Neither machines CPU or memory seems too terribly taxed when this happens either. Plenty of headroom on both machines. 

Edit: 

nfsstat also shows no retransmissions, so it's not that either.

Did some more tests reading back the data, 
```
dd if=test of=/dev/null
```
can achieve 80MB/sec locally, but only 40MB/sec across the network. The network graph shows a nice steady line around 400mbit though. Not fast, but steady.

Also tried upping rsize and wsize to 65536, and adding async. No difference. 

Any ideas what could be causing this loss in performance?

---

### Post by amauk on 2010-10-14
try adding "async" to the NFS options

I believe by default, NFS using synchronous transfers (meaning the next data packet is delayed until the server has flushed the last packet to disk)

async transfers should give you a significant speed increase over sync transfers, however if the server dies during a transfer, you'll have data lose

---

### Post by annoyingrob on 2010-10-15
Ha!

I didn't realize it was a server side option, I always thought async was a client side option. Well, I added that in, and now I'm getting about 65MB/sec transfer rates, I'm happy. 

Thanks!


On a side note, I tried it with iSCSI, and managed about 65MB/s too, so I'm happy that NFS could match that.

---

