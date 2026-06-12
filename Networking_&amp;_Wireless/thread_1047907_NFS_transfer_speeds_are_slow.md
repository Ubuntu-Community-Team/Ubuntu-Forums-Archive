---
title: "NFS transfer speeds are slow"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by e24ohm on 2009-01-22
Forum:
I am having a hard time with my NFS transfer speeds. I use the -o switch with the following, rsize=x,wsize=x. what should my numbers be? I thinkg nfs uses bytes for the read and write size, so do I try to convert the numbers to mbps  since my network 100 mbps CAT5. (have not upgraded to 1000mbps yet).

What should my numbers be, I came up with something like rsize=12500000,wsize=12500000, but i am not sure if this is right. The transfer speeds are still way to slow. I my win box blows past my nfs transfers, so i know i am doing something wrong.

any help will be great...

Cheers!!!
E

---

### Post by netztier on 2009-01-23
> **e24ohm said:**
> Forum:
I am having a hard time with my NFS transfer speeds. I use the -o switch with the following, rsize=x,wsize=x. what should my numbers be? 


Default for both is 8192 (8 kByte), which is ok for your common wired LAN. It means that one NFS read/write request will carry up to 8k of data. A full-sized NFS request will be transported as 6 ethernet frames of 1500bytes (max). 

On networks with high packet loss rates (such as WLANs), this becomes somewhat of a problem: if only one of the 6 ethernet frames is lost, the entire NFS request has to be repeated. In such networks, it helps to reduce this value to 1024, so an entire NFS request fits into a single ethernet/wireless frame; if a frame/packet is lost, only a single request will have to be repeated. 

So since ethernet is prone to the occasional packet loss by it's very nature, using large numbers has a limited benefit. A long while back, I did some tests and it turned out that using 32768 (32kBytes) for rsize and wsize gave slightly better performance - I used a 100mbps LAN then, with two switches, Debian as server and Ubuntu as client. Today, I have Ubuntu 8.04 as server and 8.10 as client, and a 1000Mbit/s LAN. The server hardware is old and so are it's IDE disks - still, I can get 20-30MByte/sec out of the old box.


But before diving into NFS tuning, please do a sanity check on your network: install **iPerf** from the universe repositories and run it from server to client and client to server. On a 100Mbps switched network, iPerf should report figures in the 93-95Mbit/s range.

This might seem redundant, but more than once I've been able to make out a full/half duplex problem, a cable problem or a slowly dying LAN switch (small packets at slow rates would work, but highspeed streams were terrible), and these need to be sorted out before taking care of NFS.

Search this forum for "iPerf", there's many threads in here that show how to use it, for example: [http://ubuntuforums.org/showthread.php?t=1034930](http://ubuntuforums.org/showthread.php?t=1034930)

Then, on the NFS server, use **sudo hdparm -tT /dev/sdXn** (where sdXn is the harddisks device/partition name) to see how much the harddisk is able to deliver:

```
marc@torch:~$ **sudo hdparm -tT /dev/sda1** 

/dev/sda1:
 Timing cached reads:   6218 MB in  2.00 seconds = 3116.76 MB/sec
 Timing buffered disk reads:   94 MB in  3.02 seconds =  31.12 MB/sec

```

Finally, also use iPerf to read n-hundred Megabytes of data from a file (on the harddisk you are serving NFS from) when sending to it's peer - like that, you can see how your system combines storage I/O with network I/O - without the protocol overhead of NFS or Samba:

for example
```
user@client:/~$ **iperf -s**

```
```
user@server:/~$ **iperf -c <client's IP> -n 600M -F /path/to/samplefile -i 5**

```


regards

Marc

---

### Post by e24ohm on 2009-01-23
> **netztier said:**
> Default for both is 8192 (8 kByte), which is ok for your common wired LAN. It means that one NFS read/write request will carry up to 8k of data. A full-sized NFS request will be transported as 6 ethernet frames of 1500bytes (max). 

On networks with high packet loss rates (such as WLANs), this becomes somewhat of a problem: if only one of the 6 ethernet frames is lost, the entire NFS request has to be repeated. In such networks, it helps to reduce this value to 1024, so an entire NFS request fits into a single ethernet/wireless frame; if a frame/packet is lost, only a single request will have to be repeated. 

So since ethernet is prone to the occasional packet loss by it's very nature, using large numbers has a limited benefit. A long while back, I did some tests and it turned out that using 32768 (32kBytes) for rsize and wsize gave slightly better performance - I used a 100mbps LAN then, with two switches, Debian as server and Ubuntu as client. Today, I have Ubuntu 8.04 as server and 8.10 as client, and a 1000Mbit/s LAN. The server hardware is old and so are it's IDE disks - still, I can get 20-30MByte/sec out of the old box.


But before diving into NFS tuning, please do a sanity check on your network: install **iPerf** from the universe repositories and run it from server to client and client to server. On a 100Mbps switched network, iPerf should report figures in the 93-95Mbit/s range.

This might seem redundant, but more than once I've been able to make out a full/half duplex problem, a cable problem or a slowly dying LAN switch (small packets at slow rates would work, but highspeed streams were terrible), and these need to be sorted out before taking care of NFS.

Search this forum for "iPerf", there's many threads in here that show how to use it, for example: [http://ubuntuforums.org/showthread.php?t=1034930](http://ubuntuforums.org/showthread.php?t=1034930)

Then, on the NFS server, use **sudo hdparm -tT /dev/sdXn** (where sdXn is the harddisks device/partition name) to see how much the harddisk is able to deliver:

```
marc@torch:~$ **sudo hdparm -tT /dev/sda1** 

/dev/sda1:
 Timing cached reads:   6218 MB in  2.00 seconds = 3116.76 MB/sec
 Timing buffered disk reads:   94 MB in  3.02 seconds =  31.12 MB/sec

```

Finally, also use iPerf to read n-hundred Megabytes of data from a file (on the harddisk you are serving NFS from) when sending to it's peer - like that, you can see how your system combines storage I/O with network I/O - without the protocol overhead of NFS or Samba:

for example
```
user@client:/~$ **iperf -s**

```
```
user@server:/~$ **iperf -c <client's IP> -n 600M -F /path/to/samplefile -i 5**

```


regards

MarcHey thanks mate. I am running CentOS 5.5 as my server, and i believe 7.10 as my ubuntu client. I had some issuesw ith 8.04 and my hardware. I will try your suggestions. I feel alittle frustrated, because i am only moving 54mb folders of .flac and .ogg files around, and they take over 30 minutes.

My hardware is old on the server, so that might be part of the problem. I think the box is an old AMD K6 processor, with 1GB of RAM. I only did this because i wanted to learn an rpm based distro.

Oh, and i am not sure which version of NFS i am useing. I tried the NFS4 switch in my terminal, but it errors out, and the only way i can get the drive to mount is by using just NFS.



thanks.

---

