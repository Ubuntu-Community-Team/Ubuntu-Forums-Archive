---
title: "What causes stalled copies?"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by ZagiFlyer on 2006-07-10
Hey All,

I've got several GB of data on my Windows 2003 laptop that needs to make it's way onto my Kubuntu dekstop system. I keep starting copies and they keep stalling. I'd kind of like to know why. Actually, I'd like them to not stall, but. . .

As stated, The laptop is running Windows 2003 and is connected to the home network via a known good and trustworthy wireless connection. When doing Windows/Windows copies, I have *never* had a problem.

The target computer is a home-built system that was running Windows 2003 R2 until yesterday and also never had a networking problem. So, I know that it's not a hardware or network issue.

I've mounted the Windows shares on the laptop to mount points on the Kubuntu system via the command:
$ sudo mount -t smbfs -o username=<my username>/<source machine workgroup> //<source machine IP address>/<share name> /mnt/<mount point>

I can then browse the remote shares, so I know that part works.

I open Konqueror and type in /mnt/<mount point> in the top area and all the files on the share show up. I then <CTRL-A> and drag them to my target folder in my home directory. The copy starts and all looks good.

After awhile, the copy stops and the dialog box says "stalled".

The Windows laptop (source machine) is still up and on the network. All networking appears to still be functional (I can reach the Internet, ping the source laptop, etc.).

**Edit: **I've discovered that, when a copy stalls, if I then enter: $ls /mnt/<mount point> it returns an error: "Input/output error". I now believe this to be a networking issue, so it's in the correct forum after all.

**Another edit: **I did an "$ls /mnt/<mount point> in two different terminal windows (for two different smbfs mount points mounting the same Windows 2003 laptop) and actually hard-locked the system.

Any ideas? This is seriously bugging me! If I can't trust something as simple as a network file copy, then how can I trust the OS at all?

I *really* want to make a move from Windows for my home systems, but if I can't even copy across the network. . .

Thanks!

---

### Post by DigitalXpert on 2006-07-10
I'm guessing that the xfer is taking so long that the authenticated connection is timing out.  But who knows, its windows.... its breaks and doesn't tell you why.

I'd install either proftpd on the ubuntu machine and transfer it via ftp.  Ftp will give you better xfer speeds than the smb mount will as well.  

Another option is to install ssh on the ubuntu.  Then just xfer the files from windows to ubuntu using the program winscp.

You will have to do the ssh if you plan to xfer files to anywhere but your home folder on the ubuntu machine.

---

### Post by ZagiFlyer on 2006-07-11
> **DigitalXpert said:**
> I'm guessing that the xfer is taking so long that the authenticated connection is timing out.  But who knows, its windows.... its breaks and doesn't tell you why.

I'm inclined to doubt this, as a Windows-to-Windows copy never had the issue. Based on that, I submit that this is a Linux issue, not a Windows issue. For that reason, I further submit that it's Linux that's not forthcoming with a failure cause. Lastly, there should be *nothing* that a Windows copy could do to cause Linux to hard-lock (and require a power cycle).

I've been using computers since 1978, I was a Unix (SunOS 4.1.x) sysadmin for several years, and I've been an MCSE in the past as well. Obviously I'm not smart enough to figure this out on my own (yet) but to just say "that's Windows" and write the problem off -- especially when there is evidence that it's **not **Windows -- is to ignore the basic issue.

> **DigitalXpert said:**
> Another option is to install ssh on the ubuntu.  Then just xfer the files from windows to ubuntu using the program winscp.

That's an alternative I'd never considered. I'll look into it. In the meantime, I'd like common tasks such as copying files to/from an OS that runs on 95% of the world's dekstops to Just Work and not require a reboot of the Linux target computer.

> **DigitalXpert said:**
> You will have to do the ssh if you plan to xfer files to anywhere but your home folder on the ubuntu machine.

If I 'sudo', I can write anywhere I'd like.

Please don't take the tone of this response the wrong way. I'm not "defending Windows", nor am I bashing Linux. More importantly, I really do appreciate people reading the post and offering advice. I'd just like to figure out why this is happening and fix the core issue. Then maybe I could help others out when it happens to them.

Is this something that should go in a bug report? Or is it just a configuration/user error?

---

### Post by relovett on 2006-07-11
See if "Input/output error" can be attributed to a disk error. Examine /var/log/messages or /var/log/syslog for entries containing your disk device. You may need to tweak disk parameters with hdparm.

My guess is that its an error in the linux filesystem code.

---

### Post by ZagiFlyer on 2006-07-11
Curiouser and curiouser. . .

I changed my kernel from generic i386 to 2.6.15-26-k7 #1 SMP PREEMPT and stared the copy again. I didn't think to myself "hey, if I change the kernel, maybe. . .", I changed the kernel because I wanted to make use of the second core in my AMD machine.

That said, there are two new pieces of data:
1) The copy has not stalled (yet)
   It's 26% through 11GB and in the past it would have stalled already

2) In spite of the fact that it's not stalling (yet), I'm getting the following messages in /var/log/messages:

> 07/11/2006 01:28:26 PM	beast	kernel	[17182486.028000] smb_get_length: Invalid NBT packet, code=6e

07/11/2006 01:28:56 PM	beast	kernel	[17182516.024000] smb_add_request: request [edc5ba80, mid=25199] timed out!

07/11/2006 01:28:56 PM	beast	kernel	[17182516.024000] smb_proc_readdir_long: error=-5, breaking

07/11/2006 01:33:06 PM	beast	kernel	[17182765.532000] smb_add_request: request [edda0bc0, mid=2932] timed out!

07/11/2006 01:37:19 PM	beast	kernel	[17183018.160000] smb_add_request: request [edc5b180, mid=51811] timed out!

07/11/2006 01:43:28 PM	beast	kernel	[17183388.076000] smb_add_request: request [edda05c0, mid=2137] timed out!

07/11/2006 01:51:05 PM	beast	kernel	[17183844.216000] smb_add_request: request [edda09c0, mid=23306] timed out!

07/11/2006 01:54:00 PM	beast	kernel	[17184019.224000] smb_add_request: request [edda08c0, mid=59691] timed out!

07/11/2006 01:54:30 PM	beast	kernel	[17184049.912000] smb_get_length: Invalid NBT packet, code=41

07/11/2006 01:55:00 PM	beast	kernel	[17184079.912000] smb_add_request: request [edda06c0, mid=14485] timed out!

07/11/2006 02:00:25 PM	beast	kernel	[17184404.172000] smb_get_length: Invalid NBT packet, code=20

07/11/2006 02:00:25 PM	beast	kernel	[17184404.172000] smbiod_handle_request: smbiod got a request ... and we don't implement oplocks!

07/11/2006 02:00:54 PM	beast	kernel	[17184433.968000] smb_add_request: request [edda0ec0, mid=21311] timed out!

07/11/2006 02:20:13 PM	beast	none	-- MARK --

07/11/2006 02:20:15 PM	beast	kernel	[17185594.768000] smb_add_request: request [f551a980, mid=23417] timed out!

07/11/2006 02:25:54 PM	beast	kernel	[17185933.532000] smb_add_request: request [f551a980, mid=8199] timed out!

07/11/2006 02:30:26 PM	beast	kernel	[17186205.088000] smb_add_request: request [db84b1c0, mid=59391] timed out!

07/11/2006 02:39:37 PM	beast	kernel	[17186756.076000] smb_add_request: request [d4de6bc0, mid=39232] timed out!

07/11/2006 02:53:32 PM	beast	kernel	[17187591.204000] smb_add_request: request [d4de6dc0, mid=48595] timed out!

So, it looks like it *may* be an issue with the i386 compiled kernel -- I really don't know. If it stalls again, I'll edit the post.

---

### Post by egd on 2006-08-25
I'm having exactly the same copy stall problems getting data off NTFS partitions onto an ext3 formatted drive - no network involved though.  The source drives are all mounted READ-ONLY and I can acces any file individually.  Ask Krusader or MC to copy my data off the NTFS partition to the ext3 partition and Ubuntu grinds to a halt after roughly 7GB.

At first I thought the target drive may be faulty (it's been in use for years) so I checked it and thereafter the source drive using manufacturer diagnostics and both drives checked out OK, report no file system errors etc.  To be on the safe side I used GParted to repartition and reformat the target drive and retried the copy operation.  Same proplem occurs...copy operation stalls and Ubuntu grinds to a halt requiring a hardware reset.

My strategy was simple - install Ubuntu, get one additional empty HDD, copy data off NTFS partitions to ext3, repartition and reformat NTFS partitions to ext3, et voila - kiss my proverbial *** windows.  Of course, it's never that simple, is it.

Three things I'd add:
- The same copying operation of the data under wxp or w2k3 completes without incident, stall or any issue
- seems unlikely to be a network issue as described earlier.
- we're not the only ones experiencing these problems [http://www.ubuntuforums.org/showthread.php?t=63064&highlight=stalled+copy](http://www.ubuntuforums.org/showthread.php?t=63064&highlight=stalled+copy) & [http://www.ubuntuforums.org/showthread.php?t=38256&highlight=stalled+copy](http://www.ubuntuforums.org/showthread.php?t=38256&highlight=stalled+copy)

Anyone have any ideas to resolve the issue?

I'm running ubuntu-6.06.1 on an Intel d975xbx, kernel 2.6.15-26-amd64-generic #1 SMP PREEMPT

---

### Post by jmmcd on 2006-09-26
Hi all,

I'm having a similar problem. The first symptom is that transfers of
large(ish) files over scp (from my ubuntu to my mac) often stall (the
transfer rate goes down, then scp echoes "- stalled -"), whereas very
small files often succeed. It also happens from my ubuntu to another
linux machine. However, it's asymmetric: from the mac to the ubuntu
works fine. When it stalls, I have to use ifdown/ifup eth0 to get my
network back. HTTP and apt-get (which runs over HTTP) are fine, at
least for downloading to the ubuntu.

On the net, I've seen this associated with iptables (1), with dropped
packets (2), and with very slow connection speeds from ISPs (3). In my
case, I don't think iptables is running (how can I tell? Sorry, I
don't know anything about it); and my two machines are on a fast LAN,
and I've used ls -lh on the target machine (see (4)), so that leaves
(2). And yes indeed:

$ sudo ping -f jamesmac
Password:
PING jamesmac.XXX.XXX (xx.xx.xx.xx) 56(84) bytes of data.
..............
--- jamesmac.XXX.XXX ping statistics ---
514 packets transmitted, 500 received, 2% packet loss, time 565ms
rtt min/avg/max/mdev = 0.271/0.312/18.003/0.792 ms, ipg/ewma 1.102/0.275 ms

2% packet loss on this run, though it's often as high as 15%.

So what could be causing the packet loss? I don't think it's hardware,
because I dual-boot my ubuntu into windows, and winscp works fine in 
both directions (though I don't know how to do the equivalent of 
ping -f in windows). On the other hand, on ubuntu, ping (without -f) 
doesn't show any packet loss.

I ran ethtool, and that says that it's connected at 100Mb/s with full
duplex, which I think is right; and after the ping -f I ran ifconfig,
and that didn't report any errors or dropped packets on eth0.

What else? I've seen it recommended to try reversing the ethernet
cables (5), and I've tried that and also swapped out ethernet
cables. No change.

So now I'm out of ideas - do I have my networking misconfigured
somewhere? I originally had ipv6 set up (as is the default on ubuntu)
but I tried disabling it (search the forums and google for lots of
references to /etc/modprobe.d/blacklist and aliases), and it doesn't
make any difference.

Finally, another symptom I've noticed is that ifup eth0 is very slow -
about 60 seconds.

Dapper Drake on a Toshiba laptop with Marvell Yukon ethernet card.



(1) [http://www.networksecurityarchive.org/html/Secure-Shell/2005-04/msg00049.html](http://www.networksecurityarchive.org/html/Secure-Shell/2005-04/msg00049.html)
(2) [http://openvpn.net/archive/openvpn-users/2005-02/msg00641.html](http://openvpn.net/archive/openvpn-users/2005-02/msg00641.html)
(3) [http://lists.freebsd.org/pipermail/freebsd-bugs/2004-January/005146.html](http://lists.freebsd.org/pipermail/freebsd-bugs/2004-January/005146.html)
(4) [http://lists.pdxlinux.org/pipermail/plug/2004-January/027657.html](http://lists.pdxlinux.org/pipermail/plug/2004-January/027657.html)
(5) [http://lists.pdxlinux.org/pipermail/plug/2004-January/027752.html](http://lists.pdxlinux.org/pipermail/plug/2004-January/027752.html)

---

### Post by bcampbe81 on 2006-09-28
K guys 

I'm a real newb to linux not just ubuntu but after doing a bit of research i have installed ubuntu dapper on to my new system.

I live in a share place with a bunch of linux ppl one of which pointed out the fact that MTU is set as a default to 1500 when it should be set to 1492 to prevent any packages being dropped during transfer. 

so i know how to set it when i need to transfer the files

sudo su
sudo ifconfig eth1 mtu 1492

and everything seems to be going well..

further googleing and i found that u need to alter one of the config files and place the desired mtu into that file

sudo gedit /etc/network/interfaces

however when i attempted to put the line of code in (mtu=1492, under the appropriate place) i was unable to

anyhelp would be appreciated ... the others at my home dont use ubuntu

thanks in advance

Ben

---

### Post by jmmcd on 2006-09-29
Hi bcampbe81,

> place the desired mtu into that file

> sudo gedit /etc/network/interfaces

> however when i attempted to put the line of code in (mtu=1492, under the appropriate place) i was unable to

This should work - I have this in my /etc/network/interfaces:

```
# The primary network interface
auto eth0

iface eth0 inet static
address x.x.x.x
netmask x.x.x.x
gateway x.x.x.x
mtu 1492
```

(*not mtu=1492 - ie no 'equals' sign*)

and when I run

```
$ sudo /etc/init.d/networking restart
```

and then 

```
$ ifconfig eth0
```

I see that the mtu has been set to 1492. If this isn't happening for you, post exactly what you did and what went wrong. By the way, from looking at

```
$ man interfaces
```

it doesn't seem to allow mtu as an option for dhcp - are you using dhcp or a static ip?


For my own problem, altering the mtu doesn't affect things, unfortunately. I tried quite a few different values.

---

### Post by TurkVU on 2006-12-19
Are there any new ideas on this? Is it def a kernel issue? I'm on edgy generic and having the same type of issue

I mounted a drive on a window share using smb4k and when I try to copy files from the windows share to a local ntfs drive (mounted w/ ntfs3g) at first it xfers at several MBps. But the connection slowly degrades into the KBps and eventually stalls. It 'wakes up' every now and again and makes some progress...but copying a 700MB file can take over a day...which is ridiculous.

All my other network stuff seems to be working just fine throughout this entire process.

Any ideas?

---

### Post by xanas3712 on 2007-01-21
I think the issue is a KDE/konqueror issue.  I had it recently and found this thread in a search about the problem.

I never have this sort of problem copying from the console using cp, but various different things (partition types, network mounts, etc. ) seem to be finicky when copying in kde (every version just about).  Of course, at times it works just fine, so it all seems rather inconsistent.

And it's not reserved for me to a specific kernel or distro (this is on gentoo for example).

This thread is old, but the problem still exists even now without a directly attributed cause so I am just bumping it to confirm it still occurs and add a "me too" to a problem that down the road is hopefully looked into further.  I will try to look into it more deeply sometime myself.

---

### Post by jmmcd on 2007-04-23
I don't think it's anything to do with KDE or Konqueror, I had the problem on a fairly vanilla Dapper without much KDE stuff...

FWIW my problem has disappeared after clean-installing Feisty.

---

### Post by Defrector on 2007-12-29
BUMP.

I am  trying to figure out why my CIFS transfers are stalling so badly. This has been persisting for over a year now with little avail with kernel updates.

I have a Maxtor NAS which uses linux for its SMB server. Transfers from it to a windows machine are flawless. However when copying to a kubuntu 7.10 machine the copy dialog indicates a stall when doing large runs of files (one thread, not multiple copies at once). Multi-threading copies almost guarantees severe stalling.

The stalling is evident when it occurs with smaller files. It seems that stalling happens more often with data images such as floppy IMG files or NES images-all of which are 2MB or less. This only happens with certain files. There does not appear to be any oddities in the names, timestamps, or ownerships of those files.

The stalls occur on the same files consistently. When the stalls happen, I can catch them in the syslog:
```
Dec 29 03:35:45 studio-pc kernel: [ 1191.387735]  CIFS VFS: server not responding
Dec 29 03:35:45 studio-pc kernel: [ 1191.387753]  CIFS VFS: No response to cmd 46 mid 5172
Dec 29 03:35:45 studio-pc kernel: [ 1191.387761]  CIFS VFS: Send error in read = -11
Dec 29 03:35:45 studio-pc kernel: [ 1191.388030]  CIFS VFS: No response for cmd 50 mid 5173
Dec 29 03:35:46 studio-pc kernel: [ 1192.011720]  CIFS VFS: No response for cmd 50 mid 5174
Dec 29 03:35:46 studio-pc kernel: [ 1192.011855]  CIFS VFS: No response for cmd 50 mid 5175
Dec 29 03:35:46 studio-pc kernel: [ 1192.135224]  CIFS VFS: Send error in read = -9
Dec 29 03:35:46 studio-pc kernel: [ 1192.142413]  CIFS VFS: Send error in SETFSUnixInfo = -5
Dec 29 03:36:15 studio-pc kernel: [ 1221.361406]  CIFS VFS: server not responding
Dec 29 03:36:15 studio-pc kernel: [ 1221.361425]  CIFS VFS: No response to cmd 46 mid 5198
Dec 29 03:36:15 studio-pc kernel: [ 1221.361434]  CIFS VFS: Send error in read = -11
Dec 29 03:36:15 studio-pc kernel: [ 1221.361447]  CIFS VFS: No response for cmd 50 mid 5201
Dec 29 03:36:15 studio-pc kernel: [ 1221.361457]  CIFS VFS: No response for cmd 50 mid 5200
Dec 29 03:36:15 studio-pc kernel: [ 1221.361472]  CIFS VFS: No response for cmd 50 mid 5199
```

I am trying the transfers from the command line and the stalls are much shorter, however they are still happening. There is definitely a pattern in terms of the same files causing snags, however I see no pattern as to why those specific files are causing the snags.

The kubuntu machine's kernel is 2.6.22-14-386
The NAS' kernel is 2.4.20
It's distribution is openmss, based off of a custom-made linux-based firmware put together at Maxtor for their Maxtor Shared Storage NAS. The NAS uses reiserfs internally for storage. 

The destination on the kubuntu side is also reiserfs.

Could it be the older kernel and newer kernel not getting along? Why are these snags happening so much with certain files?

The NAS is listed in fstab as such:
```
//192.168.1.204/XXXX /media/Maxtor\040NAS cifs auto,username=xxxxx,password=yyyyy 0 2
```

Mounts fine. After using the CIFS format instead of SMBFS things got a lot more stable. But the copy stalls persist. The stalls are significant enough to be making 20GB transfers a multi-day task.

**edit:** yes, my MTU is set to 1492 :)
**update:** I compiled a new kernel to version 2.6.23.12 with K7/Athlon/Duron set instead of 486. It still is stalling, still drama on syslog during cp so I don't think it is the kernel's processor setting... nor does it seem to be fixed in an upgrade at this time. I wonder if there's an MTU setting on the NAS; it might be something to try.
**update:** The stalling problems persist copying from a mac to ubuntu via SMB, so it appears to have nothing to do with the remote machine but something inside of ubuntu.

If anyone has input/ideas please reply.

**update:** Found the problem! It wasn't ubuntu itself but a flaky ADMTek network card and/or driver glitch. Other things I checked in case you're reading this and still haven't found a solution:

- simplify the network: remove switches/hubs to see if something is corrupting the send process with process of elimination
- run ifconfig to see if there are a lot of packet errors. Sometimes this indicates flaky cards or a corruptive network.
- using ifconfig set MTU to 1500 or 1492 (1500 is considered the 'standard' and all mtu's are recommended to match on network connections but 1492 is another popular one if that doesn't work)
- move network card to a different slot
- Try FTP, SMB, and other transfer protocols from the command line to send the masses of files or GFTP. If you have a bad general interface (driver or hardware) they should all stall at least somewhat badly on some files. I don't recommend SSH/Telnet, as SSH and other interactive protocols seem to be much more tolerant to problems than transfer protocols.

---

