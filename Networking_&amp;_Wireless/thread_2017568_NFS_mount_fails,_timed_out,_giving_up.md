---
title: "NFS mount fails, timed out, giving up"
date: 2012-07-05
forum: Networking &amp; Wireless
---

### Post by bpmod on 2012-07-05
Hello

I have 4 computers on a network:
2 Ubuntu 11.10
1 Win 7
1 FreeNAS 8.0.2

I have an NFS share on the FreeNAS and a file on each Ubuntu (/etc/init.d/mountall.sh) which mounts the share upon bootup.

All has been running for 6 months with nary an issue until this morning when 1 Ubuntu machine would no longer connect to the NFS share. The second one connects fine, and the Win7 machine connects to its Windows share on the FreeNAS.

I have been googling for three hours as well as searching this forum and the FreeNAS forum. The closest I have come to finding the situation is at [http://ubuntuforums.org/showthread.php?t=1682228](http://ubuntuforums.org/showthread.php?t=1682228) but there is no solution there.

The exact error message I am getting is "mount.nfs: mount to NFS server 'serverIP:/share' failed: timed out, giving up" (where serverIP and share are the FreeNAS IP address and NFS share path, respectively).

I have verified the following:
The FreeNAS IP address has not changed
I can SSH into the FreeNAS
showmount -e serverIP shows the correct share
The other Ubuntu machine can be disconnected and re-connected at will with no issues

I have to assume that the problem lies on the Ubuntu machine and not the FreeNAS, but I cannot seem to track it down.

All suggestions given in the thread referenced above have come up short.

Thanks for any help

Brian

---

### Post by SeijiSensei on 2012-07-05
Did the client's IP address change?  Is it still within the range of acceptable hosts in /etc/exports?

---

### Post by bpmod on 2012-07-05
> **SeijiSensei said:**
> Did the client's IP address change?  Is it still within the range of acceptable hosts in /etc/exports?
No. The client's IP did not change, and it is still within the range, and would be even if it had changed.

The DHCP server's range is the same as the range of acceptable hosts in /etc/exports.

Brian

---

### Post by bpmod on 2012-07-06
Update:

I can connect to the NFS share when I boot my machine from a Live CD, but every other solution I have tried has failed.

When I run 'rpcinfo -p' on the client, I do not get any lines referencing nfs or port 2049. I do, however, get lots of references to portmapper on port 111.

Is this normal?

Thanks

Brian

---

### Post by SeijiSensei on 2012-07-06
On my NFS client with mounted shares, rpcinfo returns a lot of lines like these:

```

    100003    2   udp   2049  nfs
    100005    1   udp  58150  mountd
    100021    1   udp  47937  nlockmgr

```

I have multiple shares mounted so I have multiple entries like this.

Are you mounting as root with sudo? If so, do you have "no_root_squash" among the options on the server?

---

### Post by bpmod on 2012-07-07
> **SeijiSensei said:**
> On my NFS client with mounted shares, rpcinfo returns a lot of lines like these:

```

    100003    2   udp   2049  nfs
    100005    1   udp  58150  mountd
    100021    1   udp  47937  nlockmgr

```I have multiple shares mounted so I have multiple entries like this.

Are you mounting as root with sudo? If so, do you have "no_root_squash" among the options on the server?
Do these entries exist on the machine before you mount the share? Or only after the successful mount?

My other Ubuntu machine (the one that connects fine) has some entries that the troublesome one doesn't, and I am wondering if it is because one is connected and one isn't.

I am mounting (attempting to, that is) as root with sudo, and as I said up front, this has been working every day for six or seven months and suddenly stopped. I have not made any changes to the setup at all.

But it is now going onto day three and is resulting in major headaches and lost time.

Thanks

Brian

---

### Post by steeldriver on 2012-07-07
can you mount the share OK after boot? I'm wondering if it's something to do with startup script order (e.g. the network interface not being up when the mountall.sh script gets run - the switch over from the old networking service to network-manager seems to have thrown up a few funnies like this)

---

### Post by SeijiSensei on 2012-07-07
> **bpmod said:**
> Do these entries exist on the machine before you mount the share? Or only after the successful mount?

I unmounted all my NFS shares and get the same results using "rpcinfo -p".

---

### Post by bpmod on 2012-07-07
> **steeldriver said:**
> can you mount the share OK after boot? I'm  wondering if it's something to do with startup script order (e.g. the  network interface not being up when the mountall.sh script gets run -  the switch over from the old networking service to network-manager seems  to have thrown up a few funnies like this)
No. I cannot mount at all, either by running the mountall.sh script after booting, or by manually mounting the share from the command line.

I have rebooted everything several times. I still get the same results: 1 Ubuntu machine will not mount the share. The other one does. The Windows machine also connects with no problem.

> **SeijiSensei said:**
> I unmounted all my NFS shares and get the same results using "rpcinfo -p".
So, could the lack of nfs, mountd & nlockmgr lines be an indication of what I need to look into?

I have googled these and have come up empty.

Thanks

Brian

---

### Post by luvshines on 2012-07-08
You wouldn't need nfs, mountd etc running on the NFS client machine.

Is the port 111 of the NFS server reachable from your client ?
```
## From client terminal
nc -zv <NFS-server-ip> 111
```
If yes then check the NFS ports(the ports returned after running rpcinfo -p on the NFS server) too

Did you try mount command with -vvv [verbose] option ? [May or may not be useful]

Else, capture a network trace to check what request is timing out

---

### Post by antcer1213 on 2012-08-06
I posted this just now on another thread and thought it might be relevant! :)

"I'm using Bodhi built on Ubuntu 12, 3.2.0-27-generic kernel. My NFS server would also timeout while I was trying to mount from the Client. 

Eventually, after tedious googling(lol), I realized that the ports for mountd, status, and mvsmount were constantly changing, meaning no assigned ports.

I opened up services document in terminal:

-"gksudo leafpad /etc/services"
-(typed in password, of course)
-Pressed Ctrl-F, searched for "nfs"
-Around the nfs service, I assigned ports as such:
"
#NFS Server-------------------------------------------
nfs 2049/tcp
nfs 2049/udp
mountd 2045/tcp
mountd 2045/udp
lockd  2044/tcp
lockd  2044/udp
mvsmount 2046/tcp
mvsmount 2046/udp
status 2043/tcp
status 2043/udp
"
-Saved changes
-Opened those ports up on my router through Port-Forwarding.
-then "sudo reboot"
and since then, my server is now able to connect without any problem! This is my 1st post so sorry if I didn't explain myself properly!"

---

### Post by luvshines on 2012-08-09
> **antcer1213 said:**
> 
Eventually, after tedious googling(lol), I realized that the ports for mountd, status, and mvsmount were constantly changing, meaning no assigned ports.


This is expected. The ports for NFS are not constant unless they have been explicitly defined. This is where portmapper comes into picture, which is running on port 111 (the port I asked you to check in my previous post)
NFS client contacts portmapper to know which ports are being used by NFS server then contacts those ports

---

### Post by fastie81 on 2012-10-16
> **bpmod said:**
> Hello

I have 4 computers on a network:
2 Ubuntu 11.10
1 Win 7
1 FreeNAS 8.0.2

I have an NFS share on the FreeNAS and a file on each Ubuntu (/etc/init.d/mountall.sh) which mounts the share upon bootup.

All has been running for 6 months with nary an issue until this morning when 1 Ubuntu machine would no longer connect to the NFS share. The second one connects fine, and the Win7 machine connects to its Windows share on the FreeNAS.

I have been googling for three hours as well as searching this forum and the FreeNAS forum. The closest I have come to finding the situation is at [http://ubuntuforums.org/showthread.php?t=1682228](http://ubuntuforums.org/showthread.php?t=1682228) but there is no solution there.

The exact error message I am getting is "mount.nfs: mount to NFS server 'serverIP:/share' failed: timed out, giving up" (where serverIP and share are the FreeNAS IP address and NFS share path, respectively).

I have verified the following:
The FreeNAS IP address has not changed
I can SSH into the FreeNAS
showmount -e serverIP shows the correct share
The other Ubuntu machine can be disconnected and re-connected at will with no issues

I have to assume that the problem lies on the Ubuntu machine and not the FreeNAS, but I cannot seem to track it down.

All suggestions given in the thread referenced above have come up short.

Thanks for any help

Brian

Hi 

I am not sure if you got this fixed, but I had the same problem. With FreeNAS, however I was running 8.1
I found this link [http://forums.freenas.org/showthread.php?7270-NFS-mount-times-out/page2&](http://forums.freenas.org/showthread.php?7270-NFS-mount-times-out/page2&)
Post 13 that pointed me into a DNS/Revers lookup issue.
So I had a Windows DNS running on my network. I enabled revers lookup and it all started to work.
Now they said in that post you need to add it to the FreeNAS host file but I thought I would like to keep it simple and not change to much. so DNS revers lookup was my best option and like I said worked.

So I hope this help someone ells..

C

---

### Post by pwabrahams on 2012-11-12
I have this problem also.  I have 3 computers on my local network (call them A, B, and C).  From any of A, B, and C I can mount NFS shares on A and C.  But from A and C I cannot mount NFS shares on B; the attempt enters a wait state and eventually times out.  Interestingly, I can self-mount NFS shares on B.  The mounting command that fails on A and C works when issued on B (in effect, a self-mount),   The critical line in /etc/exports on B is ```
/  *.local(rw,sync,no_subtree_check,no_root_squash)
```
If I instead use just
```
/  *.local(rw)
```
I get the same result.

---

### Post by LewisTM on 2012-11-12
What do you get if you are even more permissive?
```
/  *(rw)
```

---

### Post by pwabrahams on 2012-11-13
I modified /etc/exports on B to these lines:
```
/  *(rw)
/mnt     *.local(rw)
```
I still couldn't mount either / or /mnt from A.

Incidentally, I can ping B from A.

---

### Post by LewisTM on 2012-11-14
Your NFS clients might be requesting a mount from an unprivileged port.
Try adding the insecure option to your export to allow connections from any port.
```
/  *.local(rw,sync,**insecure**,no_subtree_check,no_root_squash)
```

---

### Post by pwabrahams on 2012-11-14
Adding **insecure** to the options doesn't help either.

I tried using a nonexistent directory on the remote machine to see what would happen:

```
sudo mount -t nfs lentinus.local:/xxx /mnt/lentinus

```

That timed out also.

---

### Post by luvshines on 2012-11-15
> **pwabrahams said:**
> I tried using a nonexistent directory on the remote machine to see what would happen:

```
sudo mount -t nfs lentinus.local:/xxx /mnt/lentinus

```

That timed out also.

Maybe check if any firewall on B is blocking the NFS mount. Better test by switching off firewall on B. Also check if syslog says something
If that doesn't help better capture network trace and check what is being denied.

---

### Post by pwabrahams on 2012-11-15
I installed the **guvw** program on B, and it revealed a firewall that I never knew was there.  In any event, I turned the firewall off completely and now I can communicate correctly.

I'm puzzled about that behavior, though.  The only rule that's listed is on port 11371, and the action is "Allow in from anywhere".  

Thanks!!

---

