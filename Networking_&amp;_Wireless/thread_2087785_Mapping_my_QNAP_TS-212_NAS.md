---
title: "Mapping my QNAP TS-212 NAS"
date: 2012-11-24
forum: Networking &amp; Wireless
---

### Post by lewisskinner on 2012-11-24
Hi all.  A little help here please.

As the titles suggests, I have a QNAP TS-212.  The nice easy "map network drive" feature on Virista works surprisingly well, but I can't get it mapped on Ubuntu.

I've followed [this guide](http://ubuntuforums.org/showthread.php?t=249889), but when I run the first command, *sudo apt-get install nfs-kernel-server nfs-common portmap*, I get the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'rpcbind' instead of 'portmap'

```

The remainder of the commands on this post relate to portmap, not rpcbind.  Where do I go from here?

---

### Post by lewisskinner on 2012-11-26
bump.  Anyone with any ideas?

---

### Post by Statia on 2012-11-26
Coincidentally, I installed and configured NFS today on a home-brew NAS (EEEPC 701 with external USB drive) and came across the same mention about portmap.
However, all I had to do was edit /etc/exports and start the server and it worked for me.
So just try following all steps except the ones that relate to portmap and see if it works.

DISCLAIMER: I did not bother with any security, since this runs on a small home network and is not accessible from the Internet.

---

### Post by lewisskinner on 2012-11-26
Just getting the following:

```
lewis@Arcadia:~$ sudo mount //192.168.0.10 /HomeNAS
mount: wrong fs type, bad option, bad superblock on //192.168.0.10,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by dannyboy79 on 2012-11-26
are you sure your shares are being shared via NFS? You mention previous drive mapping in Vista working flawlessly which leads me to believe that they are SAMBA shares from your QNAP. You would use the CIFS protocol, not NFS.

---

### Post by Statia on 2012-11-27
Sharp observation, Dannyboy79. He wrote about "Virista" and I thought that was some Windows software that is unknown to me.
But indeed, when he is mapping drives to Windows (Vista), he'll be using SMB and should look at samba for Linux.

(People actually use Vista:confused: )

---

### Post by lewisskinner on 2012-11-29
No, I don't use Vista.  It came with my PC, and I've kept it for the occasions I play video games away from my console, or for occasions such as this :-?.  I am not attempting to access the NAS from Vista and Ubuntu simultaneously.  In otherwords, whilst Vista may be using SMB, The NAS is able to use SMB and NFS (and indeed FTP and AFP)

QNAP's [own documentation](http://docs.qnap.com/nas/en/index.html?share_folders.htm) states:

[quote=QNAP]**Linux Users**

On Linux, run the following command:

mount -t nfs <NAS IP>:/<Network Share Name> <Directory to Mount>

For example, if the IP address of the NAS is 192.168.0.1, to connect to the network share &#8220;public&#8221; under the /mnt/pub directory, use the following command:

mount -t nfs 192.168.0.1:/public /mnt/pub[/quote]

So, I've tried both following the instructions in the above linked post, and running
```
 mount -t nfs 192.168.0.10/web /HomeNAS
```
and variations thereof, ie
```
mount -t nfs 192.168.0.10/web /HomeNAS
mount -t nfs 192.168.0.10:/web /HomeNAS
mount -t nfs //192.168.0.10/web /HomeNAS
mount -t nfs //192.168.0.10:/web /HomeNAS
mount -t nfs 192.168.0.10/public /HomeNAS
mount -t nfs 192.168.0.10/Multimedia /HomeNAS

```etc

Can someone please enlighten me as to the use of NFS/Samba?  I assumed that these were software packages I needed to install on the PC I'm using (ie the Vista/Ubuntu dual-boot box) to access the NAS - not on the NAS itself.  You can see that QNAP's own instructions indicate an NFS command and, as stated earlier, both are available.  The instructions for Vista essentially just state to right-click "computer", click "map network drive" then enter the IP and username/password, so I see no reason why it should be so difficult on Linux?

---

### Post by dannyboy79 on 2012-11-30
are you certain the share name is web and is called web for NFS? I know your QNAP is capable of CIFS/SMB, AFP(3.1), NFS, FTP, HTTP, HTTPS but it's not setup by default I wouldn't think since you have to choose which folders to share and by which protocol. It may be called web but only for SAMBA? Yes, you're correct in saying that you need to install the correct software within Ubuntu. The QNAP already has all the correct software BUT it's probably not configured by default.

Since you can obviously can mount it in Vista is the one reason I know for certain that it is sharing that certain folder as SAMBA (SMB). 

Have you tried this to see what shares are available?
```
smbclient -L 192.168.0.10
```

You may have to install smbfs
```
sudo apt-get install smbfs
```
before you can use smbclient. Also, is the username on your ubuntu machine the same as the username you used for credentials when connecting on Vista?

On a side note what are the permissions on the folder /HomeNAS? I would suggest creating the folder within /mnt/ versus having it at the root level.

---

### Post by steeldriver on 2012-11-30
... agree with the above, OTOH if you *do* want to do it via NFS then it should be as simple as

1. install nfs-common

```
$ sudo apt-get install nfs-common
```2. check the export list from your server

```
~$ showmount -e 192.168.1.127
Export list for 192.168.1.127:
/c/home    *
/c/media   *
/c/public  *
/c/backup  *
/USB_HDD_1 *
```3. make a suitable mount point

 ```
sudo mkdir -p /mnt/nas-01/public
```4. mount the chosen export

```
$ sudo mount -t nfs 192.168.1.127:/c/public /mnt/nas-01/public/
```(fwiw the share name is 'public' and 192.168.1.127:/public also works - not sure that is always the case, I don't really understand the share naming conventions)

This works for my Netgear ReadyNAS anyhow - hope this helps

---

### Post by lewisskinner on 2012-12-01
Thanks both of you.  /web is a share drive, and I've set the others.  The advice from  steeldriver got me mounted - thank you!

---

