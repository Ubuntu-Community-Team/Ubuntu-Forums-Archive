---
title: "SMB Mount size 78 MB?"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by mac666 on 2010-01-07
Hey
I have mounted a SMB hardvare drive that works flawless if i go by the adress:
**smb://freenas/share**

But if i mount it to **/media/share** the size is 78 MB.
The real size is 1TB.
Still, if i go to **smb://freenas/share**, the size is real.

This is my fstab line that mounts it:
[HTML]//freenas.local/share /media/share smbfs credentials=/home/mac/.smbcredentials,uid=mac,gid=users 0 0[/HTML]

Any ideas? :(

---

### Post by johnson.d on 2010-01-08
Can you post the output of mount command in your client machine and also specify the tool used to browse through the address smb://freenas/share ( Nautilus? )?

---

### Post by mac666 on 2010-01-08
> **johnson.d said:**
> Can you post the output of mount command in your client machine and also specify the tool used to browse through the address smb://freenas/share ( Nautilus? )?

No Specific output:

```
mac@turd:~$ sudo mount -t smbfs //nasaret.local/share/Lager2 /media/Lager2 -o uid=mac,gid=users
Password: 
mac@turd:~$ 
```
same with cifs instead of smbfs
```
mac@turd:~$ sudo mount -t cifs //nasaret.local/share/Lager2 /media/Lager2 -o uid=mac,gid=users
Password: 
mac@turd:~$ 
```

I browse the drive with nautilius.

---

### Post by johnson.d on 2010-01-21
I have simulated the same setup and have tried mounting a freeNAS share and i get the following results

When mounted the folder using the following command:

mount -t cifs //freenas.local/share /mnt/share -o uid=xxxxxx,dom=WORKGROUP

It gets mounted seamlessly and shows the exact size while using the command $ df -h and getting the following details:

//freenas.local/share 1.5G 42M 1.4G 4% /mnt/share

When mounted in nautilus using the url smb://freenas.local/share and when i see the properties by right clicking on the folder "share" it shows the following details

Contents: 6 items totaling 41.4 MB

Free space: unknown
0 bytes used
0 bytes free

Please check if this matches your findings.

---

### Post by mac666 on 2010-01-23
Hey

What you need to do is:

Mount the Drive, not the share point.

Etc:

If you have a mounted drive on /mnt/share/drive1

Mount that one, instead of just mounting share..

Go for it!

---

### Post by johnson.d on 2010-01-25
I am afraid I don't understand your setup clearly. Can you explain it in more detail, possibly listing the steps you are following in both scenarios (using Nautilus and the console)?

---

