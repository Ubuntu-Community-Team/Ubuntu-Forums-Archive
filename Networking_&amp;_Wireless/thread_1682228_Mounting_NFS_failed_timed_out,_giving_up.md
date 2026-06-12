---
title: "Mounting NFS: failed: timed out, giving up"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by ruzlebiff on 2011-02-05
Hello,

I'm running FreeNAS with NFS enabled, but when I follow this guide: [http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html](http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html)
I get to "$ sudo mount  -o soft,intr,rsize=8192,wsize=8192 192.168.1.1:/viveks /nfs" But it files with "failed: timed out, giving up"

I have also tried "sudo mount 192.168.0.120:/mnt/FreeNAS /media/nfs/" but i get the same error here.

Hope someone van help me.

Best Regards,
Sindre

---

### Post by Jose Catre-Vandis on 2011-02-05
Follow the thread  [http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS](http://ubuntuforums.org/showthread.php?t=249889&highlight=NFS)

Start at first post, then check last few pages for issues with nfs version / NAS

---

### Post by ruzlebiff on 2011-02-06
I'm sorry, but i can't find an answere to my problem.
There is no firewall running.

I was running ubuntu 10.10 on 2 computers. 1 was working and 1 got the "failed: timed out, giving up"-error. I didn't understand why, because they were practical identical.
Now I have reinstalled the one that was working (installed ubuntu ultimate 2.8) and now i get the same error on both computers.

Samba is working great, but it's slow.

BR
Sindre

---

### Post by ruzlebiff on 2011-02-07
Would be super if someone could help me with this :)

---

### Post by Jose Catre-Vandis on 2011-02-07
Um if its happening on both clients, something is wrong with the nfs server. What has changed? Either on both clients or on the server? Are all your nfs versions the same?

---

### Post by ruzlebiff on 2011-02-09
I have no idea what version of NFS the newest (stable) version of FreeNAS is running. Nothing have changed here. Enabled it once, and that's it.

On the clients, i haven't done anything but following some how-to's online.
Did the same thing on both clients, but only 1 was able to connect to the NFS.
Now none of them are working :(

---

### Post by Jose Catre-Vandis on 2011-02-09
So what is the output of
```
showmount -e "Your NAS IP"
```

Try the following code in your /etc/fstab file for one of your shares
```
NAS_IP_Address:/your_share   /your/mountpoint       nfs     rsize=8192,wsize=8192,timeo=14,intr,bg
```

You'll need
```
sudo mount -a
```
to mount or this might give "useful" errors

---

### Post by ruzlebiff on 2011-02-10
> So what is the output of
```
showmount -e "Your NAS IP"
```showmount -e 192.168.0.120
Export list for 192.168.0.120:
/mnt/FreeNAS 192.168.0.0

> 
Try the following code in your /etc/fstab file for one of your shares
```
192.168.0.120:/mnt/FreeNAS   /media/nfs       nfs     rsize=8192,wsize=8192,timeo=14,intr,bg
```You'll need
```
sudo mount -a
```to mount or this might give "useful" errors
Same message as before :(

---

### Post by Jose Catre-Vandis on 2011-02-10
Try

```
sudo mount -t nfs4 192.168.0.120:/mnt/FreeNAS /media/nfs/
```

(/media/nfs does exist, doesn't it?)

Do you have firewalls running?

Have you run through this post?

[http://ubuntuforums.org/showpost.php?p=4442654&postcount=212](http://ubuntuforums.org/showpost.php?p=4442654&postcount=212)

Can you edit the exports file on the NAS?

My exports look like this (where 10.10.10.1 is the subnet I run on, and 10.10.10.1/24 serves all the PCs on the lan):

```
10.10.10.1/24(rw,no_root_squash,async,no_subtree_check)
```

---

### Post by ruzlebiff on 2011-02-11
/media/nfs exist ;) (i often use tabulator, so i don't misspell annything)
 
I'll go throug that post and see where it gets me.
 
My nas is running 192.168.0.0, as i posted yesterday. That's shuld be the same as /24
Do you know where i can find the exports in FreeNAS?

---

### Post by ruzlebiff on 2011-02-11
Tried the commands in the post, 1 and 3 seemed to work fine, but:
> sudo /etc/init.d/portmap restartgave this: 
> 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service portmap restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart portmap
portmap start/running, process 17642

You posted this: > sudo mount -t nfs4 192.168.0.120:/mnt/FreeNAS /media/nfs/That gave : > mount.nfs4: No such deviceSo i tried: > sudo mount -t nfs 192.168.0.120:/mnt/FreeNAS /media/nfs/That gave : > mount.nfs: mount to NFS server '192.168.0.120:/mnt/FreeNAS' failed: timed out, giving up

---

### Post by Jose Catre-Vandis on 2011-02-11
Pretty certain freeNAS is running nfs V3

The portmap command is OK, its just alreting you to the newer way of restarting it, "sudo service portmap restart"

Just trying to eliminate the obvious, having looked at your first post again, your clients are on the same subnet as your NAS aren't they? e.g. if NAs is 192.168.0.120 your clients are something like 192.168.0.5 ?


Have a look through this thread:

[http://ubuntuforums.org/showthread.php?t=646805](http://ubuntuforums.org/showthread.php?t=646805)
and here:
[http://boardreader.com/thread/mount_to_NFS_server_server_IP_failed_tim_b1sxXf5t.html](http://boardreader.com/thread/mount_to_NFS_server_server_IP_failed_tim_b1sxXf5t.html)
and here:
[http://tldp.org/HOWTO/NFS-HOWTO/troubleshooting.html](http://tldp.org/HOWTO/NFS-HOWTO/troubleshooting.html)

You didn't answer about firewalls?

Only other thing is permissions. Do you have the same user/uid on both the NAS (don't know if you can do this?) and the clients?

---

### Post by movieman on 2011-02-11
Are the rpc services running on the client? Here's mine:

$ rpcinfo -p [host]
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp   6000  status
    100024    1   tcp   6000  status

Also, are you using a firewall? I think I had to set a fixed port in /etc/default/nfs-common so I could allow connections through to rpc.statd (and, yeah, 6000 probably wasn't he best port to choose :)).

---

### Post by ruzlebiff on 2011-03-08
Hello again,

Been doing some more trying to get NFS working.. Her is what i got so far:

> :~$ rpcinfo -p 192.168.0.120
   program vers proto   port
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100000    4     7    111  portmapper
    100000    3     7    111  portmapper
    100000    2     7    111  portmapper
    100005    1   udp    800  mountd
    100005    3   udp    800  mountd
    100005    1   tcp    800  mountd
    100005    3   tcp    800  mountd
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100024    1   udp    954  status
    100024    1   tcp    661  status
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100021    0   udp   1011  nlockmgr
    100021    0   tcp    687  nlockmgr
    100021    1   udp   1011  nlockmgr
    100021    1   tcp    687  nlockmgr
    100021    3   udp   1011  nlockmgr
    100021    3   tcp    687  nlockmgr
    100021    4   udp   1011  nlockmgr
    100021    4   tcp    687  nlockmgr
Went to my router and opened port 111, 2049 and 32771.

> :-$ sudo /etc/init.d/nfs-kernel-server restart * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                        [ OK ] 
 * Starting NFS kernel daemon> :~$ less /var/log/syslog | grep -i nfs
Mar  8 19:45:15 sindre-HP-Compaq-6910p kernel: [186212.003547] FS-Cache: Netfs 'nfs' registered for caching
Mar  8 19:51:54 sindre-HP-Compaq-6910p kernel: [186611.035323] nfsd: last server has exited, flushing export cache
Mar  8 19:51:55 sindre-HP-Compaq-6910p kernel: [186612.124604] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Mar  8 19:51:55 sindre-HP-Compaq-6910p kernel: [186612.124625] NFSD: starting 90-second grace period
Mar  8 20:07:07 sindre-HP-Compaq-6910p kernel: [187524.849885] nfsd: last server has exited, flushing export cache
Mar  8 20:07:09 sindre-HP-Compaq-6910p kernel: [187525.925445] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Mar  8 20:07:09 sindre-HP-Compaq-6910p kernel: [187525.925468] NFSD: starting 90-second grace period
Mar  8 20:09:55 sindre-HP-Compaq-6910p kernel: [187692.752880] nfsd: last server has exited, flushing export cache
Mar  8 20:09:56 sindre-HP-Compaq-6910p kernel: [187693.814329] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Mar  8 20:09:56 sindre-HP-Compaq-6910p kernel: [187693.814354] NFSD: starting 90-second grace periodI don't know what this last is, but from this link: [http://ubuntuforums.org/showthread.php?t=646805](http://ubuntuforums.org/showthread.php?t=646805) they used it to fix a problem.

Still get:
> :~$ sudo mount -t nfs 192.168.0.120:/mnt/FreeNAS /media/nfs/
mount.nfs: mount to NFS server '192.168.0.120:/mnt/FreeNAS' failed: timed out, giving up

---

### Post by ruzlebiff on 2011-03-14
I have run "iptables -F" and "ufw stop"
So i'm sure i don't have any FW blocking me.
 
SSH and samba is working with no problems, but i still can't get the nfs-share to mount.
 
My freenas is reporting that nfs is running and everything is OK.
 
Hope somebody can help me with this. Feels like I've read a million "how-to mount nfs"-threads now! :P

---

### Post by jeduffey on 2011-04-15
I am having the same problem and was wondering what solution might have presented? 

One day FreeNAS is chugging along happily, the next day->
mount.nfs mount to NFS server '192.168.1.3:/mnt/zdevice/share' failed: timed out, giving up

ping works
rpcinfo -p 192...3 gives correct info showing nfs and portmap running
ssh works correctly
web-gui for FreeNAS works correctly
I thought I had UID for users set correctly, but checking showed they were not. Now they match.

I've been pounding the search engines for a week now and no solution.

---

### Post by charlie0440 on 2011-04-16
> I am having the same problem and was wondering what solution might have presented? 

That would be 3 of us!

I recently upgraded to Ubuntu 10.10 before it all worked fine.

Showmount -e shows the shares but trying to mount them gives me:

"mount.nfs: mount to NFS server 'ipaddress:/mnt/Disk2' failed: timed out, giving up"

---

### Post by jeduffey on 2011-04-18
I connected to my server via SSH, cd into the ZFS directories and found that it shows nothing. However I can mount the server share -on the server- as a client, and going into the mounted directory, such as 'music', does show all the files. How about you?

---

### Post by charlie0440 on 2011-04-18
Not at home right now to test.

But all week I've been logged into my freenas via SSH from my ubuntu box & have been browsing and copying files around no problem (they are visible, im not using ZFS).

I will try and mount the shares on the server later.

---

### Post by charlie0440 on 2011-04-18
I don't know enough about freeBSD...
it doesn't let me use sudo - "bash - sudo: command not found"

when I try and mount the share:
mount 192.168.0.100:/mnt/Disk1 /mnt/test2/nfs
[udp] 192.168.0.100:/mnt/Disk1: RPCPROG_MNT: RPC: Authentication error; why = Client credential too weak

presumably because I am not root.

Ive installed firestarter and can see my nas box trying to communicate with ubuntu - have no idea what the problem is

---

### Post by jeduffey on 2011-04-19
with FreeBSD / FreeNAS, use " su " <enter> to get to root mode
then enter your mount command.


on my own system rpcinfor -p se.rv.er.ip   works correctly

---

### Post by jeduffey on 2011-05-11
update: I was able to get complete access to my NFS shares by booting with Lucid Puppy 5.0.1  and  Peppermint Ice.
For LPuppy I had to install nfs-common, it automatically had root access.
Peppermint Ice also had to install nfs-common, but then had to open a terminal, su to root, then get access to all the share, which has root ownership.

This tells me that my Unix buddy is correct, something is wrong on the workstations, causing the timeout - giving up error.
But what is the is issue is still anybodies guess.

---

### Post by jeduffey on 2011-05-13
I used the command line
nfsstat --version

in Ubuntu 10-10 and got the response 1.2.2
in Peppermint I get 1.1.6

I am pursuing the angle that the NFS versions don't match

---

### Post by jeduffey on 2011-05-13
I realized that the nfsstat --version command only gave me the version of the nfs utility not the version of nfs.

Then I tried rpcinfo -p 192.168.1.3
and got the following
   program vers proto   port
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100000    4     7    111  portmapper
    100000    3     7    111  portmapper
    100000    2     7    111  portmapper
    100005    1   udp    673  mountd
    100005    3   udp    673  mountd
    100005    1   tcp    673  mountd
    100005    3   tcp    673  mountd
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100024    1   udp    878  status
    100024    1   tcp    942  status
    100021    0   udp    849  nlockmgr
    100021    0   tcp    629  nlockmgr
    100021    1   udp    849  nlockmgr
    100021    1   tcp    629  nlockmgr
    100021    3   udp    849  nlockmgr
    100021    3   tcp    629  nlockmgr
    100021    4   udp    849  nlockmgr
    100021    4   tcp    629  nlockmgr

This looks like the nfs version is both 2 and 3.

Running the same command on my workstations shows some with nfs appearing only once each for udp/tcp as 3, some that show it three times each with 2, 3, 4.

---

### Post by invisiblefish on 2011-05-18
I was having this same issue with FreeBSD nfs server using a Debian Squeeze client.  

I made the following entry in the Debian client's /etc/fstab under the options column:

mountproto=tcp

to force the nfs client to use tcp.  Everything seems to be working fine now.  Hope this helps.

---

### Post by jeduffey on 2011-05-25
Your post was a little vague. I added your "mountproto=tcp" as a separate line in /etc/fstab file and it stopped my haddrive from mounting. Booting from a LiveCD Linux gave me access to fix that.

I did some more research, found this link
[http://www.linuxquestions.org/questions/linux-networking-3/nfs-client-mount-only-works-with-proto%3Dtcp-while-iptables-is-running-881308/](http://www.linuxquestions.org/questions/linux-networking-3/nfs-client-mount-only-works-with-proto%3Dtcp-while-iptables-is-running-881308/)

#mount -v -o proto=tcp NetApp:/share /mnt

I used that format to add "-o proto=tcp" to my command line mount command.
It did work. Now I have to figure out why it works and what side effects that has.

Thanks.

---

### Post by jeduffey on 2011-05-25
I am also tracking my solution search in the FreeNAS forum
[https://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=49&t=9018&p=51727#p51727](https://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=49&t=9018&p=51727#p51727)

---

### Post by jeduffey on 2011-06-01
While I have determined that the NFS client is trying to use UDP and the server is using TCP, I have not been able to figure out why or what changed. I have started looking at how to force both the server and the client to boot with the setting of only using TCP for the NFS connection.

I came across this
>>
On the system, you have problem with, modify /etc/rc.config.d/nfsconf.

Check mountd_options setting. Should look like follows.

MOUNTD_OPTIONS="-o proto=tcp"
[http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1306851845674+28353475&threadId=895314](http://forums13.itrc.hp.com/service/forums/questionanswer.do?admit=109447627+1306851845674+28353475&threadId=895314)
>>

Every search says that the filename and location are what is listed, but on Natty Narwhal 11.04 that is not the case. My Unix buddy suggested /etc/default/..    nfs-common is in there and nfs-kernel-server, but it still doesn't look right.

---

### Post by jeduffey on 2011-08-09
I have, as yet, not resolved this issue. Any help is still greatly appreciated.

---

### Post by charlie0440 on 2011-08-09
> i have, as yet, not resolved this issue. Any help is still greatly appreciated. 	
+1

---

### Post by jeduffey on 2011-09-19
I am still chugging on this issue, a little at a time.

Most recent thought: UDP vs TCP, how can I tell which is *actually* functioning?
Answer: network packet sniffer, I used Wireshark, right in the U software center.
The output seems to indicate that Ubuntu is -not- sending out or receiving UDP, but I can't be sure, at least not yet.

From this line of thought I ran a different search about UDP packets and NFS and found this posting.
[http://wdtvforum.com/main/index.php?topic=5379.0;wap2]("http://wdtvforum.com/main/index.php?topic=5379.0;wap2")
The claim is that enabling Jumbo Frames messes with the function of NFS.
Here to enable [http://krypted.com/ubuntu/enable-jumbo-frames-in-ubuntu-server-10/]("http://krypted.com/ubuntu/enable-jumbo-frames-in-ubuntu-server-10/")

I will continue testing and post the results as I may.

---

### Post by jeduffey on 2011-09-19
Jumbo Frames in FreeNAS
[http://pacopablo.com/blog/blog/pacopablo/freenas_lagg_jumbo_frames]("http://pacopablo.com/blog/blog/pacopablo/freenas_lagg_jumbo_frames")

---

### Post by charlie0440 on 2011-09-22
> Jumbo Frames in FreeNAS

I remember configuring freenas and ubuntu 10.10 for jumbo frames. The problem didn't occur until I installed 11.04 so maybe you are on to something!

Edit - didnt work! didnt think changed the MTU would make a difference

---

### Post by jeduffey on 2011-11-11
I have attempted to correct this issue with upgrades to Ubuntu 11.10, also with no results.

I set up an older PPC Mac, installed OS X 10.5 Leopard and was able to connect to the server with no problem at all. So it seems the server is really working the way it is supposed to work. But ALL of the Ubuntu machines are not.

I am still able to connect to the NFS exports if I add (-o proto=tcp) after mount command.  But why do I have to add this option statement? I should just be able to use the mount statement and be done. I have several exports, so after fixing this specific I issue I need to move to autoFS for all of them.

Again, any help is appreciated.

---

### Post by jeduffey on 2012-02-09
I am now inclined toward the view that it is a combination problem.
Ubuntu wants to send and receive, at least initially or by default, via UDP.
FreeNAS wants to send and receive via TCP.

sudo mount -o proto=TCP 192.168.1.1:/share/data /mnt/servershare/data
works as it should.

So how do I hard code Ubuntu to TCP and UDP?
Mac OS X does this automatically.

How do I hard code the settings for FreeNAS to broadcast in both TCP and UDP?

Any help is greatly appreciated.

---

### Post by jeduffey on 2012-05-20
(a few weeks ago) I upgraded my FreeNAS 7.2 to 7.5 of the latest stable build. Same results.

As of this post I have upgraded again to NAS4free 9.0, with the same results: mount nfs timed out giving up.

I have also tried using Linux Mint 13RC. With no change in results.

Any help with this issue is greatly appreciated.

---

### Post by jeduffey on 2012-05-21
Anyone have some specifics about where Ubuntu or any other Linux Distro keeps its configuration settings for TCP / UDP protocol usage?

---

### Post by jeduffey on 2012-05-30
Yesterday I installed Linux Mint 9 with kernel 2.6.32-21 on an extra macine.
Once I installed NFS-Common it connected to the NFS server, WITHOUT any protocol specification, in a few seconds with no problems at all.

I am now quite clear that there was in fact some major change in the LINUX kernel. Somewhere between 2.6.32 and approximately 3.0.

Any help with finding or understanding the change in the kernel would be greatly appreciated.

---

### Post by jeduffey on 2012-06-11
I have confirmed my theory.  The change is between 2.6.32 and 2.6.33

I booted a copy of MacPup 5.2.8  using kernel 2.6.33 = mount nfs timed out giving up

Now I know *where* something happened. The Linux kernel was changed. 

Great. New questions: What exactly in kernel 2.6.33 is different from 2.6.32?   
Who changed it and why, would also be good to know.
Can I get the next kernel to change it back? Or maybe just an update to fix it?

---

### Post by antcer1213 on 2012-08-06
I'm using Bodhi built on Ubuntu 12, 3.2.0-27-generic kernel. My NFS server would also timeout while I was trying to mount from the Client. 

Eventually, after tedious googling(lol), I realized that the ports for mountd, status, and mvsmount were constantly changing, meaning no assigned ports.

I opened up services document in terminal:

-"gksudo leafpad /etc/services"
-(typed in password, of course)
-Pressed Ctrl-F, searched for "nfs"
-Around the nfs service, I assigned ports as such:
"
#NFS Server-------------------------------------------
nfs           2049/tcp
nfs           2049/udp
mountd        2045/tcp
mountd        2045/udp
lockd         2044/tcp
lockd         2044/udp
mvsmount      2046/tcp
mvsmount      2046/udp
status        2043/tcp
status        2043/udp
"
-Saved changes
-Opened those ports up on my router through Port-Forwarding.
-then "sudo reboot"
and since then, my server is now able to connect without any problem! This is my 1st post so sorry if I didn't explain myself properly!

---

