---
title: "idmapd and NFS v4 setup for NAS access - UID/GID issues"
date: 2021-05-26
forum: MINT
---

### Post by bedege on 2021-05-26
Hello there

I'm running Linux Mint 20.1 Cinnamon on my desktop and am trying to access my Synology NAS NFS shares from it. I'm on a home network, but the user UID/GID do not align between the server (Synology) and the client. I understand that idmapd must be running on both NFS server and client in order to properly have the same user names align, eventually. Similarly, I understand that I must use NFS v4 for idmapd to work.

In any case, I was able to have [FONT=Courier New]idmapd[/FONT]  running on the Linux Mint client side, by installing the [FONT=Courier New]nfs-kernel-server[/FONT] package and now have [FONT=Courier New]idmapd[/FONT] up and running on the client.

```
$ sudo systemctl status nfs-idmapd  
&#9679; nfs-idmapd.service - NFSv4 ID-name mapping service
     Loaded: loaded (/lib/systemd/system/nfs-idmapd.service; static; vendor preset: enabled)
     Active: active (running) since Tue 2021-05-25 17:39:22 CEST; 49min ago
    Process: 11772 ExecStart=/usr/sbin/rpc.idmapd $RPCIDMAPDARGS (code=exited, status=0/SUCCESS)
   Main PID: 11774 (rpc.idmapd)
      Tasks: 1 (limit: 9113)
     Memory: 604.0K
     CGroup: /system.slice/nfs-idmapd.service
             &#9492;&#9472;11774 /usr/sbin/rpc.idmapd

mai 25 17:39:22 Tatihou systemd[1]: Starting NFSv4 ID-name mapping service...
mai 25 17:39:22 Tatihou systemd[1]: Started NFSv4 ID-name mapping service.
```

In [FONT=Courier New]/etc/idmapd.conf[/FONT], the domain has been set to the same name, on both server and client.

However, I don't know what to use in terms of Mapping in [FONT=Courier New]idmapd.conf[/FONT] so that usernames are properly translated, thus permissions are properly granted.

Does anybody have any mileage regarding this type of setup between a Linux box (Ubuntu-based) and a Synology NFS server?
In particular
- what Translation should be used between static, nsswitch and umich_ldap?
- what logfiles should I look into to make sure that idmapd properly works?

Any pointer to a working solution would be welcome. I've looked at tons of forum pages (for Linux Mint, Ubuntu and Synology) but haven't seen the light yet. Also, I don't want to have to install Kerberos or LDAP. This is simply a family LAN I'm working on!

Cheers

bedege

---

### Post by jeremy31 on 2021-05-26
Moved to Mint

---

### Post by TheFu on 2021-05-26
No clue about Synology.

I've never seen idmapd actually work on **any** Unix.  Moving to centralized user/group management is the best practice and solves this issue.

Often the easy answer is to manually align the userids across all systems.  Just make the human userids match and whatever groupids you want used on the NAS storage needs to match on all systems.  Doing this isn't hard. There are just 2 text files in /etc/ to change and they aren't hard to understand. But the order that you make the changes is very important, so that sudo keeps working.  Of course, you should have a "Try Ubuntu" live boot environment ready and working to mount the /etc/ storage and fix any of the files if needed.

Files:
/etc/passwd
/etc/group

The shadow and gshadow files don't need to be changed unless you modify more than just the numbers. Leave the username and groupnames alone, and all will be fine, unless you need to add some groups across some systems to have consistency.   

BTW, when it is time to change passwords, 'expect' is the killer app for that.  Lots of examples for that exist online.
But really, using LDAP for centralized user management would be the correct answer.   [https://ubuntu.com/server/docs/service-ldap](https://ubuntu.com/server/docs/service-ldap) I understand there are GUIs to manage LDAP.

If you really don't care about security, NIS is fairly easy to setup, but it is highly non-secure.  NIS is the early 1990s way we had centralized passwd, group, hosts, and netgroup databased that could be used by any Unix-like OS.  Back then, it was under 15 minutes to setup and configure a server and 2-50 client machines.  I stopped using NIS at home due to security considerations in the early 2000s.  NIS+ was the follow on solution, but Sun Microsystems only released the client code. They retained the server-side code and never ported it from Solaris. That attempt at locking down NIS+ failed, as we all know.

As for logfiles - they are in /var/log/. If you use grep to search all the files for errors or warnings, then there isn't any need to know exactly which file. Search them all. It isn't hard. [https://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](https://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

You are correct. This should be easier. When I had centralized LDAP, it was managed by another complex tool. It worked very well, but that other tool would break it at each upgrade, so I decoupled the logins.  I miss having 1 password to change, but with ssh that really isn't an issue very often.

---

### Post by bedege on 2021-05-26
> **TheFu said:**
> No clue about Synology.

I've never seen idmapd actually work on **any** Unix.  Moving to centralized user/group management is the best practice and solves this issue.



Hello
Thanks for the feedback. Needless to say, I find it really strange that idmapd is so difficult to master and so poorly documented (with real life examples I mean).
My expectation when I bought the NAS couple of years ago was that since Server and Clients were running some *nix flavor of some sort, and NFS being *the* *nix file sharing protocol then aligning all this would be a breeze.

Apparently it's not the case. So I guess I'll have to manually change the UIDs on my clients.

If anybody around has a different experience, please shout :)

---

### Post by TheFu on 2021-05-26
> **bedege said:**
>  If anybody around has a different experience, please shout :)

I'd love to know as well!  Or a simple way to have (AND maintain) centralized user and group management.

BTW, NFSv4 doesn't require Kerberos. See:
```
$ dft
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--mate-root ext4   19G   14G  4.1G  78% /
/dev/mapper/vgubuntu--mate-home ext4   12G  6.3G  4.9G  57% /home
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi
istar:/d/D1                     **nfs4**  3.5T  3.5T   16G 100% /d/D1
istar:/d/D2                     **nfs4**  3.6T  3.6T   10G 100% /d/D2
istar:/d/D3                     nfs4  3.6T  3.6T  9.3G 100% /d/D3
romulus:/raid/media             **nfs4**  1.8T  1.7T   20G  99% /R
romulus:/Data/r2                **nfs4**  1.3T  1.2T   67G  95% /S

```
I can assure you that I do NOT have Kerberos on any of those machines.  I am using **autofs** to handle the mounts, however.  I use autofs for all network and USB mounting needs.

---

### Post by bedege on 2021-05-26
> **TheFu said:**
> 
I can assure you that I do NOT have Kerberos on any of those machines.  I am using **autofs** to handle the mounts, however.  I use autofs for all network and USB mounting needs.

I fully understand. I've been using NFS v4 and autofs for quite a while. I really love the speed of NFS access compared to Samba which I used before.

However, the *only* thing I've been unable to grasp is [FONT=Courier New]idmapd[/FONT] and being able to translate usernames via NFS. I've read in so many threads that it is broken that it doesn't make sense to me, given how long it's been around.

Go figure

---

### Post by TheFu on 2021-05-26
> **bedege said:**
> I fully understand. I've been using NFS v4 and autofs for quite a while. I really love the speed of NFS access compared to Samba which I used before.

However, the *only* thing I've been unable to grasp is [FONT=Courier New]idmapd[/FONT] and being able to translate usernames via NFS. I've read in so many threads that it is broken that it doesn't make sense to me, given how long it's been around.

Go figure

I'm not sure that it is broken, just that I've been unable to figure out how to get it working - at least not with rpc.idmapd and static mappings.  
This [https://unix.stackexchange.com/questions/438939/how-to-get-nfsv4-idmap-working-with-sec-sys](https://unix.stackexchange.com/questions/438939/how-to-get-nfsv4-idmap-working-with-sec-sys) says that the only way to get things working is with Kerberos.  The name mapping works without Kerberos, but the uid/gid mapping does not, so while the translation from uid--> username works, since the storage only cares about the uid/gid that doesn't really help.

And when you change the uid for a user on a system, don't forget to chown all the files from the old uid to the new uid or it will be bad.  Fortunately, we generally only need to worry about uids and gids over 1000.  OSX begins uids at 500, so moving those out to 1000 will be needed for all OSX clients.

If we just create userids in the same order on Linux systems, the name --> uid numbers should map fine. No help for OSX, sorry.  There is good news.  Because only the numbers uid/gid matter, we can have different usernames and groupnames on the different systems. Sorta a hack, but it works.

---

### Post by bedege on 2021-05-28
Hello there
More on my predicament...

I did modify my UID and GID on the client side, which means that both on Server and Client, I share the exact same values : 1026 and 100 respectively

On the server (Nasquatch)
```
benoit@Nasquatch:~$ id
uid=1026(benoit) gid=100(users)
```

On the Client (Tatihou)
```
benoit@Tatihou ~ $ id
uid=1026(benoit) gid=100(users)
```

Having done that, I'm not sure what to use in /etc/idmapd.conf. Since I don't have LDAP or Kerberos installed, I thought that Static was the way to go, so that my idmapd.conf looks like

```
benoit@Nasquatch:~$ sudo cat /etc/idmapd.conf 
[General]
Domain=evergreen
[Mapping]
Nobody-User=guest
Nobody-Group=users
[Translation]
#Method=nsswitch
Method=static
#GSS-Methods=static,synomap
[Static]
benoit@evergreen = benoit
```

However, this does not seem to work.

Cound somebody around share their /etc/idmapd.conf file so that I can understand the differences between Static, nsswitch and synomap, and start from there?

Thanks

---

### Post by TheFu on 2021-05-28
The /etc/idmapd.conf should be left at the default if the uid/gid match on the clients.  I don't think it matters what the NFS server knows about uid, unless you typically access the files locally on the server too.

Here's the default:
$ more /etc/idmapd.conf 
```
[General]

Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if it differs from FQDN minus hostname
# Domain = localdomain

[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup
```

---

