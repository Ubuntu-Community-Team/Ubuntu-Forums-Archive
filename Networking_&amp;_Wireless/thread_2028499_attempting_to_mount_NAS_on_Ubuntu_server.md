---
title: "attempting to mount NAS on Ubuntu server"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by StariBrko on 2012-07-18
My LAN contains several Windows XP/7 boxes (IPs : 192.168.0.10x), Ubuntu 10.10 Maverick Meerkat server (IP: 192.168.0.11) and WD 4T Sharespace NAS (IP: 192.168.0.9).

Windows workstations can access NAS directly. There are shared directories on NAS that can be mapped from windows machines.

I set Bind9 DNS server on Ubuntu server and it works fine

Ubuntu can ping NAS but it cannot browse through files and directories (it needs to be mounted…)

Upon root login on NAS, executing *uname –mrs* command returns:
**Linux 2.6.12.6-arm1 armv5tejl**

Executing *mount* command on NAS gives the following info:

[B]/dev/root on /old type cramfs (ro)
proc on /old/proc type proc (rw,nodiratime)
/dev/md0 on / type ext3 (rw,noatime)
proc on /proc type proc (rw,nodiratime)
/proc/bus/usb/ on /proc/bus/usb type usbfs (rw)
/dev/pts on /dev/pts type devpts (rw)
trusteesfs on /trustees type trusteesfs (rw)
/dev/md2 on /DataVolume type ext3 (rw,noatime)
/dev/ram0 on /mnt/ram type tmpfs (rw)
/dev/md2 on /shares/Public type ext3 (rw,noatime)
/dev/md2 on /shares/Download type ext3 (rw,noatime)
/dev/md2…[/B]

The rest is the same…   
…on /shares/TheRestOfSharedDirectories type ext3 (rw,noatime)

I tried command (from Ubuntu machine):
*sudo mount –t nfs 192.168.0.9:/nfs/MYSHAREDFOLDER /my_mounting_point*
as well as
*sudo mount –t nfs 192.168.0.9:/MYSHAREDFOLDER /my_mounting_point*

and received the following responds (respectively):
**mount.nfs: access denied by server while mounting 192.168.0.9:/nfs/MYSHAREDFOLDER** and 
**mount.nfs: access denied by server while mounting 192.168.0.9:/MYSHAREDFOLDER**

I tried both options because I found the following info while I was browsing NAS setup:
_Mount point for NFS share is /nfs/SHARENAME, Ex. /nfs/Public_

What should I do in order to mount above mentioned NAS on Ubuntu?

Thanx for your responds

---

### Post by steeldriver on 2012-07-18
I think that guide is confusing you - the 'nfs' part is not meant to be literal - it should be the hostname (if you have local name resolution) or IP of the nfs server, for example if I have a NAS with IP 192.168.1.127 and share name 'public', and I want to mount it at /mnt/nas-01/public,  I would do 

```
sudo mkdir -p /mnt/nas-01/public
sudo mount -t nfs 192.168.1.127:/public /mnt/nas-01/public
```You can get the share list either from the server's /etc/exports file or by executing 'showmount -e *server*' from the client - if you do the latter, be aware it may prepend the actual share name with a parent directory e.g. "/c/public" - the "/c/" is NOT part of the share name.

You need to have package nfs-common installed on the client machine

---

### Post by StariBrko on 2012-07-18
Exactly!
I agree with everything you have commented.
Actually, I have literally done the very same procedure you wrote in your comment:
[LIST]
[*]I did install nfs-common package on Ubuntu box (client machine);
[*]I did create mounting point on client machine (MYSHAREDFOLDER);
[*]I did type *mount *command exactly the same way as you did in your comment;
[/LIST]
Basically, I did everything by the book (or at least I think I did...)

Nevertheless, the respond I received upon executing *mount *command was:
**mount.nfs: access denied by server while mounting 192.168.0.9:/MYSHAREDFOLDER**

Hence the thread at first place...:(

Therefore, any idea is more than welcome...

---

### Post by steeldriver on 2012-07-18
did you confirm that the NAS is actually exporting nfs shares (not just samba - which is what the windows boxes will be using)?

```
showmount -e 192.168.0.9
```

---

### Post by StariBrko on 2012-07-19
I just run the command ```
showmount -e 192.168.0.9
``` from Ubuntu box that should be NAS client, and got the following:

```
Export list for 192.168.0.9:
/DataVolume/Public         *
/DataVolume/Download       *
/DataVolume/BackupPoint    *
/DataVolume/MyNetworkShare *

```
So, it seems that NAS is exporting nfs shares all right

---

### Post by StariBrko on 2012-07-19
And the winner is:
```
sudo mount -t **_cifs_ **192.168.0.9:/*MyNetworkShare* /*MyMountigPoint* -o username=*MyUserName*,password=*MyPassword*
```

It just worked as a charm.
Suppose, if I add a corresponding line to /etc/fstab, my NAS should be mounted automatically each time during boot process.
Right?

---

