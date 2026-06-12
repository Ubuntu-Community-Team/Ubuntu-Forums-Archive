---
title: "Slow file transfers over Samba + GbE"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by philpem on 2010-02-08
Hi guys,
I'm having some issues with slow file transfers over Samba. The network segment involved looks like this:

Server (wolf) eth0 ---> Netgear GS108 GbE switch ---> Client (cheetah) eth0

Server has one Realtek RTL8111C PCI Express Ethernet controller and three Realtek RTL8110SC PCI GbE controllers. eth0 is the 8111C (PCI Express) controller. Processor is a 1.6GHz Intel Atom 230, with HyperThreading enabled, and 2GB RAM. OS is 32-bit Ubuntu 8.10 LTS (it's a server, I want it to be stable).

Client has a pair of Marvell 88E8056 PCI-E GbE controllers (eth0 and eth1). eth1 is disabled, eth0 is wired to the switch. CPU is an Intel Core 2 Quad Q6600 at 3GHz (slightly overclocked), with 4GB RAM, running 64bit Ubuntu 9.10.

What I'm seeing is an incredibly slow (~4Mbytes/sec) transfer rate from Samba-based file transfers, and better rates from SFTP (~10MBytes/sec), but the SFTP transfer rate drops off over time -- that is, a transfer starts at ~10MBytes/sec, then drops off steadily to around 6-7MBytes/sec.

I've run netperf on both machines and got this:
```
philpem@wolf:~$ netperf -H cheetah
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to cheetah.homenet.philpem.me.uk (10.0.0.8) port 0 AF_INET : demo
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.00     367.31

philpem@cheetah:~$ netperf -H wolf
TCP STREAM TEST from 0.0.0.0 (0.0.0.0) port 0 AF_INET to wolf.homenet.philpem.me.uk (10.0.0.1) port 0 AF_INET : demo
Recv   Send    Send                          
Socket Socket  Message  Elapsed              
Size   Size    Size     Time     Throughput  
bytes  bytes   bytes    secs.    10^6bits/sec  

 87380  16384  16384    10.01     540.46   

```

From these tests, it looks like I should be expecting a worst case transfer rate of about 15MBytes/sec (based on the highly scientific method of dividing the Mbits/sec figure from Netperf by 20 -- 8 bits per byte plus overheads, and ACK packets).

I've also done disc performance tests on the server:
```
philpem@wolf:~$ sudo hdparm -Tt /dev/md0

/dev/md0:
 Timing cached reads:   1150 MB in  2.00 seconds = 574.76 MB/sec
 Timing buffered disk reads:  242 MB in  3.02 seconds =  80.00 MB/sec

```

All this points to an issue with Samba.. Is anyone aware of any issues that could cause slow file transfers between Samba 3.2.3 (on the server) and 3.4.0 (on the 9.10 client)?

I've already added a "socket options" line to smb.conf on both machines:
```
socket options = TCP_NODELAY SO_RCVBUF=32768 SO_SNDBUF=32768
```
The transfer rates are the same both with and without this line.

I've also tried setting the MTU higher on both machines -- the network driver on the server won't accept any MTU higher than 1500 bytes; the driver on the client will go up to ~9000 bytes (the maximum my LAN switch will allow). I haven't tested to see if this has any effect on the transfer rate, but I wouldn't expect it to unless both machines are using the same increased MTU.

Is there something I've missed here? Surely I should be seeing transfer rates far higher than this -- I would have expected somewhere in the region of 20-30Mbytes/sec peak for unencrypted traffic (the Atom230 in the server tends to struggle a bit when fed huge blobs of encrypted data, which is probably why SFTP is slowing down mid-transfer)...

Thanks,
Phil.



EDIT: I've just tried increasing the MTU on both systems to 7200 (the Marvell chip will go up to 9000, but the Realtek chip only supports 7200, thus I've set it to the lower of the two) and installed the latest Realtek drivers on the server. The standard kernel 'r8169' driver won't accept an MTU above 1500.
Speed seems much better to start with (seems to transfer about 50MB in a few seconds) but rapidly tails off to about 6Mbytes/sec over SMB, slowing down even more as the transfer proceeds (it's been running for ~2 minutes and is now down to ~5Mbytes/sec).
Netperf reports the same transfer rates with MTU1500 as it does for MTU7200. SFTP with Jumbo Frames runs at about 7Mbytes/sec (same as without JF support).

EDIT2: I've disabled the network bridge (br0 = eth0+eth1+eth2) and the transfer rates (per netperf) are up to 849.25Mbit/sec and 940.96Mbit/sec (cheetah=>wolf and wolf=>cheetah respectively). Reducing the MTU from 7200 to 1500 roughly halves the speeds in both directions. Samba and SFTP are still glacial at both MTUs though -- they both start at ~10-20MBytes/sec and rapidly tail off to ~4MByte/sec. Ugh.

---

### Post by skogs on 2010-02-11
Samba network speed has been crippled in Ubuntu for a great long period of time.  As I'm sure you've found by now, blame casting is frequent and vigorous.  Some achieve better results using an fstab entry to mount the share rather than nautilus's mapping function.  Some achieve better results by switching to either deadline or anticipatory scheduler for the kernel's IO scheduler.  

I feel your pain.  I've dealt with this every time I've loaded/reloaded/reinstalled/upgraded ubuntu for the last 3 years.  Just now, finding your post, I was searching for the answer myself.  I do a great deal of computer repair, and hate to reboot to windows to do simple tasks like copy large quantities of files or antivirus/malware scans.  I was just recently getting transfer rates that started at about 6Mb/s....down to 3Mb/s....down to 1Mb/s....and then it started going down to 900kb/s.  Just plain isn't acceptable when you are moving Gigs of data.  

:)  Hope I gave you some ideas to work with.

---

### Post by ojobson on 2010-03-14
I have similar issues, but only with reading from the samba share on my server.

I have U9.10 installed on a atom 330 system, used as a file server with the onboard realtek 8111c Gig ethernet chip, similar setup to the OP - the clients here are a MacBook Pro (2009 5,5) and a Win 7 Pentium D machine.

Writing to the samba share on the server is around 35 to 50 MBps depending on the client. Reading from the server using samba is about 7 MBps on both the Win and OS X clients.

This read speed is a marked contrast to the appletalk (netatalk) share on the atom server - this achieves around 40MBps when read from the MBP - so the hardware can handle it. The Win/MBP can both talk over samba at about 45 MBps in either direction.

I have used all the various SO_RCVBUF=XXXXX, SO_SNDBUF=XXXXX, TCP_NODELAY etc and tweaked the mtu to 7200.

Can't seem to shift the speed higher no matter what i do.

---

### Post by peap on 2010-10-25
> **ojobson said:**
> I have similar issues, but only with reading from the samba share on my server.

I have U9.10 installed on a atom 330 system, used as a file server with the onboard realtek 8111c Gig ethernet chip, similar setup to the OP - the clients here are a MacBook Pro (2009 5,5) and a Win 7 Pentium D machine.

Writing to the samba share on the server is around 35 to 50 MBps depending on the client. Reading from the server using samba is about 7 MBps on both the Win and OS X clients.

This read speed is a marked contrast to the appletalk (netatalk) share on the atom server - this achieves around 40MBps when read from the MBP - so the hardware can handle it. The Win/MBP can both talk over samba at about 45 MBps in either direction.

I have used all the various SO_RCVBUF=XXXXX, SO_SNDBUF=XXXXX, TCP_NODELAY etc and tweaked the mtu to 7200.

Can't seem to shift the speed higher no matter what i do.


I would love to see your netatalk lines as my own netatalk performance is far below the 40MB/s you're getting.

---

### Post by ojobson on 2010-10-25
Gave up in the end and installed OSX SL on the atom board - runs like a dream and I don't have to mess around for ages to get Ubuntu to support time machine. Get 40 MB in each direction regardless of client / protocol.

Wasn't all that easy to set up, but there are plenty of guides and help  - also, probably no worse than my first time installing ubuntu.

---

### Post by lozt.again on 2011-02-28
> **skogs said:**
> Samba network speed has been crippled in Ubuntu for a great long period of time.  As I'm sure you've found by now, blame casting is frequent and vigorous.  Some achieve better results using an fstab entry to mount the share rather than nautilus's mapping function.  Some achieve better results by switching to either deadline or anticipatory scheduler for the kernel's IO scheduler.  

I feel your pain.  I've dealt with this every time I've loaded/reloaded/reinstalled/upgraded ubuntu for the last 3 years.  Just now, finding your post, I was searching for the answer myself.  I do a great deal of computer repair, and hate to reboot to windows to do simple tasks like copy large quantities of files or antivirus/malware scans.  I was just recently getting transfer rates that started at about 6Mb/s....down to 3Mb/s....down to 1Mb/s....and then it started going down to 900kb/s.  Just plain isn't acceptable when you are moving Gigs of data.  

:)  Hope I gave you some ideas to work with.

So there isn't a way round this problem?

I'm using my old pc for a nas/media server, and yeah, reads or writes from a window machine are pathetic. 5mBps. The other way round and we see 50mBps. Real great file server :rolleyes:

Maybe virtual box and freenas? Seems like a long way round to do something relatively simple.

---

### Post by headvampyre@hotmail.co.uk on 2011-02-28
Try building packages from sambas git repos, they wont have the problems from ubuntu, and as for:

socket options = SO_RCVBUF=XXXXX, SO_SNDBUF=XXXXX, TCP_NODELAY
max xmit = XXXX

You need to play around a lot with these, it depends on your LAN, not everyone elses.
65536 is pretty much only useful on a Gigabit network, not 54mbps or 100mbps, try using lower and higher options aswell, although the bigger numbers might appear to give a higher speed - they wont.

---

### Post by lozt.again on 2011-03-01
> **headvampyre@hotmail.co.uk said:**
> Try building packages from sambas git repos, they wont have the problems from ubuntu, and as for:

socket options = SO_RCVBUF=XXXXX, SO_SNDBUF=XXXXX, TCP_NODELAY
max xmit = XXXX

You need to play around a lot with these, it depends on your LAN, not everyone elses.
65536 is pretty much only useful on a Gigabit network, not 54mbps or 100mbps, try using lower and higher options aswell, although the bigger numbers might appear to give a higher speed - they wont.

Cheers buddy. That sounds like a plan.

---

### Post by headvampyre@hotmail.co.uk on 2011-03-01
Yeah, I find that 
max xmit = XXXX
causes a LOT of speed problems, especially in Samba4 environments.
i set it to 65536, and all the other common ones and had hell with it, in the end i just commmented it out, but if you wanna keep it, just play around with that aswell :)

---

