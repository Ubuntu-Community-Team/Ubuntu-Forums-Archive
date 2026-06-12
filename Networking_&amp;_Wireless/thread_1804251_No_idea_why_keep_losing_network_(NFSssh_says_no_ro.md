---
title: "No idea why keep losing network (NFS/ssh says no route to host)"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by aspidistra on 2011-07-14
ubuntu 11.04 on both machines client and server
seems periodic -- seems to brown out and then come back

mount command I use is --- (to speed things up)

sudo mount 192.168.1.70:/home/dir /home/dan/mountdir -o rsize=32768,wsize=32768,intr,noatime

I also use ssh -4 now which I recall is ipv4 again to speed things up
problem was still extant with ipv6

but its dropping ..... 

any pointers anyone?  any idea where any network messages will be 
generated

---

### Post by varelov on 2011-07-14
No route to host means theres no such ip address. And if I got it correctly, you have only ip v 6 addresses on your nic's. If those addresses start with fe:: that means you have no real ip v 4 dhcp that will assign addresses to your nic's. Provided you have dhcp on your network.
I would check basic connectivity of those boxes with their dhcp server and do other basic connectivity diagnostics before plunging into nfs.

---

### Post by aspidistra on 2011-07-14
> **varelov said:**
> No route to host means theres no such ip address. And if I got it correctly, you have only ip v 6 addresses on your nic's. If those addresses start with fe:: that means you have no real ip v 4 dhcp that will assign addresses to your nic's. Provided you have dhcp on your network.
I would check basic connectivity of those boxes with their dhcp server and do other basic connectivity diagnostics before plunging into nfs.

They do have fe:: in front of them.  But ssh -4 does speed ssh up I was told it would.  The connectivity is wireless how would I check basic connectivity.  The network just seems to drop intermittently -- maybe it is hardware/interference -- but both machines never lose their internet connection.  I am currently setting up another connection from client as server to the server (just NFS) going both way -- won't take long -- just to check.  Never had network issues before.  Is it 11.04?  Never had this with 10.04 to 10.04.  Problems I am having have only arisen with 
11.04 (co-incidentally).  It's the 64 bit version.

---

### Post by varelov on 2011-07-14
So, right-click on a connection and choose "Connection Information" and notice what it will tell you. Is the fe:: address the only address you are getting for your network interfaces? No dotted IPv4 addresses?
You check basic connectivity by pinging network addresses, that's for starters. Let's put ssh and NFS on side for now since you may have more pressing problems to solve. If you can't ping your server and/or each machine in the network, you can't expect ssh, NFS or any other network service to work.
Fire up Terminal and start testing with ping.

---

### Post by aspidistra on 2011-07-15
> **varelov said:**
> So, right-click on a connection and choose "Connection Information" and notice what it will tell you. Is the fe:: address the only address you are getting for your network interfaces? No dotted IPv4 addresses?
You check basic connectivity by pinging network addresses, that's for starters. Let's put ssh and NFS on side for now since you may have more pressing problems to solve. If you can't ping your server and/or each machine in the network, you can't expect ssh, NFS or any other network service to work.
Fire up Terminal and start testing with ping.

I've attached that information -- ifconfig information
and network ping --- I ran a few ping sets

network ping shows some packet loss - Is that causing the problem. Booted up client this morning   ssh name@server 

got:

ssh: connect to host main port 22: No route to host

some minutes later was back up.

The ifconfig information / ping information was after the cxn was backup (obviously).  Puzzled.  Never had network problems before.  

I have a number of wireless dongles I think the Belkin one is on there -- generally use netgear fully compatible/Belkin.  There is a newer one kicking round somewhere.  Can't believe a wireless dongle would be the problem when the cxn is running at full speed anyway.  Would have thought internal network was minimal bandwidth.  I can supply information right away.  

In the "network information" ipv6 ignored I think is because I set the ssh configuration  to permanently provide the ssh -4 option (ipv4) which has speeded up my ssh.  The problem existed before I set that.


Thanks

---

### Post by aspidistra on 2011-07-17
Few days later.  

Have done nothing but replace wireless dongle

now using long shielded cable away from machine dangling in open air.  -- new dongle has got a long antennae on it

no failures since

must have been wireless signal problems.  Sorry to bother.

---

