---
title: "NFS Export not allowing read write"
date: 2013-03-01
forum: Networking &amp; Wireless
---

### Post by wt9bind on 2013-03-01
Hi,

I am running 12.04.2 LTS, Mediatomb, Deluge, Webmin and NFS Exports. As a Mediaserver

My Client machine is a mac.

If I connect to NFS by: Command+K nfs://IP/export/TV/TV

It connects, lists the directory and allows me to execute but I can't create folders or files.

My FSTAB Looks like this:
```
  GNU nano 2.2.6                               File: /etc/fstab                                                                    

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f4fff3f1-1007-48df-b4c4-a59acd621102 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=225e9a95-7f10-4fe6-8495-c47ba1d608a9 none            swap    sw              0       0
# movies entry
UUID=0000a369-1d53-49de-914d-0ae8b7b1c53c /media/Movies ext4    auto,rw 0       0
# TV Entry
UUID=900d9a55-413f-43a7-b473-3ebe7abcecc0 /media/TV     ext4    auto,rw 0       0
# Music Entry
UUID=36aef72e-188f-4679-8f44-01e1a8a5a63f /media/Misc   ext4    auto,rw 0       0
# Kids Entry
UUID=025dc5a7-c33e-4727-bee8-81eb1fb46c64 /media/Kids   ext4    auto,rw 0       0


/media/Kids/TV  /export/TVExtra bind    bind    0
/media/Movies   /export/Movies  bind    bind    0
/media/Misc     /export/Misc    bind    bind    0
/media/TV       /export/TV      bind    bind    0
/home/ftp       /export/FTP     bind    bind    0
/var/lib/deluge /export/Torrent bind    bind    0
```


My Exports looks like this:
```
  GNU nano 2.2.6                              File: /etc/exports                                                                   


# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/export (insecure,no_subtree_check,rw,nohide,fsid=0)
/export/TVExtra    192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check,nohide)
/export/Movies  192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check,nohide)
/export/Misc    192.168.1.0/255.255.255.0(sync,anongid=1000,no_subtree_check,no_root_squash,anonuid=1000,insecure,rw,nohide)
/export/TV/TV   192.168.1.0/255.255.255.0(sync,anongid=1000,no_subtree_check,no_root_squash,anonuid=1000,insecure,nohide,rw)
/export/FTP 192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check,nohide)
/export/Torrent 192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check,nohide)



```



I can confirm that I belong to 1000:
```
user@SVR1:/var/lib/deluge$ id -u user
1000
user@SVR1:/var/lib/deluge$ id -g user
1000
```





Can somebody tell me why? This has worked perfectly in the past but after rebuilding my server it is no longer working the same way.

Thanks

---

### Post by luvshines on 2013-03-02
What are the permissions on the exported path ? Is this UID/GID allowed to write ?

---

### Post by wt9bind on 2013-03-02
Thanks for the reply luvshines.

UID has the permissions of: 
drwxr-xr-x 73 on the directory, but I think I have worked it out but I don't know how or why.


```

  GNU nano 2.2.6                         File: /etc/exports                                                        


# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
/export *(insecure,no_subtree_check,rw,nohide,fsid=0)
/export/TVExtra    192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check,nohide)
/export/Movies  192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check,nohide)
/export/Misc    192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check,nohide)
/export/TV/TV   192.168.1.0/24(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check,nohide)
/export/FTP 192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check,nohide)
/export/Torrent 192.168.1.0/255.255.255.0(rw,sync,all_squash,insecure,anonuid=1000,anongid=1000,no_subtree_check,nohide)






```


But I ran: sudo exportfs -a
And got a message about if I don't have a "*" in /export *(insecure,no_subtree_check,rw,nohide,fsid=0) that it would mess up (obviously not the exact message) so I added it, ran exportfs -a again, the message wasn't there and I could then write to the folders.

So my problem is solved but I don't know why exactly.

---

### Post by luvshines on 2013-03-03
It's good that the issue is resolved for you
But adding '*' should not have made difference since specifying no hostname is same as *

Weird !! Maybe in you leisure, try removing that * again, reexport and then check if you are back to this issue. Also capture some network traces to see what call is failing.

---

### Post by wt9bind on 2013-03-03
Thanks luvshines,

I removed the "*", re-ran exportfs -a and you are right, I can write to the shares.

I got this error of course:
```
d@B:~$ sudo exportfs -aexportfs: No host name given with /export (insecure,no_subtree_check,rw,nohide,fsid=0), suggest *(insecure,no_subtree_check,rw,nohide,fsid=0) to avoid warning



```

I am starting to think when I set these Exports up, I didn't run exportfs -a but was going into Webmin and applying changes there as I didn't know the command in SSH. I wonder if Webmin actually wasn't applying the changes and it was configured correctly but wasn't being applied.

---

### Post by luvshines on 2013-03-04
That is just a Warning message, not an Error message :)

I haven't used the Webmin interface so I can't comment. BTW, the instructions for webmin, [http://doxfer.webmin.com/Webmin/NFSExports](http://doxfer.webmin.com/Webmin/NFSExports),  says that don't forget to click 'Apply Changes' on the main NFS exports screen to activate the exports.
Do you remember doing that step ?

**Edit**: I installed Webmin for verification and was able to setup NFS exports. Just keep in mind to press 'Apply Changes' and the exports should be available/unavailable immediately.
This can be verified using 'sudo exportfs' command

---

### Post by wt9bind on 2013-03-04
Yes. That is the button I was reffering to.

---

### Post by luvshines on 2013-03-05
> **wt9bind said:**
> Yes. That is the button I was reffering to.

Well !! It works for me :)
Anyways, you may try again from webmin and check

---

