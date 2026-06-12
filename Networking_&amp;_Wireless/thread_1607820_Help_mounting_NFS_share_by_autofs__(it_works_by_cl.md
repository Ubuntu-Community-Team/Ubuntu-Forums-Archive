---
title: "Help mounting NFS share by autofs  (it works by cli)"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by frafu on 2010-10-28
Hello, 

I have a server, with a static IP of 192.168.1.17, that is running Ubuntu lucid sever edition and that exports some shares per NFS. Here is its /etc/exports:

```

/media/Share00 192.168.1.0/255.255.255.0(rw,nohide,insecure,no_subtree_check,async)
/media/Share01 192.168.1.0/255.255.255.0(rw,nohide,insecure,no_subtree_check,async)
/media/Share02 192.168.1.0/255.255.255.0(rw,nohide,insecure,no_subtree_check,async)
/media/Share03 192.168.1.0/255.255.255.0(rw,nohide,insecure,no_subtree_check,async)
/media/Share04 192.168.1.0/255.255.255.0(rw,nohide,insecure,no_subtree_check,async)
/media/Share05 192.168.1.0/255.255.255.0(rw,nohide,insecure,no_subtree_check,async)

```

The client, that I want to configure to mount the shares from the server by using autofs is running Ubuntu maverick desktop edition; it has a static ip of 192.168.1.37 and here are its configuration files for autofs:

/etc/auto.master
```

#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#
#/misc	/etc/auto.misc
#
#
# NOTE: mounts done from a hosts map will be mounted with the
#	"nosuid" and "nodev" options unless the "suid" and "dev"
#	options are explicitly given.
#
#/net	-hosts
#
# Include central master map if it can be found using
# nsswitch sources.
#
# Note that if there are entries for /net or /misc (as
# above) in the included master map any keys that are the
# same will not be seen as the first read key seen takes
# precedence.
#
#+auto.master
#
#
# Added by frafu:
#
/msrv   /etc/auto.msrv  

```

/etc/auto.msrv
```

Share04 -fstype=nfs4    192.168.1.17:/media/Share04
Share05 -fstype=nfs4    192.168.1.17:/media/Share05

```

The user frafu exists on both machines and has 1000/1000 as uid/gid on both machines. I also want you to know that there are more users on the client, than on the server; in case it might be relevant.

I am able to mount the shares with scripts like this one (mount is in the sudoers file): 
```

#!/bin/sh
#
/usr/bin/sudo /bin/mount 192.168.1.17:/media/Share05 /media/Share05

```

However, autofs does not work: the /msrv directory appears and disappears when I start and stop autofs; but when I enter "cd /msrv" followed by "cd Share05" in the terminal, I get the "bash: cd: /msrv/Share05: No such file or directory" message after the second command. 

Could anybody please tell me why it does not work or at least tell me how I can narrow down the problem? (Looking at syslog or other similar threads was not helpful to me). 

Cheers, 

Francesco.

---

### Post by frafu on 2010-10-29
Hi, 

This thread has been hit around 40 times, but has not got any reply yet. 

I think that it might also be helpful, if I am told how I can make autofs and the related operations more verbose in order to see where the problem is located. 

Cheers, 

Francesco.

---

### Post by hufemj on 2010-10-30
I don't have an answer for you. But I'm experiencing a similar problem in reverse. I had nfs4 set up on a server running 10.04 per the directions at [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo). The client was/is running 10.04. When I upgraded the server to 10.10, it began failing the mount in /etc/fstab. That is, a "mount failure press S to skip" (or something similar) appeared during boot. After pressing S and completing the boot, mount -a worked just fine. That leaves me to believe that fstab is fine and that there's a boot order problem. Maybe that same change is affecting you.

I hesitate to upgrade the client to 10.10 because I have presentation coming up in a couple of days and don't want to risk problems on the client (my laptop).

---

### Post by frafu on 2010-10-31
Thanks hufemj for your reply. I am I fact wondering whether the default values of NFS in maverick are causing the problems. In fact, I have a linux based settop box, that mounts the shares by using autofs without problems. 

I think that I will keep Ubuntu lucid (10.04) server edition on the server as long as I don't have a good reason to upgrade; especially also because it is an edition with long term support.

---

### Post by haihovu on 2010-11-13
I got autofs working with NFS and NIS in Maverick. Seems like you got at least the NFS part working. I don't know if this means any thing but your example listed this bit in the auto.master file: 
[INDENT]**/msrv**   /etc/auto.msrv
[/INDENT]But later you mentioned that this worked for you:
[INDENT]/usr/bin/sudo /bin/mount 192.168.1.17:/media/Share05 **/media**/Share05
[/INDENT]Do you have directory /msrv created?

Since I use NIS I also added this bit to /etc/nssswitch.conf:
[INDENT]automount: files nis
[/INDENT]Did you also use idmapd to map user IDs and group IDs?

Oh, one other problem I found with autofs is that it had been switched to the new upstart framework in newer Ubuntu releases, where as NIS is still using the good ole init startup script, and as such we can no longer guarantee the order of startup of these two. What I needed was to have NIS started first, and then autofs started, because autofs is dependent on NIS. So I placed autofs start in /etc/rc.local instead of in /etc/rc2.d. I added this to /etc/rc.local
[INDENT]start autofs
[/INDENT]Did you try to restart autofs after booting up and then try to access the auto mounted directory(ies) again? If that doesn't work check all system logs like messages, syslog, daemon.log to see if there is any clue when you attempting to automount some thing. Last resort would be to run strace on the PID of autofs to see what it's doing when you attempt to automount.

That's a lot of rambling but I hope that some of those rambles might trigger some discovery.

Cheers,

---

### Post by frafu on 2010-11-14
Hello haihovu,

First of all, thanks for your reply. 

> **haihovu said:**
> I got autofs working with NFS and NIS in Maverick. Seems like you got at least the NFS part working. 


NFS on the server is working: I am able to mount the shares manually and I have a settop box running an old linux version that is able to automount the shares. 

> 
I don't know if this means any thing but your example listed this bit in the auto.master file: 
[INDENT]**/msrv**   /etc/auto.msrv
[/INDENT]But later you mentioned that this worked for you:
[INDENT]/usr/bin/sudo /bin/mount 192.168.1.17:/media/Share05 **/media**/Share05


I am already using that server for a few years and I have been mounting it all the time by using scripts to mount the various shares. The second line was simply copied from the scripts that mounts the shares under /media to make them appear on the desktop.

In order to not mess around with my scripts, I decided to use a different directory for the automount; at least until automount is working. That's why automaster uses /msrv.

> 
Do you have directory /msrv created?


When I start autofs, the /msrv directory appears; when I stop it, the /msrv directory disappears. (if it was not already there when starting autofs)

So autofs seems at least to work in part. However, when I enter "cd /msrv/Share05" in the terminal, I get "bash: cd: /msrv/Share05: No such file or directory".

Could you please confirm that the Share05 should indeed appear under /msrv with the autofs settings of the first post of the thread? 

Moreover, I tried to look at different log files on the client machine (also syslog), but no automount entry appears when I try to cd to the share. How can I make sure that automount tries to mount the share? Or more generally, how can I make the whole autofs more verbose to see what is going on? 

> 
Since I use NIS I also added this bit to /etc/nssswitch.conf:
[INDENT]automount: files nis
[/INDENT]Did you also use idmapd to map user IDs and group IDs?


I have not been using idmap until now. Is it related to nis? I gave it a try just now by enabling it on the server and on the client, but it does not seem to make any difference. 

> 
Oh, one other problem I found with autofs is that it had been switched to the new upstart framework in newer Ubuntu releases, where as NIS is still using the good ole init startup script, and as such we can no longer guarantee the order of startup of these two. What I needed was to have NIS started first, and then autofs started, because autofs is dependent on NIS. So I placed autofs start in /etc/rc.local instead of in /etc/rc2.d. I added this to /etc/rc.local
[INDENT]start autofs
[/INDENT]Did you try to restart autofs after booting up and then try to access the auto mounted directory(ies) again? If that doesn't work check all system logs like messages, syslog, daemon.log to see if there is any clue when you attempting to automount some thing. Last resort would be to run strace on the PID of autofs to see what it's doing when you attempt to automount.


I gave a look at some documentation about nis and it does not seem trivial to activate it. As I don't have much thime to play around at the moment, I might try to set it up later. On the other hand, as I have the same name and uid on the client and on the server, I would rather guess, that nis will not make any difference. Otherwise, would there not be some identification errors in the log?

> 
That's a lot of rambling but I hope that some of those rambles might trigger some discovery.


I am thankfull that you took the time to write them down. As you said, they might always trigger some discoveries, or give some new insights clearing up the picture about how it works. 

Cheers, 

Francesco.

---

### Post by haihovu on 2010-11-16
Sounded like you don't need NIS for autofs. Basically you can add auto.master and other autofs maps into the NIS database on the server side so that you don't need to set up /etc/auto.master, ... on client side. This is only useful if you have many clients. So you can ignore the NIS issues. Do make sure that autofs is not using NIS by having this line in /etc/nsswitch.conf:

automount: files

As for IDMAPD, it is used for mapping user ID/group ID between clients and servers and should not prevent autofs from functioning properly, however if not configured correctly can give you permission issues later on.

So in your case NFS seems to work, autofs seems to be running, though not mounting properly. Your problem sounds like what you'd see if the autofs maps are not properly setup, even though your auto.master and auto.msrv look good. Try removing -fstype=nfs4 from your map files and restart autofs and see what the behaviour is (just grasping at straw at this point). Also to eliminate NIS as a problem, execute this:

ypcat auto.master

You should get no such map error.

Also check out /etc/default/autofs to see if there is something unusual (everything in there should make sense).

Good luck,

---

### Post by frafu on 2010-11-17
Hi haihovu,

Many thanks for your help: autofs is working now under maverick and also under natty. 

> 
Try removing -fstype=nfs4 from your map files.
Also check out /etc/default/autofs.


The second sentence of the quote was decisive to find the solution. Indeed, the /etc/default/autofs included an option to make autofs verbose. The error messages and google gave me the solution: remove the executable bit of the auto.msrv file. Thus, one of the problems was the permission of the file that were 755 instead of 644.

The second problem was the -fstype=nfs4 option in the auto.msrv file that I had to remove. 

Thanks again for your help.

Francesco.

---

### Post by haihovu on 2010-11-17
Good to see a problem solved. I didn't know about the executable permission bits needed to be disabled. I'll add that to my doc.

Cheers,

---

### Post by frafu on 2010-11-17
Hi haihovu,

I am glad that the thread has given a new piece of information also to you. :-)

Thanks again for your help.

Francesco.

---

### Post by gpborges on 2011-09-07
> **frafu said:**
> Hi haihovu,

I am glad that the thread has given a new piece of information also to you. :-)

Thanks again for your help.

Francesco.

Guys, I tried ALL I cant to get this working on a XBMC Live install (Ubuntu 10.04.03 LTS) but I can't...

I set up autofs in my working laptop and it was a breeze. Didn't face any issues. I've just copied the same kind of setup and I can't get it working. It startups, does the mounts.. but I can't access anything inside of it:

I get errors like this:

ls: cannot open directory Videos/: No such file or directory

Could any good soul help me out? :-D

My /etc/auto.master is just this:

```
/mnt/NFS       /etc/auto.type      --ghost,--timeout=30
```(all the rest is commented out)

then my /etc/auto.type is:

```

# NFS mount for the Downloads shared folder on NAS
Videos    my_local_ipr:/volume1/Videos

```persmissions of files re:

```

xbmc@XBMCLive:/mnt/NAS$ ll /etc/auto.*
-rw-r--r-- 1 root root  719 2011-09-07 23:51 /etc/auto.master
-rw-r--r-- 1 root root 1374 2010-08-17 07:35 /etc/auto.net
-rw-r--r-- 1 root root  747 2011-09-07 23:52 /etc/auto.type
xbmc@XBMCLive:/mnt/NAS$ 

```and also, the /etc/nsswitch.conf have that last line:

```

xbmc@XBMCLive:/mnt/NAS$ cat /etc/nsswitch.conf 
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

automount: files
xbmc@XBMCLive:/mnt/NAS$ 


```Looking forward any kind of help/feedback

---

