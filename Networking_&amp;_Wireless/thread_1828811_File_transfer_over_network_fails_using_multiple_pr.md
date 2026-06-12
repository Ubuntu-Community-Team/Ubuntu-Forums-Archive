---
title: "File transfer over network fails using multiple programs"
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by devmage on 2011-08-19
So, I'm trying to move a set of files from my personal machine to my server, over my network. The file set is approximately 40GB total, with file sizes varying from kilobytes to tens of megabytes. So far, I cannot transfer more than the first few megabytes without the server locking up entirely, forcing a hard reboot. The actual amount transferred is unpredictable - in some cases, I can move across a few tens of megabytes; in others, it fails on the first file. I have reproduced this with all of: NFS, SFTP initiated client-side, SCP initiated server-side, Rsync initiated server-side (with bwlimit=5000, even).

My personal machine is a Macbook Pro with Remote Login (ssh) enabled, though I have also had similar problems transferring from an older Dell Latitude with Ubuntu and another MBP. I've just done the most extensive troubleshooting with this one machine. The network is gigabit-capable on both devices and the router between them.

My server is an ASUS EeeBox EB1006 (Atom N270, 2GB memory) running 11.04 with the server kernel, with a 2TB external USB drive attached, all drives formatted as ext4. It has enabled a Samba share and an NFS share, as well as a couple background services (e.g. BOINC). The relevant /etc/exports line for the NFS share is:
```
/media/Bank	192.168.1.0/255.255.255.0(rw,nohide,insecure,no_subtree_check,async)

```
The Samba configuration is less interesting, but if needed I can post parts of it.

The server itself is rather small, but its specs if needed can be found [on Newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16883220013") and others. I recently upgraded the memory to 2GB, but I had been having this problem before upgrading as well. Fsck reports that all disks are clean, and I don't believe that it is a memory error unless I have somehow encountered two consecutive bad sticks.

It really disturbs me that *any* notably large network transfer causes this hard lock-up to occur. Transfers that are local to the server (e.g. from the server's internal hd to the external) work fine. I've also tried transferring both to the external and the internal. in case it were some kind of write bottleneck on the external, but the problem persists regardless of the transfer destination.

It also seems that I am not alone (e.g. [this poster]("http://ubuntuforums.org/showthread.php?t=1478413")) in problems related to network transfer, however my problem is not NFS-specific.

Help? Thanks in advance for suggestions on how to remedy this. Please let me know if there is more information about my setup that I should post.

---

### Post by gordintoronto on 2011-08-19
I don't know if this will help, but I run exactly one type of sharing on a server. Actually, I would install Ubuntu LTS Desktop, and use Nautilus to set up Samba shares. Perhaps having a Mac in the picture means you should use NFS, and not Samba.

Server is great for high-volume web sites, but most people find it awkward.

---

### Post by devmage on 2011-08-20
Unfortunately, the dual sharing setup is a necessity for my network environment. I also have a Windows machine that needs to read data from the server as well, so it connects through the Samba share. I do use NFS when I connect from the Mac, though, as it results in faster transfers overall.

But what's the point of transfer speed, when writing more than like a megabyte at a time causes a lockup? :(

I don't exactly see why having *any* particular sharing daemons active would impact a sftp or scp transfer to an unrelated part of the machine. That was my point in testing whether the problem persisted when I transferred to the server's internal hd over sftp and scp, versus to its external over one of the shares.

How exactly might LTS help? From all I'm seeing across other threads, it seemed to be a problem for some users that was resolved in an updated kernel, which may or may not have made it to LTS. I'd also have to downgrade the server, which isn't something I'd prefer to do...

Thanks all the same for the response, though. I'm glad there are eyes reaching this post!

---

### Post by devmage on 2011-08-20
For reference, I just tried queueing up the transfer in FileZilla in XFCE on the server (normally I access it headless, but I have a monitor on the side for troubleshooting), pulling from the Macbook over SFTP. It lists the files fine, builds the transfer queue and begins transferring, but the whole system locks up after less than a gigabyte's worth of transfer.

---

### Post by devmage on 2012-01-30
Revisiting this problem, I today tried to push files over Samba, after modifying my smb.conf to allow writing. One folder, about 170 MB in size, pushed fine. A second folder, about 500 MB, failed after the first 200 MB or so.

I still have no good explanation for this issue, nor can I find any relevant logs. Any help would be appreciated.

---

### Post by gordintoronto on 2012-01-30
My guess: it's a hardware problem on the server. 20% confidence!

---

### Post by devmage on 2012-01-30
It's entirely possible! I'm hoping to rule out everything else that I can, before ruling it as an auto-immune disorder.

I'll see if there are any known disorders with that particular line of machine, or its components. I wouldn't be surprised if it were just a poor Atom chip, as the Atom lines tend to be fairly low-grade anyway.

---

