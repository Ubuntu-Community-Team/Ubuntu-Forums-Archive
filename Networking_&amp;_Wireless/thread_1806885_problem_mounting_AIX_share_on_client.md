---
title: "problem mounting AIX share on client"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by schnoogge on 2011-07-18
I have a strange situation and can't figure out why all of a sudden I can't mount the AIX share on my ubuntu desktop client. I am constantly getting mount(2) Permission denied. 

root@nb11938:/boot/grub# showmount -e gmzut001
Export list for gmzut001:
/home/st_software    (everyone)
/smt-repo            (everyone)
/nfs_camera/RZ       rzcamera
/oracle_stage        (everyone)
/sysmgt/tmp          (everyone)

gmzut001 is the aix machine


root@nb11938:/boot/grub# mount -t nfs -v -o vers=3  gmzut001:/sysmgt/tmp /keepass
mount.nfs: timeout set for Mon Jul 18 15:46:59 2011
mount.nfs: trying text-based options 'vers=3,addr=163.161.14.39'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 163.161.14.39 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying 163.161.14.39 prog 100005 vers 3 prot UDP port 45758
mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting gmzut001:/sysmgt/tmp


message when I try a mount -v


in /etc/exports
/sysmgt/tmp -public,sec=sys:krb5p:krb5i:krb5:dh,rw

Funny enough with a sun nfsshare I have no problem but have the same problem when trying to mount with other AIX boxes

Thanks in advance 
Mick

---

### Post by jmoorse on 2011-07-18
Mick, is this share mounted on any clients?  Has it ever been mounted? 

Error message indicates the issue *may* be with the AIX server, but I don't want to leave you with just that because that isn't very helpful now is it?

---

### Post by schnoogge on 2011-07-19
Strange is this AIX server is a share for many systems as it is like our infrastructure server with software and oracle software on it . I don't have another Ubuntu to tes tti with. However I am able to mount it on a sun machine with the nfs vers. 3  mount -o vers=3  ......

---

### Post by jmoorse on 2011-07-21
I have only worked with Solaris and AIX a few times, so I am a bit out of my element.  

I did find this little nugget, don't know if it still applies but should be easy to test:

> 
The NFS server must be able to reverse-resolve the client IP address


What does a 'host' on the IP addresses of a working solaris client return?  And the ubuntu box?

---

