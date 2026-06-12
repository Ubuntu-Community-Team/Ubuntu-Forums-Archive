---
title: "FTP shares won't mount on startup [Curlftpfs]"
date: 2011-12-31
forum: Networking &amp; Wireless
---

### Post by jamespetts on 2011-12-31
I have recently set up a NAS device (a WD Mybook Live) as a backup device for my parents' computers. It connects to three other computers running Ubuntu 11.10 over a wired network, connected using a Thompson Speedtouch 546 router/switch. 

The Mybook Live has NFS support, but I found this to be very unreliable in practice, and, in the end, could not connect to it using NFS at all. Looking at WD's forums, it seems that they do not support the NFS option at all.

It does, however, support FTP. Using Curlftpfs, I was able to get it to connect to the computers' backup folders as transparently as if it was running NFS. Deja Dup backup ran very smoothly, and the transfer speed was impressively fast.

However, on turning the computers on again in the morning, they will fail to connect to the /backup mount when first starting up, giving an error message about being unable to mount /backup, asking whether I want to skip mounting or go into a recovery console.

If I go into the recovery console and try sudo mount -a, it fails to mount anything, as the network is unreachable. I can confirm this by failing to ping anything other than the loopback interface. If I skip mounting, then log in and go into the terminal and type sudo mount -a, the mounting works every time. This is specific to the Curlftpfs mounts, however, as other nfs mounts (to another computer on the network) work on startup without difficulty.

The relevant lines of my /etc/fstab file are:

```

192.168.1.65:/   /mnt   nfs4    _netdev,auto  0  0
curlftpfs#mounter:*******@mybooklive/Public /backup fuse auto,user,uid=1000,allow_other 0 0

```

I have checked, and even replacing the "mybooklive" name with the unit's local IP address (192.168.1.67) produces the same result. The computer on 192.168.1.65 mounts using nfs without difficulty on startup. 

Am I missing something? Do I need to add a line to a configuration file somewhere telling curlftpfs to load sooner in the bootstrap process, perhaps? Any assistance would be much appreciated.

---

