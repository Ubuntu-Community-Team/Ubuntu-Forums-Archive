---
title: "Mounting NFS Between Ubuntu VMs"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by spartan21 on 2012-06-19
I am running two Ubuntu VMs, and I am trying to mount a directory from one on the other.  I followed the instructions on [**this**]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch29_:_Remote_Disk_Access_with_NFS") page, i.e. I have the required packages, NFS is running correctly on both client and server, I edited the server-side /etc/exports file, and I believe I entered the correct command on the client.

My /etc/exports file on the server includes the line:

```
/home/serverUSER  client.ip.add.ress(rw,sync,no_subtree_check)
```

The command I run on the client is:

```
sudo mount -t nfs serverUSER@server.ip.add.ress:Documents/ servermount/
```

After executing, I get the following error:

```
mount.nfs: Failed to resolve server serverUSER@server.ip.add.ress: Name or service not known
```

I can ssh between VMs, and I can successfully mount using SSHFS, but so far NFS has been unsuccessful.  Any ideas would be greatly, greatly appreciated.  Thanks!

__

---

### Post by SeijiSensei on 2012-06-19
If you want to mount the share as root on the client, add "no_root_squash" to the options on the server.  Then use:

```
sudo mount server:/home/serverUSER /mountpoint
```

You don't need "user@" like with SSH.

---

### Post by spartan21 on 2012-06-19
Thanks for your help!  When I followed your advice, I received the error

```
mount.nfs: access denied by server while mounting server.ip.add.ress:Documents
```

But I figured out what was causing this.  My problem was that I was mounting using 

```
mount server.ip.add.ress:Documents /mountpoint
```

In /etc/exports I listed the export directory as /home/serverUSER/Documents.  While both paths are technically equivalent, mounting only worked when the directory paths matched exactly, as in:

```
mount server.ip.add.ress:/home/serverUSER/Documents /mountpoint
```

---

### Post by SeijiSensei on 2012-06-19
That's because, while you may see the two as "technically" equivalent, NFS doesn't treat them the same way.  If you export /home/user/Documents, then /home/user isn't available.  You can only mount /home/user/Documents and directories below it if subtree checking is disabled as it is by default.

Without checks like these NFS could inadvertently allow you to manipulate files over the network that you wouldn't have permission to change on the server itself.

---

