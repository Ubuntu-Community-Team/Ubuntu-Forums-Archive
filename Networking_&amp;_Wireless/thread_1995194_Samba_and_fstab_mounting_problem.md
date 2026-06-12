---
title: "Samba and fstab: mounting problem"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by Ptallqvist on 2012-06-03
Hello,
I have two ubuntu machines, server and client. The server shares documents via samba to the client, which mounts the samba shares automatically with fstab. I replaced the client with a new computer and now the samba stopped working. I have the exact same fstab as in the old client. The relevant lines are as follows:

Server's smb.conf:
```
[files]
        path = /files
        comment = fileshare
        browseable = yes
        valid users = user1
        writable = yes
       guest ok = no
```

Client's fstab:
```
//192.168.100.22/fileshare /home/shared_files/ cifs username=user1,passwd=password 0 0 
```

When doing a 'mount -a', I get no errors. Also, dmesg shows no errors.

'Mount' seems to show that everything is ok:
```
//192.168.100.22/fileshare on /home/shared_files type cifs (rw)
```

I can browse to the folder /home/shared_files, but it is empty.

When I try to mount manually with 'sudo smbmount //192.168.100.22/fileshare /home/shared_files -o user=user1', it works, so I am assuming the problem is in the fstab file and this is not  server or network issue.

What should I try next?

---

### Post by steeldriver on 2012-06-03
do you see any messages from mount in /var/log/dmesg (especially things like 'not ready'?

this really is ONLY a guess but I wonder if the new client machine uses the network-manager service and the old one used the traditional networking service (via /etc/network/interfaces), and if so whether the start order is later for network-manager since it's more of a userland thing and the interface is not yet up when it tries to mount?

a lot of ifs I know

---

### Post by zSeries on 2012-06-03
You may still need map the incoming Windows user user1 to Linux user user1.  Have you done that?

---

### Post by Ptallqvist on 2012-06-10
Thank you for the replies.

I don't know what you mean by mapping the incoming user? 

This is really weird, as all this worked just fine before upgrading to 12.04. Could of course be a coincidence.

EDIT:
I tried this with a laptop, running ubuntu 11.10,, and its dmesg shows this:
```
[   33.689535] init: apport pre-start process (1019) terminated with status 1
[   33.700579] init: apport post-stop process (1063) terminated with status 1
[   33.764942] init: gdm main process (1051) killed by TERM signal
[   34.290294] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.306208] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
[   34.364979] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.373876] Adding 1037308k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:1037308k 
[   34.408962] CIFS VFS: Error connecting to socket. Aborting operation
[   34.422958] CIFS VFS: Error connecting to socket. Aborting operation
[   34.429762] CIFS VFS: cifs_mount failed w/return code = -101
[   34.431706] CIFS VFS: Error connecting to socket. Aborting operation
[   34.444349] CIFS VFS: cifs_mount failed w/return code = -101
[   34.447440] CIFS VFS: cifs_mount failed w/return code = -101
```

Now, when I check the desktop-client's dmesg after a reboot, it shows this:
```
[   19.075495] CIFS VFS: Error connecting to socket. Aborting operation
[   19.076859] r8169 0000:04:00.0: eth0: link down
[   19.076863] r8169 0000:04:00.0: eth0: link down
[   19.077004] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.077140] CIFS VFS: cifs_mount failed w/return code = -101
[   19.078432] CIFS VFS: Error connecting to socket. Aborting operation
[   19.078523] CIFS VFS: cifs_mount failed w/return code = -101
[   19.078957] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.177570] CIFS VFS: Error connecting to socket. Aborting operation
[   19.177824] CIFS VFS: cifs_mount failed w/return code = -101
[   19.181234] CIFS VFS: Error connecting to socket. Aborting operation
[   19.183513] CIFS VFS: cifs_mount failed w/return code = -101
[   19.232961] CIFS VFS: Error connecting to socket. Aborting operation
[   19.233299] CIFS VFS: cifs_mount failed w/return code = -101

```

So, it seems like you are onto something, steeldriver. Now, what can I do to fix this? :)

---

### Post by steeldriver on 2012-06-10
well I did a bit of reading around the subject, there's some kind of signaling between network-manager and mountall (via upstart) but I'm still not clear whether that is expected to happen in strict order (local-filesystems, then networking, then remote-filesystems) or whether mountall  just keeps re-trying the mount regardless of signals from the various network service upstarts

there's a (rather old) bug report/discussion here:

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/447649](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/447649)

I guess you could see if the behavior is different if you revert to defining your interface via /etc/network/interfaces instead of (presumably) using network-manager?

---

### Post by Ptallqvist on 2012-06-11
I disabled network-manager (like [this]("http://www.liberiangeek.net/2012/03/disable-network-manager-in-ubuntu-11-10-oneiric-ocelot/")), but it still wouldn't work. After I added gid=user1 to the fstab samba lines, it seems to work. I still can't quite figure out what the problem(s) were, but I'm happy it works.

Maybe this whole episode would have been easier with a native linux solution, like nfs?

Thank you all for the help!

---

### Post by roelforg on 2012-06-11
> **Ptallqvist said:**
> I disabled network-manager (like [this]("http://www.liberiangeek.net/2012/03/disable-network-manager-in-ubuntu-11-10-oneiric-ocelot/")), but it still wouldn't work. After I added gid=user1 to the fstab samba lines, it seems to work. I still can't quite figure out what the problem(s) were, but I'm happy it works.
 
Maybe this whole episode would have been easier with a native linux solution, like nfs?
 
Thank you all for the help!
 
It would.
This is how one of my systems automounts a nfs share:
```

<ip_of_server>:/export/share /mnt/servershare nfs defaults 0 0

```
where /mnt/servershare is chmod 777 and is owned by group admin (thereby allowing my user to use it too).
I'm sure i added some flags to allow the execution of binaries too, but i forgot and i'm not able to reach that system now.

---

