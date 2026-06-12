---
title: "large NFS copy locks up/hang client with large files (again) (lucid)"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by ScarletPea on 2010-05-09
Good day all,

 On lucid 10.04 client, with debian (sid) nfs server, using nfsv4, the client machine locks up/hangs on transfer of large files ~GiB+ to the nfs mount.

 I am not alone, this was reported by:
[http://ubuntuforums.org/showthread.php?t=1455632&highlight=nfs+lockup]("http://ubuntuforums.org/showthread.php?t=1455632&highlight=nfs+lockup")
and sim.
[http://ubuntuforums.org/showthread.php?t=1437722&highlight=nfs+lockup](http://ubuntuforums.org/showthread.php?t=1437722&highlight=nfs+lockup)

Same behaviour with cp or nautilus.
No problems with scp, rsync, samba(except its super slow - no not an option)

Read from the server seems ok.

With the mouse free to move and everything else stuck I thought this could be the nic module or interrupts or something. Loading the module with debug enabled showed nothing.

The client machine is Dell XPS M1710 with:
 Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet adaptor. 
(so using wired in case you ask), standard mtu, connecting through a fast ethernet switch to via epia-en server, nic: 
VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter

NFS is mounted as (from fstab)
```
192.168.1.9:					/media/minihaha nfs4	noauto,users,rw,hard,intr 0 	0
```
and exported as (/etc/exports)
```
[/nfs4exports 192.168.1.0/24(rw,fsid=0,sync,insecure,no_subtree_check,nohide)
```

Given the range of machines that this is occuring on, I doubt it is one nic. It may be a gigabit thing... 

 Can we amass the user experience here and see if there are any common factors.

 Other than that, what commands etc. can I do to really log what is going on to try and determine what is causing this.

The weird thing is it doesnt happen straight away, it takes a finite (~40s) ammount of time, which I assume is why noone notices for small files. So there could be a buffer or somthing that get full... 
 Anyway, help and collaboration would be appreciated.

Thank you.

Jasper

---

### Post by ScarletPea on 2010-05-10
From [http://ubuntuforums.org/showthread.php?t=1455632&highlight=nfs+lockup](http://ubuntuforums.org/showthread.php?t=1455632&highlight=nfs+lockup),
The configurations with trouble are:

dist: Lucid,
nic:  ath5k, wireless

dist:Lucid/Karmic
nic:  atl1c, "Atheros Communications AR8131 Gigabit Ethernet"
nfs server: debian 5.0

dist: karmic
arch: 64bit (32bit fine aparently)

I am:
dist: Lucid
arch: 64bit
nic: tg3, Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet
nfs server: debian (sid) (NFS V4)

---

### Post by Lepy on 2010-05-13
I've been experiencing this problem as well. NFS uploads to a Freenas seem to lockup the ubuntu systems (graphically and sometimes ssh) and cause transfer speeds to slow down dramatically or stop altogether. 

A desktop and mythbuntu system that are both gigabit wired to the Freenas exhibit these symptoms. A laptop with a wireless g connection does not seem to show these symptoms (or I am too lazy to transfer a large file at g-speeds). All systems including Freenas have different nic cards/drivers.

I have noticed that transferring to the nas causes a spikey graph over gigabit while the wireless seems to be a pretty constant throughput (wireless is much slower, so makes sense). I could blame it on Freenas or hardware but 1.) a reboot of the uploading machine doesn't break any of the nas's functions or subsequent connections, it keeps chugging along like nothing ever happened for the rest of the systems 2.) someone has the same problem using openfiler. 

I've never had a problem with downloads, and none of the logs seem to show any signs; however, I have experienced a dmesg "task X blocked for more than 120 seconds." as jeebustrain. I believe I have only seen this on the mythbuntu system, but it only seems to bork the systems lirc usb remote until a reboot.

I recently upgraded the Freenas to the latest nightly build, and the problem still occurs. These symptoms were present in many kernels under 9.10 and seems to have gotten worse in 10.04. On 9.10 I could transfer a few 100 gigs to the nas no problem and it would occasionally lock up. Now, it seems like it happens on many 600+ meg files.

Other than specific hardware, I'm not sure if there is much more to say that hasn't been covered in the other threads you linked. I hope we can get this figured out. This is pretty killer for the mythtv box because many auto transcodes/exports to the nas of 40+ minute shows (with commercials cut) seem to be locking the system causing recordings to not take place or mythwelcome to not function. This is only the transfer too as the transcoding is done on the local hdd.

Anyway, long post, but a big problem!

---

### Post by dr_latino999 on 2010-05-18
I am experiencing the same effect on my test setup at work, where even a 700mb ISO brings NFS and Nautilus to a screeching halt for 5-45 seconds then resumes as if nothing happened. Both client and server are 10.04.

---

### Post by ScarletPea on 2010-05-21
Can I confirm that ALL the above problems are with Gigabit NIC's
 I hae a 10/100 switch.

Where to from here? a bug report maybee, but if _anyone_ out there has another distro handy, can they check this out, so <other distro> -> deb/ubuntu nfs server, with gigabit, and without. So as to determine wherther this is a Deb/Ubuntu issue or something for upstream

Then, is this an nfs bug or a kernel bug, if kernel, what part, certainly not the nic driver.

 *when* I get some of the stack of broken laptops working I can try fast-ethernet. But at this stage it looks like gigabit is the issue.

Other transfers dont seem to do this, then again, most others are much slower (aka samba, scp)

This is pretty killer for any home network, cant believe more people do not experience this... what is it with our setups?

NFS version? I use 4 on the server.
blah!

---

### Post by greenhat on 2010-05-24
I'm having the same kind of problems with an unresponsive/semi-frozen system doing a large copy (50 files/147 Gb) from a local Lucid ext4 HD connected with a gigabit ethernet nic on a 10/100 switch to an NFS share on another Lucid box (ext4) with gigabit ethernet.

I say it's semi-frozen because it's still working according to the system monitor which updates every few minutes, but I can't really do anything else on the box because it's soooo slooooow.

---

### Post by Lepy on 2010-05-25
The problem may be related to gigabit as I have only experienced complete lock-ups using gigabit. I don't usually do large transfers from laptops because I lack an N router, and while I have noticed nautilus lag/system slowness during G speed transfers, they always complete without a lock-up.

All computers are gigabit wired to a netgear 1000 switch, including a 10/100/g router that assigns static IPs. The heaviest used v4 NFS shares reside on a FreeNAS with raidz1 ZFS v13 pools.

I have attached a netgraph image with a wired (top) and wireless (bottom) nfs transfer. The same file was first moved from the nas and then moved back to the nas. Spikeyness may be due to the way ZFS checksums all files.

---

### Post by JeffPH on 2010-05-28
This is happening to me to...

My System:

Intel Atom Ion with Atheros gigabit network card.
Ubuntu 10.04 LTS 
2.6.32-22-generic kernel

When I use FTP from Nautilus to transfer large files (basically mkv's) from PC to NAS, NAS to NAS my desktop PC hangs after 1-2 mins of file  transfer. This is usually faster about 13-15 MB/sec.

When i just use samba/nfs transfers there are no problems but the speed is slow at 2-3 MB/secs.

I have been searching the net and it seems there are a lot people having problems with this too..... Hope someone can find a solution as I am backing up 4TB and this will take days :(

---

### Post by leespa on 2010-06-04
Hi All,

I am experiencing very similar NFSv4 sporadic file transfers as well. This was preceded by crappy Samba performance that could also corrupt large 10+ GB files after it dropped from 20 MB/s to 12 MB/s; Samba sometimes finished, sometimes didn't.

NFS seems to finish, but actually appears to slower overall than Samba was.

It's difficult to get a handle on actual NFS write to server speed I am getting since Nautilus reports the xfer happening in 200-300 MB 'gulps' and then stops.

Server:
Atom 330 mobo [ECS 945GCD-M (V1.0)], 4GB DDR2, Mythbuntu 9.10, NFSv4

Client:
Core 2 e8400, ubuntu 9.04, NFSv4, 4 GB DDR2

Network:
ALL Gigabit, 2 x 8 port DLink DGS-1008D

I have been banging my head against the wall RE this for quite some time. Normal networking tests are all A-OK. TCP iperf test from client to server for instance can push down 840 Mbps consistently.

I believe the NIC on the server is an Atheros as well...

*-network
                description: Ethernet interface
                product: Attansic Technology Corp.
                vendor: Attansic Technology Corp.

NIC on client is NVIDIA
 *-network
             description: Ethernet interface
             product: nVidia Corporation
             vendor: nVidia Corporation

I'll do some more digging as well and report back here if I find anything.

---

### Post by leespa on 2010-06-04
Some more similar posts...

[http://ubuntuforums.org/showthread.php?t=1162724&highlight=nfs+large+file](http://ubuntuforums.org/showthread.php?t=1162724&highlight=nfs+large+file)

[http://ubuntuforums.org/showthread.php?t=1357352&highlight=nfs+large+file](http://ubuntuforums.org/showthread.php?t=1357352&highlight=nfs+large+file)

---

### Post by jolig on 2010-06-06
Hello,

Same here:
Client is Lucid 64bits
Server is freenas

I would say it was working fine when I was in Ubuntu 9.10 but as I've updated my freenas server recently, I am not 100% sure it is related to Ubuntu or freenas.

Any, it sux as samba share or ftp are working fine (& faster!) both of them while nfs is just freezing my computer (client) :(

---

### Post by zackiv31 on 2010-06-06
I've had this problem on numerous Ubuntu distros for over a year now... very frustrating.  Will be trying to see if fedora suffers from similar problems tonight.

Has this specific bug been filed?  I'm also on gigabit.

---

### Post by jolig on 2010-06-10
Up the thread to see if anyone has an idea ?

---

### Post by leespa on 2010-06-10
Is there any graphical utility that can record overall system throughput; uplink + downlink; that people can recommend? 

Ideal if it could save/export the data too. 

I've used iperf, system utility/monitor, iptraf, etc. for looking at near real-time throughput, but it'd be nice to be able to see actually NFS throughput recordable in graph form...

I'd use this for benchmarking + troubleshooting purposes on this issue. 

Thanks

---

### Post by zackiv31 on 2010-06-13
I've noticed that I only have problems when writing to my nfs mounts, and not reading from them.

excerpt from fstab mount:

```

nfs		  tcp,intr	  0	0

```

EDIT: I have complete lockups from wireless to NFS writes... I don't think its a gigabit issue.

---

### Post by jolig on 2010-06-19
The simple fact to extract a big archive (rar/zip) from my local HDD to my local HDD make my computer freezing while the unrar is processing (it take about 25% of my CPU ressources) and I last in about 1 minute for a couple of GB archive which seems to be fine.

I do not have anything strange in dmesg.

Any help to find what's going on ?

---

### Post by leespa on 2010-06-19
Some more info; no resolution.

**Systems**
-----------------------
Server = Atom 330 mobo [ECS 945GCD-M (V1.0)], 4GB DDR2, Mythbuntu 9.10, NFSv4

Client = Core 2 e8400, ubuntu 9.04, NFSv4, 4 GB DDR2

Network = ALL Gigabit, 2 x 8 port DLink DGS-1008D

**Problem**
-----------------------
Using NFS v4 standard mount options and combo of other tests an NFS write of a large file; 8.4 GB in this test case; will start off with a very large burst of 60+ MB/s and then more or less level off at an anemic 12 MB/s. 

Looking at the throughput graphs, however, this is a very far from stable 12 MB/s; throughput goes up and down like a bride's pajamas...**[COLOR="Red"]OVERALL NFS WRITE SPEED SUCKS[/COLOR]**.

[COLOR="Blue"]See attached pictures; bursty_2.png + bursty_3.png[/COLOR]

**What I Have Done To Try And Isolate The Problem**
-----------------------
server = Load is very high; 15+ when doing the NFS xfer but CPU, IOWAIT, MEM are NOT conspicuously high as well; so I checked things like nfsstat -rc, iostat, netstat -ic, iotop, etc and don't see obvious issues. 

[COLOR="Blue"]See attached text file; bursty_txt.txt for details.[/COLOR]

**What I Have Done To Try Fix The Problem**
-----------------------
* note: have been using default mount of:
sudo mount -t nfs4 192.168.YY.XX:/temp0 /mnt/nt_tmp/
unless otherwise noted.

-- increased amount of nfsd threads on server from 8 to 32 = no change
-- mtu on both ends from 1500 to 9000 = no change
-- mount option rsize,wsize from default of 524288 to 262144 = no change
-- mount option rsize,wsize from default of 524288 to 1048576 = maxes out at 524288, no change

**Overall Results**
-----------------------
-- Xfering a 8.4 GB file over Gigabit NFSv4 = 14m53s

-- Compared to Samba it is SLOWER; Samba consistent 16 MB/s and 9m30s for same file

-- What I'll try next is a) 100 Mbits switches on each end; b) faster server...eventually.

**Closing**
-----------------------
-- At this point I am wondering if the atom330 server is just too slow?! Units seems to work well; browser, etc still very responsive even when the load says 15+ for the NFS xfers...

-- **Any one have any other ideas for me to test?**

Thanks

---

### Post by leespa on 2010-06-25
FYI. From what I can tell the cpu + mdadm combo is NOT the issue / bottleneck...

<user>@atom330:~$ time dd if=/dev/zero of=/home/<user>/raid5/test.dd bs=8k count=1000000
1000000+0 records in
1000000+0 records out
8192000000 bytes (8.2 GB) copied, 137.285 s, 59.7 MB/s

real	2m17.716s
user	0m1.420s
sys	1m21.340s

<user>g@atom330:~$ time dd if=/dev/zero of=/home/<user>/raid5/test.dd bs=8k count=1000000
1000000+0 records in
1000000+0 records out
8192000000 bytes (8.2 GB) copied, 148.631 s, 55.1 MB/s

real	2m31.178s
user	0m1.590s
sys	1m33.970s

<user>g@atom330:~$ time dd if=/dev/zero of=/home/<user>/raid5/test.dd bs=8k count=1000000
1000000+0 records in
1000000+0 records out
8192000000 bytes (8.2 GB) copied, 143.58 s, 57.1 MB/s

real	2m25.909s
user	0m1.620s
sys	1m32.640s

This same test with an 8.4 GB file over NFSv4 took 14m53s.

dd testing the load never went above 2.5 either...was 15+ for the NFS transfers; MUST be something on the networking side?

Funny thing is an iperf test to this server averages 840 Mbits/sec -OR- 100+MB/s using TCP so I'm not sure why these file xfers are so terrible.

---

### Post by jolig on 2010-06-27
on my side, it seems that my system has problems when reading large local files as :
1- I am able to read from my NFS share with good speed (30-40MB/s) and write it to my local HDD
2- When I try to copy a file from my local HDD, My computer freeze randomly
3- Same Computer, Same OS, Same files (copied/read to a NTFS partition) I am experiencing the exactly same behavior
4- Same Computer, Same OS, Same files but using CIFS produce the same behavior
4- Running on the same Computer, but from Windows XP, I do not get any freeze.

I'm am now trying with an Ubuntu LiveCD 9.10 and i'll keep you updated...

---

### Post by jolig on 2010-06-27
No performances issues with my LiveCD 9.10 :-(

It seems to be definitly a problem with 10.04 on my computer...
Anyone has an idea ?

---

### Post by Lepy on 2010-06-29
I also get great read speeds from NFS shares (on my nas, check my first post). 
Local file copy is fine though. 

I setup a CIFS share on the nas and proceeded to copy a 1.2 gig file over CIFS and NFS (to different folders, though they reside in the same ZFS pool).
The NFS transfer completed but would lock up for a bit then burst write.
The CIFS transfer went fine. It did not lock up, the percentage bar steadily moved forward, and for the first time, I feel like I had an accurate write speed displayed through nautilus.
The server showed 30% memory usage and 30% load average (dual core proc) during both transfers.
I've attached another network graph. The CIFS transfer is first and looks much less erratic than the NFS transfer.

I am fairly sure this problem occurred in 9.10 with less frequency. I transferred a terabyte or two to the nas in only a few separate transfers under 9.10. I feel like it would have taken many more transfers under 10.04.
I have tried messing with mtu as well as rsize and wsize. Doesn't help.
The only other export options I can think to change are sync and async, but I have not been able to test this as FreeNAS does not seem to allow this change.
This is all I have for now.

---

### Post by ScarletPea on 2010-06-29
RIIIIGHT!
 Some (only some) PROGRESS!
ok Ime yelling, but finally getting somewhere.

 It turs out we have two (maybe unrelated) Problems, with potential solutions, so please please try these and let me know your milage:

[LIST=1]
 [*]Client Freezing
  [LIST]
   [*]Apply the following patch to your (client) kernel
[https://bugzilla.kernel.org/attachment.cgi?id=26815]("https://bugzilla.kernel.org/attachment.cgi?id=26815")
   [*]I think you do this as follows (ish)
   ```
sudo apt-get install linux-source
cd /usr/src/
wget "https://bugzilla.kernel.org/attachment.cgi?id=26815"
tar -xjf linux-source-2.6.33.tar.bz2
cd linux-source-2.6.33
patch -P1 < ../
fakeroot make-kpkg --initrd --append-to-version=-nfs-fix kernel-image
sudo dpkg -i ../liux-image-2.6.33-nfs-fix...
sudo mkinitramfs-kpkg -o /boot/initrd.img-2.6.33-nfs-fix 2.6.33-nfs-fix
reboot, choose new kernel w/grub   
```
    note the mkinitrd-kpkg, the initrd hook needs to be setup properly, and I havnt figured it out quite right yet... maybee you have 8) Everything above is approximate as I havnt done it quite like that... follow _some_ of: [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile"), ime old fashioned I guess
  [/LIST]
 [*]Intermittant Transfer
   Aparently this could be the vm stuff on the server, try adjusting the following:
 ```

echo 40 >  /proc/sys/vm/dirty_expire_centisecs; \
echo 1 >  /proc/sys/vm/dirty_background_ratio; \
echo 20 >  /proc/sys/vm/dirty_writeback_centisecs 
```
 These numbers didnt quite work for me so check before you do what things are set to. Would be interesting to know what you had before, and what fixed them problem, please report... so check with:
 ```
cat /proc/sys/vm/dirty_expire_centisecs;\
cat /proc/sys/vm/dirty_background_ratio; \
cat /proc/sys/vm/dirty_writeback_centisecs
```
[/LIST]

Let me know please, the more feedback the better!

---

### Post by ggerri on 2010-07-02
Having the same problem for a while now. First time that Win7 (my office notebook) is doing better here than Ubuntu :-(

ok, this is how I just solved it for myself:

1. in NAS nfs settings: disabled sync mode
2. changed nfs entry in fstab from

[PHP]192.168.1.2:/media     /media/nas/media      nfs  rsize=8192,wsize=8192,timeo=14,intr[/PHP]

to 

[PHP]192.168.1.2:/media     /media/nas/media      nfs  rsize=32768,wsize=32768,timeo=14,intr[/PHP]

Hope that works for you as well :-)

---

### Post by ScarletPea on 2010-07-03
Thanks ggerri,
 What problem were you experiencing please,
  client lockups? intermittant bursting transfers, both...?

 Ille try what you suggested anyway and see what milage I get!

cheers.

Jasper

---

### Post by ScarletPea on 2010-07-08
> **ggerri said:**
> 
[PHP]192.168.1.2:/media     /media/nas/media      nfs  rsize=32768,wsize=32768,timeo=14,intr[/PHP]

Hope that works for you as well :-)
 naaa didndt help with the lockups or intermittant transfers here.

So far best results with patched kernel and chnaging vm_dirty etc.

 Any other takers?

---

### Post by ScarletPea on 2010-07-26
The fix by patch and modifying vm\etc* mostly worked for me.
Theres be no real comments to the contraty, Ille mark this solved.

Thanks all.

---

### Post by leespa on 2010-07-30
**SUCCESS** for me as well!

In my case, however, it was the **'sync' option causing all the grief**. I followed a couple NFSv4 guides and decided to use the 'sync' versus 'async' since it sounds safer...

Changed /etc/exports to:

/exports 192.168.x.y(rw,fsid=0,**insecure,async**,no_subtree_check)
/exports/share0 192.168.x.y(rw,nohide,**insecure,async**,no_subtree_check)
/exports/temp0 192.168.x.y(rw,nohide,**insecure,async**,no_subtree_check)

AND **my NFSv4 WRITE speeds went from 7 MB/s to 80MB/s** - quite an improvement! Did md5sum on xfers and all is well.

I also tried the /proc/sys/vm/* changes suggested above. Got 80 MB/s WITH the changed values, but also got same 80 MB/s after reboot and /proc/sys/vm/* values reverted back to orignal speed. Therefore, aysnc made all the diff for me...

time dd if=hd1c_8x4GB.mpg of=/mnt/nt_tmp/hd1c_8x4GB.mpg	
17676766+1 records in	
17676766+1 records out	
**9050504616 bytes (9.1 GB) copied, 113.261 s, 79.9 MB/s**	
real	1m53.372s

---

### Post by ganjaman2009 on 2010-07-31
I'm using a DLINK-323 as my NFS server with firmware 1.08.  I'm experiencing the same graphical freezes tho' my ssh sessions are unaffected if I remote in.

My desktop is 2.6.32-24-generic #38-Ubuntu SMP and the /etc/fstab entries are:

nas:/mnt/HD_a2/ganja /media/NAS nfs rw,nolock,rsize=32768,wsize=32768,timeo=14,intr,hard,tcp,async 0 0

Any ideas?

---

### Post by leespa on 2010-08-01
ganjaman2009:

All I am using for mount command on the client is:

mount -t nfs4 192.168.x.y:/temp0 /mnt/nt_tmp/

NFSv4 will automagically figure out the best wsize,rsize. I manually tried tweaking this to no avail.

What fixed things for me is to use the 'async' option in /etc/exports as indicated in post #27. See if you can tweak on the DLink-323 - I know its Linux based too...

Also, to see current nfs mount config run this on the client:

nfsstat -mounts

/mnt/nt_tmp from 192.168.x.y:/temp0
 Flags: rw,vers=4,rsize=524288,wsize=524288,namlen=255,hard,nointr,proto=tcp,timeo=600,retrans=2,sec=sys,clientaddr=192.168.x.y,addr=192.168.x.y

Hopw this helps a bit.

---

### Post by Lepy on 2010-08-01
I was able to change my FreeNAS mounts to async by adding vfs.nfsrv.async 1 to its sysctl.conf. This seems to alleviate my problems client freezing problems.

Allowing NFSv4 to set the r/wsizw seemed to make my transfer graph a little less spiky. 

I have not tried the patch, but if I encounter any more problems, I will report back.

---

### Post by leespa on 2010-08-01
FYI. My xfers still do look 'spikey' so to speak even with these changes.

The crucial part now is that average WRITE speed to the NAS is 80 MB/s...takes < 2 min to do an 8 GB xfer whereas before it was 16 min or longer.

---

### Post by leespa on 2010-08-06
Update:

Pushing NFSv4 over Gigabit to a 5 x 1.5 TB raid 5 array running mdadm:

time dd if=hd1c_8x4GB.mpg of=/mnt/nt_tmp/hd1c_8x4GB.mpg
17676766+1 records in
17676766+1 records out
9050504616 bytes (9.1 GB) copied, 90.6353 s, 99.9 MB/s
real	1m31.555s

**99.9 MB/s** !!... can't get much faster on gigabit...that's approx 800 Mb/s without the overhead in consideration...

---

### Post by brdhse1 on 2010-08-07
I want to start by restating the original problem:
Large NFS copies locks up/hang desktop

I tried everything suggested up to this point (async, proc changes, etc) without any success; large files still freeze my Lucid desktop - sometimes to the point where a restart is required.  

Patching the kernel is hardly a solution; at best it is a workaround.

This seems like a pretty basic and serious bug.  If a Linux desktop (client) cannot send a large file via NFS to another Linux desktop (server) without completely locking up, an alarm with flashing red lights and sirens should be going off somewhere.  

I would change my shares to use cifs instead, but this has some widespread and unresolved problems of its own (e.g. [http://ubuntuforums.org/showthread.php?t=1521653]("http://ubuntuforums.org/showthread.php?t=1521653")  one of many threads on the topic)  

I can't believe Lucid made it out of Beta with these problems.  I know this is somewhat of a rant, but this is a bit ridiculous.  

What can we do to get this fundamental problem seriously looked at?

---

### Post by leespa on 2010-08-07
brdhse1:

what mechanism are you trying to do the copy with? command line cp, nautilus, rsync, dd? one or all of the above?

have you ever happened to catch anything in dmesg? can you ssh into the box while this happens to see what is transpiring?

---

### Post by brdhse1 on 2010-08-07
> **leespa said:**
> brdhse1:

what mechanism are you trying to do the copy with? command line cp, nautilus, rsync, dd? one or all of the above?

have you ever happened to catch anything in dmesg? can you ssh into the box while this happens to see what is transpiring?

I tried command line cp and Nautilus with the same results.

I can ssh into the box but I cannot see what is going on.  dmesg doesn't show anything interesting.

---

### Post by olesk on 2010-08-08
If I am not mistaken, this is a know bug,[ which is fixed in 2.6.35-rc6]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/561210"). So hopefully this is only a matter of time.

---

### Post by ScarletPea on 2010-08-11
> **brdhse1 said:**
> 
Patching the kernel is hardly a solution; at best it is a workaround.


 In this situation, for some people patching IS the solution.

Its not hard, you can do it, and it will stay with you until you update your kernel, which you should not need to do until Maverick, at which case some other annoyance may creep in and you need to patch the Kernel.

The point here is that
i) This is a solution
ii) This problem does not affect many people, and as it affects YOU it is a damn good one.
 
 I was extreemly grateful that the elite core of NFS devs took time out to give us this solution

Have a go. Its not too hard

---

### Post by b00nish on 2010-10-14
Hey

I still have the problem of a NFS client that locks up my whole system on Kubuntu 10.10.

The patch that was posted before seems to be for an older version/revision/whatever of the kernel (.33 instead of .35) so I'm not sure if it would be a good idea to apply it.

Does anyone know how to get a NFS client proberly working in 10.10 od do I have to downgrade to good old 8.04 - the last version without major problems for me.

---

### Post by dmendels on 2010-10-24
I seem to have fixed my "NFS client locking while copying large files" problem by applying part of the solution reported in reply #23. In particular, I changed the NFS entry in /etc/fstab as suggested.

Thanks!

[EDIT] Spoke too soon, problem still occurs, possibly with less frequency.

---

### Post by b00nish on 2010-11-21
Any news on this issue?

It's still interfering my work with Kubuntu 10.10.

I also tried several things like a fresh installation but the same issue occurs there (while it's still working without problems in Kubuntu 8.04)

I also posted the issue on the Ubuntu Bugtracker ( [https://bugs.launchpad.net/ubuntu/+bug/661294](https://bugs.launchpad.net/ubuntu/+bug/661294) ), but they don't seem to care, that something totally unimportant like NFS doesn't work in their latest release... -.-

---

### Post by bedge on 2010-11-21
This has been a long term problem with Ubuntu, since 10.04. It's an embarrassment and a travesty that they claim enterprise class usability when simple NFS transfers can hang any machine.

---

### Post by leespa on 2010-11-21
Hi All.

For me the main improvement was using 'async' mount options, HOWEVER, I do occasionally experience significant slowdowns when xferring large files...throughput will drop down to nothing and then pick back up to 100+ MB/s again after a few minutes like nothing happened.

I haven't yet determined if this is a RAID-5 or nfs issue...happens sporadically, not always a problem.

---

### Post by olesk on 2010-11-21
> **leespa said:**
> 

I haven't yet determined if this is a RAID-5 or nfs issue...happens sporadically, not always a problem.

I have the same problem using RAID 10 (the real thing, not 1+0) so I don't think it's your  RAID5. Upgrading to the latest kernel on my 10.10 solved the crashes however, so this is the only problem that remains for me.

I have seen another oddity though, when copying large movies to my NFS server (a Mac), which is that Ubuntu hangs when trying to generate thumbnails for existing movies (or perhaps of the movie it is transferring) - using 100% CPU and killing pretty much everything. A kill -9 on the process has no effect.

I presume the solution is to disable thumbnails for remote files, but I have already done this to no effect on Nautilus 2.32.0. Nautilus still insists on creating thumbnail on NFS shares - perhaps because it considers them local. If you're having trouble with large files, check if it is movie files that's causing the problem or also ISOs/backups/other large files that freeze, or better yet - try copying from the terminal without having any nautilus windows for the destination open. The problem might actually not be NFS, but Nautilus.

---

### Post by leespa on 2010-11-21
When I see these occasional 'slowdowns' its via rsync in gnome-terminal. 

I also noticed copying files to/from same RAID5 volume on the local server is slower than stink...would likely be faster to transfer off and back onto machine. ;-)

Thankfully I don't do that operation very often.

---

### Post by b00nish on 2010-11-22
@ olesk

In my case it can't be Nautilus since as KDE user I don't even have it installed. Of course I also tried 'cp' from the terminal and did dozens of other tests.

However since yesterday they finally accepted the bugreport on the Ubuntu bugtracker, so there's hope that the Devs will look at it.

---

### Post by olesk on 2010-11-22
> In my case it can't be Nautilus since as KDE user I don't even have it installed. Of course I also tried 'cp' from the terminal and did dozens of other tests.
 
However since yesterday they finally accepted the bugreport on the Ubuntu bugtracker, so there's hope that the Devs will look at it.
 
Interestingly, there was an active bug on the system hangs during NFS transfers that now is closed due to a specific fix for this problem in a recent kernel update. If the hangs are still there on the most recent kernel versions, that bug should be reopened (sorry, don't have the link to the relevant bug at my current location). 
 
As for the slowdowns I would like to track that bug as well - do you have the link?

---

### Post by b00nish on 2010-11-22
No, sorry, I don't have any informations related to the slowdown.

(If your system crashes some seconds after the start of the transfer, you'll not notice any suspected slowdown ;))

All I can say is stated in my Bugreport ( [https://bugs.launchpad.net/ubuntu/+bug/661294](https://bugs.launchpad.net/ubuntu/+bug/661294) ). And this is, that the lock-up occurs with the 10.10 and the 10.04 kernel (2.6.35 resp. 2.6.32) and that they don't occur on my old 8.04 installation. I did not test other kernel versions.

EDIT: Oh, maybe im missunderstood you. If you meant the link to track a bug, it's: [https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)
(You'll need a Launchpad-Account, tough)

---

### Post by nsx241 on 2010-12-02
This issue has caused me endless grief on 10.04. I was forced to use cifs due to it, along with the painfully slow transfer rates.

However, I recently upgraded to Ubuntu 10.10 (2.6.35.23), and it seems the issue is resolved. I transferred over several 6GB files without any lockup issues, though the transfer rate seems about 10MB/sec slower than before (when it was working correctly on older releases).

---

### Post by tootlet on 2010-12-04
Happening here with Xubuntu 10.10 (and openSUSE 11.3) x86 version. I was running openSUSE 11.2 on this box with 1 320 Gb hard drive with the OS, swap and home partitions, and 3 500 Gb hd's in RAID5 at my business. One of the hard drive broke on it and one failed on my home server at the same time. So I decided to upgrade to 3 1 Tb hard drives and update to openSUSE 11.3. After I got 11.3 set up I tried to rsync some of my data to the new RAID5 via nfs over a gigabyte network. Froze up after about 5 minutes. Hard reboot was only option that worked. On reboot I got an error message stating that no file system was on md0 and to repair it. Couldn't figure that out so after struggling just decided to try Xubuntu 10.10 which was working okay on another server at home. RAID5 built okay and synced. I could make directories. But if I used rsync or cp to copy my Music folder (50 Gb of mp3's) it froze. I would have to resync about 3 hours then try again. Same thing. Requires a hard boot. my /etc/exports file already is async, I didn't try the kernel patch. Rsync has been successful for me many times in the past over this same network. I'll keep googling but suggestions needed. Thanks,
Tom

---

### Post by nsx241 on 2010-12-05
Spoke too soon. Problem has returned for me. Until this gets resolved, I'm probably going to switch to Fedora.

---

### Post by brdhse1 on 2011-01-18
Anyone?  This is embarrassing, Ubuntu.

---

### Post by andrewrchambers on 2011-01-22
@[nsx241]("http://art.ubuntuforums.org/member.php?u=608828")

FYI I've tried switching to Fedora and my computer still crashes when transferring files over NFS4 - I'm unable to even populate my shotwell library.

I've put an old 100/10 NIC in my machine for the time being until this gets resolved... This is clearly not ideal as I'm mounting /home over NFS and this slows things down considerably but I prefer this option to having complete system lock ups...

---

### Post by akshunj on 2011-03-05
I switched to samba. this issue is ridiculous...

---

### Post by olesk on 2011-03-06
Could we please have the topic changed? The [SOLVED] tag is definitely not appropriate...

---

### Post by olesk on 2011-03-31
It appears I've stumbled over a possible workaround while trying to track down bug reports on this issue. 
 
Mounting the nfs shares with a "udp" parameter, like so, seem to remove the issue for me:
```

nfserver1:/Volumes/Movies on /nfs/Movies type nfs (rw,rsize=8192,wsize=8192,timeo=14,intr,**udp**,addr=10.0.0.98)
```Could someone else please verify? I've done a couple of large transfers that twice hung my system earlier today without the "udp" parameter (Ubuntu defaults to "tcp" unless "udp" is explicitly stated"). UDP should also be faster and on a modern home network, the added reliability of TCP shouldn't really be required unless your switch/router/server drops a lot of packages.
 
**Update: IT appears a concrete fix is today included in the updated 2.6.35-28 kernel (see the change log). Link to bug report: **[**https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585657**]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585657")

---

### Post by rex86 on 2012-03-05
Hello everyone!

Has anyone read some of this stuff? 

[interesting article]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch29_:_Remote_Disk_Access_with_NFS#Troubleshooting_NFS")

The most interesting part starts from **Troubleshooting NFS**.

Also can anyone post the output of nfsstat command? 

Does anyone of you still have the same problem with >2.6.x kernels?

---

### Post by davidjo on 2012-03-15
> **rex86 said:**
> Hello everyone!

Has anyone read some of this stuff? 

[interesting article]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch29_:_Remote_Disk_Access_with_NFS#Troubleshooting_NFS")

The most interesting part starts from **Troubleshooting NFS**.

Also can anyone post the output of nfsstat command? 

Does anyone of you still have the same problem with >2.6.x kernels?

Yes, I have tried with Kubuntu 11.10, Xubuntu and the Mint 12 variants.  All freeze with kernel 3.0 and reading large files (>5GB) from a NAS box connected via NFS.  Not everytime, but repeated reads will provoke the freeze.

I'll try again with Kubuntu 12.04 beta.

---

### Post by davidjo on 2012-04-17
> **davidjo said:**
> Yes, I have tried with Kubuntu 11.10, Xubuntu and the Mint 12 variants.  All freeze with kernel 3.0 and reading large files (>5GB) from a NAS box connected via NFS.  Not everytime, but repeated reads will provoke the freeze.

I'll try again with Kubuntu 12.04 beta.

I've retried this with Kubuntu 12.04 beta 2, and after about 30 copies of a 6+GB file from my NFS shared NAS storage device to my local hard disk, all looks OK.  This is running kernel 3.2, and TCP, not UDP.

Looks like I can finally upgrade my system, which I think is based on the last LTS release!  Thank you.

---

### Post by Qwerty9119 on 2012-04-27
Has this issue been resolved? I see that davidjo was able to testing something out.

Anyone?

Q

---

### Post by Peter Bell on 2012-05-03
I'm getting repeatable lock-ups when copying files from my file server to my ubuntu desktop (11.10 and, now, with 12.04 final).  The lock-up occurs quite early, for instance after 158MB.


The fileserver is running a slackware-based package.  If the server is using a 2.6 kernel, there are no lockups, but as soon as the server is upgraded to a 3.0 (or 3.2) kernel, the lock-ups return.

Perhaps this problem occurs only if both machines are running a 3+ kernel?  Is that the same as nfsv4 support?

What makes it so annoying is that Nautilus refuses to die after the lockup, even kill -9 doesn't work.

---

### Post by Qwerty9119 on 2012-05-04
Appears to be happening in kernels 2.x & 3.x. Tried with Ubuntu 10/11/12.

Currently got a VM with 12.x in 32 bit, same problem.

Very frustrating...

Q

---

### Post by rex86 on 2012-05-14
> **Peter Bell said:**
> I'm getting repeatable lock-ups when copying files from my file server to my ubuntu desktop (11.10 and, now, with 12.04 final).  The lock-up occurs quite early, for instance after 158MB.


The fileserver is running a slackware-based package.  If the server is using a 2.6 kernel, there are no lockups, but as soon as the server is upgraded to a 3.0 (or 3.2) kernel, the lock-ups return.

Perhaps this problem occurs only if both machines are running a 3+ kernel?  Is that the same as nfsv4 support?

What makes it so annoying is that Nautilus refuses to die after the lockup, even kill -9 doesn't work.

I've done some experiments and after doing everything stated in the how-to of my previous post I do get quite stable nfs server. While I'm copying files **from** the server **to** the client the server responds more slowly but still responds. The problem is when I'm copying files from the client to the server. It locks-up even with small files ~ 150MB. I think it has something to do with the copy speed. At first I get speeds of 300MB/s (I have an SSD) and then everything kinda lock-up until everything get copied to the server. After that everything gets back to normal.

I think we should try to find an option that limits the copy speed to the server. That way we might not get lock-ups. 

If the server fails the programs using it will lock-up and wait for response indefinitely. This happens with every program using the nfs share. I believe that adding options bg,soft should help and I'm seeing _some_ improvement with Dolphin (you can kill the locked-up, start new one and it will work fine), but for other programs like Amarok that doesn't help.

I think that we need to look into the possibility of creating a fake nfs server and using that one to unlock the programs in case of the original server fails.

---

### Post by BjBlaster on 2012-06-22
I can also verify that this is happening on 12.04 LTS lubuntu. 

I have a 12.04 NFS server and it is ok with 10.04 clients but not 12.04. Only 12.04 -> 12.04 NFS seems to lock it up, however when it locks up on the 12.04 clients, the 10.04 clients are still screaming along! It's seems to be a client issue with the latest nfs-common package. If I use sshfs it works perfectly...

My 10c.

Bj

---

### Post by BjBlaster on 2012-06-22
I have managed to stop the lockups by using tcp instead of udp which fixes it for me!

192.168.2.1:/mnt/backups /mnt/backups nfs rsize=8192,wsize=8192,nolock,timeo=14,intr,proto=**tcp**,port=2049

Suprising seeing it has no trouble on 10.04....

Cheers

Bj

---

### Post by hans.hook on 2012-07-06
This is definitively *NOT* Solved.
==================================

I have Ubuntu 10.04 server amd64 and with kernels 2.6.35-32-server or 3.0.0-22-server the problem is apparent (i have not downgraded to original kernel yet but is there a point in even trying???)

I have tried with tcp or udp, sync or async - no change.
I have replaced NICs to all intel...

Clients Ubuntu 11.10 and 12.04 all have the same problem of completly freezing up.
KDE with nfs mounted home shares is impossible if more than one client
is started ther will be a deadlock/freeze often requireing hard (power off) reset.
Nothing in the logs as far as I can see...

Ubuntu 8.04 or 10.04 clients have no problems whatsoever  in the same setup.

This is really sad - I have been using NFS for home shares for something like 8 years straight with very few problem before.
10.04 introduced the problem related to bootwait - but that was solvable.. 
My conclusions is that eiter Ubuntu clients 11.10 and 12.04 are not fit for use in traditional nfs setups or the linux kernel > 3.0.0 is degraded...


First time with Linux for 8 years that I am without options...
What to do? 


Regards

---

### Post by hans.hook on 2012-07-06
Point of clarification:

Problems with freezing occurs only with more than one NFS client running 11.10 or 12.04.
One client works fine.
Several 10.04 clients with one 11.10 or 12.04 works fine.

The funny thing though is that I use kernel 3.0.0 in my 10.04 clients...

Is this an indication of portmap being replaced by rpcbind is the root cause, or something like that???

Any help greatly appreciated!  

Regards

---

### Post by rex86 on 2012-07-14
I couldn't find what's wrong with it, so I switched to samba. It looks like nfs has severely degraded for regular users and especially for those who use 
it over wifi.

---

### Post by ookami on 2012-07-20
This is certainly not solved. I'm experiencing the same symptoms, i.e. slow transfers, periodic hangups of Nautilus or sometimes entire desktop, when writing from a Ubuntu 12.04 client to a rooted (for the purpose of adding NFS support, oh the irony) Buffalo LS-XL NAS server which is running a Debian derivative Linux OS.

I really think this is rather embarrassing. NFS is after all supposed to be the less resource intensive and faster *NIX-land alternative to SMB, yet not only doesn't it do DNS-SD but also performs bugger all on the most popular Linux distro out there. This really needs to get fixed.

---

### Post by dpg77 on 2012-08-01
This is so Stupid a Fix but it worked for Me

Just edit the /etc/hosts 
and either remove all the localhost references in both ipv4 and ipv6 on both systems.
after doing this went from speeds of 100k/sec over 63Mbits/sec and also got rid of the stupid avahi warning about local domain all in 1 hit.

Hope this will help get to the bottom of this and would love to hear if this fixes the speed isssues for other people as well

If this fixes the issue for other people we may need to look at avahi daemon or the package that supplies the /etc/hosts file

Very Happy again here.


:P:P:P:P


Quick Update Tried this same setup today and back to slow speed.
One thing i Noticed though was that if i restart both server and client at same time and able to start the File Transfer before the Avaya Warning Message appear then I am able to get a good copy speed if i wait log enough for the warning to come up it is really slow.
Network Service Discovery Disabled Popup.
 Not sure if this is related or it is something else starting up in the backgroup that is effecting it.

---

### Post by icedfusion on 2012-08-26
Has a bug been raised for this - I thought I had some nic issues until I read this thread.

The original poster needs to unmark this solved, as it certainly isn't

ice.

---

### Post by icedfusion on 2012-10-03
I tried all sorts of things to solve this issue - it was happening in SMB as well.

My resolution was to move to the 32bit server - it now works as expected and as it is the pae kernel, i can use more than 4GB - what is not to like?
:guitar:
ice.

---

### Post by giuliano1969 on 2012-10-12
I'm having good result with the following configuration:

4 IBM systemx, ALL with ubuntu 12.04.01 64 bit

server, /etc/exports
/home/cfduser/OpenFOAM 192.168.0.19(rw,sync,root_squash,no_subtree_check) 192.168.0.21(rw,sync,root_squash,no_subtree_check) 192.168.0.23(rw,sync,root_squash,no_subtree_check)
192.168.0.17:/home/cfduser/OpenFOAM /home/cfduser/OpenFOAM/ nfs4 _netdev,auto 0 0


clients /etc/fstab
192.168.0.17:/home/cfduser/OpenFOAM /home/cfduser/OpenFOAM/ nfs4 _netdev,auto 0 0
#192.168.0.17:/home/cfduser/OpenFOAM /home/cfduser/OpenFOAM/ nfs _netdev,nfsvers=3,proto=tcp,noac,auto 0 0


-----------------------------------------------------
writing a dd test on a local directory I get 90Gb sec. We have all the 4 nodes on one HP switch 1910.

If I run the dd test on a nfs directory, like 
time dd bs=1M count=128 if=/dev/zero of=/home/cfduser/OpenFOAM/speedtest2 conv=fdatasync

I get a speed of 20 Gb/s
not so good, not so baad... (considering conv=fdatasync)

What are your values ?

---

