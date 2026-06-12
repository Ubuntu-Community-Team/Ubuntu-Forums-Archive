---
title: "&quot;Destination Host Unreachable&quot;"
date: 2006-05-26
forum: Networking &amp; Wireless
---

### Post by MrChonks on 2006-05-26
Yes, I too, have the nefarious "Destination Host Unreachable" error when pinging my gateway.  I just installed 6.06 after having the same issue with breezy, figuring that the newer release would resolve the issue.  Alas, not the case.  So, I went through the forum looking for threads related to the error and found a lot of troubleshooting steps to follow.  I ran through them, put the output on a floppy and brought it in to work so that I could pull it off and post it here.  Alas, no such luck as the disk is unreadable now.  ](*,) 

So, here is what I can remember from my troubleshooting.  Hopefully someone can help me figure out what is going on.

Static IP: 192.168.0.38
Netmask: 255.255.255.0
Gateway: 192.168.0.18
Broadcast: 192.168.0.255

When I run ifconfig eth0 it gives me the correct info + stating that the link is UP, but not running.

resolv.conf has the correct nameservers from comcast.

interfaces shows everything properly (i.e. auto lo, auto eth0, etc.)

I disabled ipv6 in modprobe.d/aliases and also renamed the ipv6.ko driver.

route hangs, but netstat -nr shows the proper gateway of 192.168.0.18.

arp -a hangs indefinitely.  When I do a ping on the gateway, it errors out stating "Destination host unreachable".

I did an lspci | grep Eth and it shows the correct Intel nic (e100).  Also, when I do lsmod | grep mii, it shows that the proper driver (e100) is loaded.

dmesg | grep eth0 does not show any errors.

I think I put in everything here that I had from the troubleshooting (just short of putting the actual data in here).  If you have any questions, let me know.  I would be happy to know your ideas.

Thanks,
Chonks

---

### Post by Iowan on 2006-05-26
What happens if you ping 192.168.0.38  (is the NIC enabled)?     Past that, might there be another hardware issue - bad/wrong cable, hub/switch, etc.?

---

### Post by MrChonks on 2006-05-26
I will have to try that when I get home at lunch, but as for the hardware issue, I know that there wasn't a problem a few nights ago when I installed hoary.  The network was fine and dandy there.  It only failed when I upgraded the dist to 5.10.  I am going to install 6.06 on a server here in the lab to see if I can replicate the issue and maybe get some logs on here.

---

### Post by MrChonks on 2006-05-28
I believe it was some sort of conflict with the on board intel nic.  I put in a four-port nic and it took it like a charm.

---

