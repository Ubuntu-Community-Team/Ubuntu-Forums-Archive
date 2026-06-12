---
title: "NFS mounting error"
date: 2012-07-19
forum: Networking &amp; Wireless
---

### Post by akkarris on 2012-07-19
I have recently embarked on an endeavor to set up an nfs server on one of my three computers to get a backup system going. I have been following this guide:
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
I have installed the packages: sudo apt-get install nfs-kernel-server nfs-common portmap
configured it and reset it i have also configured my /etc/exports with this code:
/home/connor/Backup ip-address(rw,async)

I have also configured my /etc/fstab file with this code:
ip-address:/home/connor/Backup nfs rsize=8192,wsize8192,timeo=14,intr,noauto

I created the file using: 
sudo mkdir /home/connor/Backup

and then I tried to mount the file using:
sudo mount ip-address:/home/connor/Backup

and it says it says:
> mount: mount point nfs does not exist
any help would be greatly appreciated!

---

### Post by steeldriver on 2012-07-19
Hi, the error seems to be because it is trying to use the filesystem type (nfs) as the mount point - I think you need to add the mount point (that you created with mkdir) as the 2nd field in the fstab entry:

```
ip-address:/home/connor/Backup **/home/connor/Backup** nfs rsize=8192,wsize=8192,timeo=14,intr,noauto
```

---

### Post by akkarris on 2012-07-19
i tried what you recommended and it only gave me another error
> mount.nfs: an incorrect mount option was specified

---

### Post by steeldriver on 2012-07-19
Sorry I don't know much about nfs mount options - the only option I have to use for my nfs mounted NAS is nolock

Where did you get that option list from?

---

### Post by akkarris on 2012-07-19
i got the list of options from the nfs setup link in the original post.

---

### Post by steeldriver on 2012-07-19
just noticed you have a typo in your option list

```
ip-address:/home/connor/Backup nfs rsize=8192,wsize[COLOR=Red]**=**[/COLOR]8192,timeo=14,intr,noauto
```

---

### Post by akkarris on 2012-07-19
good eye!
however even with the typo fix it still says 
> mount: mount point ip-address:/home/connor/Backup does not exist :(

---

### Post by akkarris on 2012-07-19
Also when i try the more simple version i get another error
sudo mount /home/connor/Backup
mount.nfs: access denied by server while mounting ip-address:/home/connor/Backup

---

### Post by steeldriver on 2012-07-19
OK well I guess that's progress at least ;)

Do you have nfs-common installed on the client machine as well as on the server? what does 

```
showmount -e *your-server-ip*
```return?

BTW I re-mounted my nfs dir using your options and it worked fine:

```
sudo mount -t nfs -o rsize=8192,wsize=8192,timeo=14,intr,noauto 192.168.1.127:/homes /mnt/nas-01/home
```(you might want to try mounting directly from the command line to start - so you don't need to keep editing and reloading /etc/fstab - once you have it nailed you can put it in the file)

---

### Post by akkarris on 2012-07-19
it is still denying my mount...
here is the result of the showmount command
> 
:/$ showmount -e 172.16.11.**5
Export list for 172.16.11.**5:
/home/connor/Backup 172.16.11.**6 


---

