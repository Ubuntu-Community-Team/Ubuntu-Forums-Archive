---
title: "Pathetic (SLOW) smbfs/cifs Performance and Good gvfs Performance: Some Findings"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by user667 on 2010-09-19
Pathetic smbfs/cifs Performance and Good gvfs Performance - Interesting Observations

_**Background:**_

For years I've been experiencing absolutely pathetic smbfs/cifs performance (10 MB/sec throughput) on my home network, running a mix of 32 and 64 bit Ubuntu systems.  Typically I try to fix this 1-2 times per year, and give up, resorting to using FTP to ship large files around my network.

Today I once again tried to crack this nut, without success, but with some interesting findings...


**_Findings_**

0) I again tried using smbfs/cifs with the same results as always.  I tried setting wsize and rsize larger (per many threads on this topic), without success.  Nothing new here: smbfs and cifs suck as always.

1) My first interesting finding was when I tried mounting via Nautilus w/ gvfs instead of via fstab.  When I use gfvfs, I get very solid performance, in the range of 65-75 MB/sec for large files (about what I would expect, given hard disk limitations).  

2) I tried, without success, to see the mounting parameters that gvfs uses, in the hopes that all I need to do is replicate these in my fstab configuration.  Despite a couple hours of poking through /proc and /var/log, and trying to use gvfs-info, I was not able to determine these.

3) Interesting Finding #1: I then tried watching things in Wireshark, and this is when things got interesting.  If I am interpreting things correctly, wsize and rsize settings map to "Write AndX Response" messages in the file sharing protocol, and mount.cifs appears to limit wsize and rsize to a max of 4096.  Setting them lower than that resulted in a change in messages caught in Wireshark, but setting them above 4096 did not.  From this, _I infer that mount.cifs limits wsize and rsize to a max of 4096_.  Nothing in the documentation about this though.

4) Interesting Finding #2: After observing the strange mount.cifs behavior, I then tried mounting via gvfs through Nautilus.  I then observed traffic that indicated that gvfs sets rsize/wsize to 65536.  Perhaps this is why performance is so much better with gvfs.


**_Notes:_**

Regarding items 3 and 4 above, I observe messages in Wireshark that read, "Write AndX Response, FID: 0x..., XXX bytes" where XXX is a max of 4096 for mount.cifs, and 65536 (not 65535) for gvfs.



**_Questions:_**

1) What's going on here?  What does one have to do to get decent smb performance (besides going though Nautilus to use gvfs)?

2) Is there any way to force wsize and rsize to larger values than 4096 for mount.cifs?

---

### Post by Jaapie on 2010-09-20
Exactly the same issue here. Thanks for your findings. 

Read speeds:
mount: 2.6MB/s 
gvfs: 25MB/s

I seem to remember performance had been quite decent earlier, so am inclined to think a fairly recent update causes this issue.

My findings:
#1 I only suffer from this issue on my desktop and not my laptop, thought they both run lucid x64, so this issue may be hardware related?

Board: Gigabyte MA-790FXT UD5P Motherboard + Phenom II 1090T
LAN: 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

---

### Post by Enigmatic on 2010-09-20
I'm seeing the same and I'm not sure what's to blame. Windows machines can access at full Gigabit speeds, and while much slower, at least gvfs is still superior to mounting the cifs share. I'm seeing 50MB/s both ways on gvfs, and about 30/15 with mount. Card is Intel Corporation 82572EI Gigabit Ethernet Controller (Copper) on the e1000e driver.

---

### Post by user667 on 2010-09-26
I've had this issue with multiple NICs.  I really don't think it is a NIC issue.

---

### Post by Vide on 2010-09-27
Well, I have the exact opposite results: gvfs slooooooow (~6MB/s) and cifs kernel module (mount.cifs) a decent speed (~55MB/s), even if it should be better (the I/O subsystem can achieve at least 100MB/s).
Out of curiosity, how did you perform the test? dd? what kernel are you using? what samba version on the other side? thanks

---

### Post by luvshines on 2010-10-10
Did you had a chance to go through this:
[http://ubuntuforums.org/showthread.php?t=1429532](http://ubuntuforums.org/showthread.php?t=1429532)

I was just searching through the forum to get some answer to my issue and came through your thread and the one posted above. Thought it cud help :)

---

### Post by Enigmatic on 2010-10-10
I tried the various wsize and rsize settings they had, remounted the share, but no changes in speed whatsoever! Switching to NFS wouldn't be a true solution.

---

### Post by Enigmatic on 2010-10-14
Some new information. I opened up Wireshark and saw many, many QUERY_PATH_INFO transmissions. It's very strange because they reference all sorts of locations. Maybe something Nautilus is doing? I notice this whenever I navigate through the share. If I'm transferring files I do not notice this.

I'm using the e1000e driver for my NIC, perhaps this could be part of the problem?

---

### Post by Enigmatic on 2010-10-14
Tried NFS - get 70MB/s both ways. Guess it's time to dump cifs until it gets fixed.

---

### Post by mdalacu on 2010-11-15
It's not CIFS related, it's Nautilus. To test it just copy the files using cp command from terminal, you will get a 10X boost in speed. You can also use DoubleCommander.

---

### Post by dragon99 on 2010-11-15
> **mdalacu said:**
> It's not CIFS related, it's Nautilus. 


m8, I share your pain. I have had the same poor performance with samba since 9.04, and FTP is only marginally faster. If its Nautilus causing the upset, why has this not been corrected by canonical in over 2 years? Seems like every time I look at the forum, nothing much has improved, still the same recurring problems. Why are there so many problems with both wireless & wired network? It doesnt encourage any new user (particularly an ex windows user) to stick with ubuntu.

Although I have enjoyed the ubuntu experience since feisty, this one issue is enough to make me look a little more seriously at mac as a replacement to win XP/Vista/win7. I've spent a lot of hours trying to resolve this issue, read a lot of threads, researched other ubuntu knowledgebases. I have re cabled all the cat5 on the home lan & pinned them exactly the same, spent many dollars replacing switches & other network equipment I thought was faulty. Nothing I have tried has corrected this problem.

The slow transfers are disgusting particularly between lucid and my FreeNas server. So slow in fact that I have been forced to use an XP laptop to transfer in excess of 2 TB data to the FreeNas. As a linux user, I really dont want to maintain an XP laptop, I would prefer a different linux distro on that laptop, but I'm not left with a choice.

If it is Nautilas causing the poor performance, would the use of a different file browser make any difference to the data transfer rates? Can Nautilas be disabled at startup & replaced with a different browser?

dragon

---

### Post by smeuse on 2010-11-20
I've been spending a lot of time on this issue and I've come to two conclusions:

1. mount.cifs is not performance optimized, and setting rsize manually doesn't seem to actually matter. /proc/mounts never shows an rsize over 16k, no matter what it's manually set to in /etc/fstab. I'm clueless on mount.cifs, I've got more reading to do, and i may try building from source to see if I can get it tweaked. 

2. Nautilus is slowing down file transfers very dramatically. 


Some data: my cifs mount looks like this:

> //server/archive /home/user/smb cifs directio,credentials=/home/user/.smbcred 0 0

Transferring a 4G DVD iso:
Nautilus: 15.5MB/s
using DD read: 48.8MB/s

I also have NFS set up as well, here is what that mount looks like:


> server:/archive /home/user/nfs nfs rsize=8192,wsize=8192,timeo=14,intr 0 0

Same file:
Nautilus: 86MB/s  (not horrible)
using DD read: 105MB/s  (840mb/s, what I would expect)


I just spent a few hours playing with my smb.conf file, and nothing seems to make that big of a difference either way. The biggest slowdown (3-4MB/s) was when I removed "use sendfile = yes".


The REAL pain point for me is that when I boot into my Win 7 partition on the same client PC, I get 100Mb/s file transfers, from the file browser, which tells me that the smb.conf is fine...

As a long time Linux defender (1993), this is serious pain :) 

Windows is outperforming Ubuntu.....ugh...

I think It's worth focusing on mount.cifs for a little while.

-Steve

---

### Post by SciFi-Bob on 2010-12-03
I have some embedded devices all running samba, and on my gigabit network I get a network read/write performance of around 56-72Mb/s on most of them, running iperf, but max. 12-17Mb/s running samba (my test was some transfers of a 1Gb file).

It's a shame that the cifs client is not utilizing my network speed at all.

I cannot for my bare life understand how a file protocol can reduce network transfer speed so much. That's just has to be a bug somewhere..

And, yes, I HAVE read about anything related to read/write buffers on the Samba doc site, and tried them. Too bad that the socket option page link is down, but I have tried most of the combinations of those options too.

Is this a "Samba 4 is on the way, screw Samba 3" issue?
If so, I can't use it, my embedded devices cannot run samba 4, and my trial run of Samba 4 on a client only proved that it had major problems authenticating with anything older. (and had no speed increase)
I'm running server security on a pure Linux network. No Win machines here)

Is it too much to ask, just to have a file sharing system on Linux, like they have on Windows, with the same speed?

And, if any NFS freaks feel like promoting their favourite, I'll just have to say that it's not ready yet.
(Try to mount a user owned NFS share from a non-root client with target user read/write access, where all new files is owned by that specified user (and group))
Samba has all this, and more too! Please Samba folks - help us get the best file sharing system on Linux up and running in circles around Microsoft!

---

### Post by Dimon8211 on 2011-04-06
Hi

Same is here. I affected by this prbm from 9.04. I always thought it is network related as I use wireless connection in general and had 2-3MB/s.After I updated my wireless to 802.11n I got only slight improvement in speed 3-4MB and 5-6Mb/s with mount in nautilus. Recently I tried Win7 as client and had 11-12MB/s on the same hardware, I installed NFS and its the same 11-12MB/s. But NFS is really pain to use because of small security and permissions issues. I saw many threads in Internet regarding mount.cifs module in different distros, but no solution. Don't want to use Win7 on my laptop, but don't have other option. Why Linux developers forget about perfomance and add only new features? I was really impressed with loading ubuntu 9.04 for 15-20 sec. Now it is became heavier and slower with every new version.

Best regards

---

### Post by Enigmatic on 2011-04-06
I recently upgraded my fileserver to Debian 6, and am seeing 80+ MB/s writes and reads (as it should be) via NFS. This is using an up to date 10.10 client.

---

### Post by Dimon8211 on 2011-04-07
> **Enigmatic said:**
> I recently upgraded my fileserver to Debian 6, and am seeing 80+ MB/s writes and reads (as it should be) via NFS. This is using an up to date 10.10 client.

Interesting situation. What had fileserver before Debian? I have Ubuntu 10.10 server, Win7 as client has good speed, Ubuntu 10.10 has not. So I suppose it is client related prbm not server

Best regards,

---

### Post by Enigmatic on 2011-04-07
Debian 5 (lenny?) previously. I don't know if it's a coincidence, but everything is very fast now.

---

### Post by Dimon8211 on 2011-04-11
> **Enigmatic said:**
> Debian 5 (lenny?) previously. I don't know if it's a coincidence, but everything is very fast now.
Think it is coincidence, I connected Win7 share and speed is bad again, so not server related.I alos tried wired connection (i has only 100M network) and get 7-8MB/s. Really terrible as I can get 11-12MB/s with this harware/drivers via NFS.
I sniffered packets and see that rsize never bigger then 5xxx bytes, while it is 64kB in Windows.

---

### Post by bhobw on 2012-01-04
This problem has been bugging me for a couple of days now. 

I've read bug reports / blogs / alternative linux distro forums - it seems fairly common. 

.... But I've solved my problem!!! 


I was getting the following situation: transfer of large files to server would initially go fast then grind to a halt @ 1-5MB/s

I tried updating network card drivers - no joy.

I discovered that my problem was the way in which my storage drive was mounted on the server. I'd used the 'sync' option in fstab.

Removed this, remounted and .... 100MB/s  - flying along now.

I suggest everyone checks their mount options

BHOBW

---

### Post by schlatter on 2012-04-13
Yes, I know this problem :( Today I started a new attempt at solving it and - as it seems - I succeeded. However, bhobw's solution didn't do it for me. Here's what I did:

1. unmount all cifs drives
2. rmmod cifs
3. modprobe cifs CIFSMaxBufSize=65536
4. mount cifs drives

Results (transfer rate measured by copying a large file):

CIFSMaxBufSize   Rate (MB/s)
16384 (default)  17.9 MB/s
65536            35.9 MB/s
130048 (max)     36.9 MB/s

using gvfs       38.4 MB/s

While I can't match gvfs's speed, my cifs performance is now at least acceptable.

---

### Post by bs27975 on 2012-06-12
> **schlatter said:**
> 
1. unmount all cifs drives
2. rmmod cifs
3. modprobe cifs CIFSMaxBufSize=65536
4. mount cifs drives


Having done this, I find my cifs now borked.

ls /{share} always returns:

```
ls: reading directory /{share}: Input/output error
```

Kubuntu 12.04 (pp).

Help!

---

### Post by bs27975 on 2012-06-12
> **bs27975 said:**
> Having done this, I find my cifs now borked.

ls /{share} always returns:

```
ls: reading directory /{share}: Input/output error
```

Kubuntu 12.04 (pp).

Help!

Interesting. Per [https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/810606](https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/810606)
changed 65536 to 130048 (and added rsize=32768,wsize=32768 to fstab) and the input/output error has gone away, and at least I can ls the share.

Can't speak to speed yet, but at least I can list the directory.

---

### Post by kid1000002000 on 2012-06-21
Same issues here. See 
[https://bugzilla.samba.org/process_bug.cgi](https://bugzilla.samba.org/process_bug.cgi)
and 
[http://www.overclockers.com/forums/showthread.php?t=683188](http://www.overclockers.com/forums/showthread.php?t=683188)
for suggestions.

---

### Post by bs27975 on 2012-06-21
> **bs27975 said:**
> Interesting. Per [https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/810606](https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/810606)
changed 65536 to 130048 (and added rsize=32768,wsize=32768 to fstab) and the input/output error has gone away, and at least I can ls the share.

Can't speak to speed yet, but at least I can list the directory.

Following up to this post ...

Never mind. Maybe.

The above changes -definitely- helped with speed. But it didn't resolve the problem - it couldn't. [When I did resolve the problem, I have no doubt that the above ( 130048 ) provided a massive speed improvement over the defaults.]

Problem turned out to be a bum network card. When I switched to the mb's nic (I intended this machine to be a gateway, and the nic I was on was intended to ultimately be 'outside', leaving the mb nic to be 'inside'), speed was 'fine'. As in, sufficiently good.

For testing, I was slinging .iso's around my net. And, I loaded the rlogin (sp?) package so I could test transfer speeds outside of cifs, letting me gauge the specific impact of cifs. [Using cygwin on my Win XP machine. (Didn't know before that that Win XP, but not 7, comes with an rcp. Have an eye for this if you use it, call \cygwin\bin\rcp specifically - MUCH faster than the native Windows utility.)] Thus, I could test via (Win) rcp, (Cygwin) rcp, ssh, and cifs, in pushing files from my Win XP to pp. (amd64)

Later, I replaced the PCI nic with an identical one, and noticed similar speeds to what I was getting via the MB nic. The original PCI nic I had been testing with promptly went into the garbage. [What a massive waste of time.]

(Garden Path) Warning: I saw hints saying to use the sk98 driver, which would have meant downloading (which I did) and compiling. However, it appears sk98 is 32-bit, this is a 64-bit system, and the world was going to get very irritating trying to shoehorn the one into the other. Whatever sk98 might bring to the party, the skge driver being natively loaded by the kernel performs sufficiently well that I would not advise anyone to go down the sk98 path. [Staying native allows later fixes to automatically come in as part of your normal update / maintenance process. Rather than remembering to download any sk98 updates / recompile, etc., at each change.]

I do suspect nic choice matters. From my reading, it appears some kernel nic drivers are 32-bit adapted (thunked?). Some nics are better supported / have better drivers than others (e.g. Broadcom vs. Intel), so if you're running into problems like I did, if you can throw a different nic in and re-test, you may gain a bit of your sanity back.

When I get back to working on this machine being a gateway, I'll go buy a PCI-X NIC, and spend an extra $20 for the Intel over the TP-Link (available at my local Canada Computer).

Once I tossed the bad nic, I saw rcp speeds hit over 200 Mibits/s. I think I saw cifs top out in the mid-170's. (ssh was a little lower, but not, say, 20MiBits/sec lower.) Good enough for me - my WinXP machine can't sustain it anyways, and miles better than XP -> XP via robocopy. [Blew my socks off to see how much faster a pp receiver was over a (Win) 'native' receiver.] Eventually Win XP will be gone, and this may all be a non-issue. (Assuming nfs is in my future, and a cifs based nas is not.)

Summary:
- yes, nics do occasionally fail in hard to detect ways. It's not either they work, or they don't.
- test your speeds, compare both against non-cifs and a different network card.
- drivers may matter. If you can, swap with a nic that doesn't use the same vendor / chipset. e.g. Broadcom, Intel, <can't think of the other major one>.

Wishing everyone the best of luck and speedy resolution if they run into this.

[What a massive waste of time chasing my tail on this one.]
[Caveat: At least the K/Ubuntu/Unix community has the tools available, let alone the user community and documentation to deal with it all. Thank you all for being here.]

---

