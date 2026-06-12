---
title: "NFS mounts fail on boot"
date: 2008-01-22
forum: Mythbuntu
---

### Post by mjezell on 2008-01-22
Hi All,

I've been using MythTV  since v.9 with a BE/FE setup on two boxes.  After mythbuntu 7.10 came out I decided to rework my systems to a MBE/FE and two remote FE.  The setup was very painless and you are to be commended for you success.  I am having a small problem with the NFS shares I have set up on my remote FEs.  When I boot them up they hang for several minutes at the point where the system tries to mount them and then fail.  After the boot-up completes and  mythtv s up and running, the mounts are accessible even thought the boot process indicated failure.  I'm sure that I must have missed something in the configuration of the NFS server on the MBE or the clients on the remote FEs.  I followed [malco2001]("http://ubuntuforums.org/member.php?u=104208") excellent howto on NFS setup and have scoured the forums and internet for and answer to this problem.

Here is my /etc/export file from the MBE - 
 > /var/lib/mythtv/recordings 192.168.1.1/24(rw,no_root_squash,async,no_subtree_check)
/var/lib/mythtv/videos 192.168.1.1/24(rw,no_root_squash,async,no_subtree_check)
/var/lib/mythtv/music 192.168.1.1/24(rw,no_root_squash,async,no_subtree_check)
/var/lib/mythtv/pictures 192.168.1.1/24(rw,no_root_squash,async,no_subtree_check)
The /etc/hosts,allow file from MBE -
> # /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap and rpc.mountd
# for further information.
#
portmap: ALL
ALL: LOCAL
The /etc/hosts.deny file from MBE -
> # /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(and rpc.mountd)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
ALL: PARANOID
portmap: ALL
And the /etc//fstab file from the remote FEs -
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8e7d99b8-5ce4-4d9c-8c74-6ad228a52ed8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e483ebb9-6647-49a2-b3bf-36b7b8d696f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

192.168.1.75:/var/lib/mythtv/music /var/lib/mythtv/music nfs rw,rsize=8192,wsize=8192,timeo=0,hard,intr,nfsvers=3 0 0
192.168.1.75:/var/lib/mythtv/videos /var/lib/mythtv/videos nfs rw,rsize=8192,wsize=8192,timeo=0,hard,intr,nfsvers=3 0 0 
192.168.1.75:/var/lib/mythtv/pictures /var/lib/mythtv/pictures nfs rw,rsize=8192,wsize=8192,timeo=0,hard,intr,nfsvers=3 0 0
Nothing strange comes up in dmesg on the remote FEs or the MBE.  I've been on the NFS website, ubuntu forums, google, and several other places trying to find an answer, but no luck.  The MBE has nfs-kernel-server, nfs-common and portmap installed and the remote FEs have nfs-common and portmap installed.  I've checked and all the systems after boot-up to make sure everything is running and no problems there.

All boxes are running mythbuntu-7.10-i386 with a mish-mash of hardware.     I'll be more than happy to supply any other system info. 

Thanks for any and all help.

Fixed (kind of): 
Since running feisty I've been installing a bash script to restart my network to resolve an issue with the wireless.  Because the network connection does not come up at the right time in the boot sequence the NFS mounts could not load, hanging the boot process.  After the bash script runs the NFS mounts are mounted and all is well.  So I removed the auto-mounts from the fstab file and add them to the bash file and everything works, sort of.  Now when I power down the remote FEs, the process hangs for a few moments at rc.local, something fails and then the shutdown completes.  That's OK because now that the remote FEs don't hang on boot-up anymore my wife is happy, therefore I'm happy.  Thanks to anyone that took the time to look at this post.

---

### Post by trieb on 2008-05-02
I am having the same problem, but I have not yet found a solution.  I'll post back if I do.

---

### Post by [Psyduck] on 2008-05-03
I have a similar issue.

During boot up the nfs mount times out and I get these messages in syslog:
```
syslog:May  3 08:37:32 htpc kernel: [   70.298181] rpcbind: server 192.168.1.254 not responding, timed out

```

But after the computer is done booting the nfs mounts work just fine?

---

### Post by laga on 2008-05-03
Do you have the "portmap" package installed?

---

### Post by gr8nash on 2008-05-04
Just a quick ditto.. mine also hangs for 30 seconds and says internal nfs error... followed by each of my mounting folders showing a red "failed"  but the good news is it still works when it boots as if it didnt have any issue.. i do have portmap installed

---

### Post by laga on 2008-05-05
Okay, that sounds like a bug. Can someone file a bug at [http://bugs.launchpad.net/mythbuntu](http://bugs.launchpad.net/mythbuntu)?

---

### Post by mjezell on 2008-05-05
After much experimenting I determined that my wireless connection was not coming up on boot so I put a small bash script in the /etc/init.d/ folder to resolve the issue with the wireless. Because the network connection does not come up at the right time in the boot sequence the NFS mounts could not load, hanging the boot process. After the bash script runs the NFS mounts are mounted and all is well.
```

#!/bin/bash
sudo /etc/init.d/networking restart

#NFS mounts
sudo mount -t nfs 192.168.1.75:/var/lib/mythtv/music /var/lib/mythtv/music -o tcp,rw,rsize=8192,wsize=8192,timeo=0,hard,intr,nfsvers=3
sudo mount -t nfs 192.168.1.75:/var/lib/mythtv/pictures /var/lib/mythtv/pictures -o tcp,rw,rsize=8192,wsize=8192,timeo=0,hard,intr,nfsvers=3
sudo mount -t nfs 192.168.1.75:/var/lib/mythtv/videos /var/lib/mythtv/videos -o tcp,rw,rsize=8192,wsize=8192,timeo=0,hard,intr,nfsvers=3

```Used this thread to setup the bash script
> 
So you have a script of your own that you want to run at bootup, each time you boot up. This will tell you how to do that.

Write a script. put it in the /etc/init.d/ directory.
Lets say you called it restart_networking. You then run

$ sudo update-rc.d restart_networking defaults

You also have to make the file you created, restart_networking, executable, using
$ sudo chmod +x /etc/init.d/restart_networking

You can check out
% man update-rc.d for more information. It is a Debian utility to install scripts. The option “defaults” puts a link to start restart_networking in run levels 2, 3, 4 and 5. (and puts a link to stop restart_networking into 0, 1 and 6.)

Also, to know which runlevel you are in, use the runlevel command.
Sorry to the original poster but I no longer have your name to credit you with this post.

Hope this helps anyone with this problem.

---

