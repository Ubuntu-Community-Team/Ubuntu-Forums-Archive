---
title: "Updated to raring and one share won't mount?"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by twinturbotom on 2013-05-21
I updated my system from 12.10 to raring.  For some reason a share from my /etc/fstab refuses to mount!  I've spend quite a bit of time on this forum and google attempting many solutions frantically; probably now creating more problems!

I mount an apple time capsule to /media/time_capsule in my /etc/fstab like this:

```
//main.local/Data /media/time_capsule cifs noauto,credentials=/home/USER/.netcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

I can successfully ping "main.local" and the IP address.

When attempting to run "sudo mount -a" I receive mount error(22): Invalid argument or mount error busy or in progress... (not sure why errors change on new reboots!)

At one point I was able to mount using nautilus "connect to server".  But now that gives me an error like "Only root can mount".

I'm a bit lost on how this update has stopped this share from mounting (others have been working fine).  Any thoughts / direction / diagnostic tools?

I also recieve this error these days and am going to chase that down now; maybe related?
pciehp 0000:00:1c.4:pcie04: Device 0000:02:00.0 already exists at 0000:02:00, cannot hot-add

Thank you for the mind share!

---

### Post by twinturbotom on 2013-05-21
So I rebooted, deleted my fstab line and retyped it from scratch... no changes as far as I can tell (maybe added a space or two?) but now things are WORKING!  not really sure what I changed.  

Thanks!

---

### Post by twinturbotom on 2013-05-24
rebooting and not working again!!! this is frustrating... never had this issue with older distributions!  I'm now installing wireshark and attempting to diagnose.  

smbtree shows server with name and I can ping IP, not name... seems like name resolution is messed up somewhere here....  
any thoughts?  My web browers as 12 tabs (literally) of forum / google advice for cifs diagnostics, I'm trying them all...no luck!

---

### Post by twinturbotom on 2013-05-24
Unable to find suitable address. for sudo mount -a.  
and attempting to connect with nautilus yields: mount: only root can mount //mainTC.local/Data on /media/time_capsule
> 

smbtree output:
        \\MAINTC                        mainTC
                \\MAINTC\IPC$  



This works: > smbclient //mainTC.local/Data -U USER%PASS

I thought smb and cifs in fstab was the same thing.... I'll keep digging....  Thoughts?

---

### Post by twinturbotom on 2013-05-25
I added the sec=ntlm option from: [http://ubuntuforums.org/showthread.php?t=2139090](http://ubuntuforums.org/showthread.php?t=2139090)

working! YAY... I did try that before!  oh well....  

I'll keep digging!

---

