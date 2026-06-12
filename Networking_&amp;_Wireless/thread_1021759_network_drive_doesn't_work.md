---
title: "network drive doesn't work"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by dancer58 on 2008-12-25
Linux asus 2.6.27-11-generic #1 SMP Fri Dec 19 16:29:52 UTC 2008 i686 GNU/Linux

Ubuntu Intrepid  (up to date)

I have a network drive attached to a netgear router. I can see the network drive and mount all the folders but when I click on the mounted folder nothing shows and the folder unmounts. After that I can no longer see the folders when I click on the network drive untill after I reboot.
both laptop and desktop do the same thing
Network drive is formated fat32

Everything works OK in WinXP

---

### Post by dmizer on 2008-12-25
What is the make and model of your NAS device?

---

### Post by dancer58 on 2009-01-03
The network drive is:

ATEC NS-384S 3.5-inch LAN Disk IDE to USB 2.0/RJ-45 Ethernet NAS Hard Drive

---

### Post by dmizer on 2009-01-04
Well, unfortunately I can't find much on your NAS device. I was hoping that it might support NFS or FTP, but I can't tell for sure.

So, unless you see indications that NFS or FTP is supported, you'll have to rely on CIFS instead. To mount the NAS device with CIFS, please see the second link in my sig.

---

### Post by dancer58 on 2009-01-06
I have been trying different things.
storage does have a setting fot SMB and FTP
This is what I have found so far:

I get two different errors, the first is a error box and the second is a segment fault

1.   Could not display "smb://storage-4444/public/".            (public is a folder with data in it)
     There is no application installed for this file type

2.   Jan  6 12:16:10 asus kernel: [  129.830075] gvfsd-smb[4409]: segfault at 0 ip b79285b3 sp b7387c8c error 4 in libc-2.9.so[b78b1000+15c000]
Jan  6 12:19:24 asus kernel: [  323.872778] gvfsd-smb[4482]: segfault at 0 ip b78425b3 sp b72a1c8c error 4 in libc-2.9.so[b77cb000+15c000]


also I have to try to mount 2 or 3 times to get a mount
If I look at properties it shows no files in folder "public"

---

### Post by dancer58 on 2009-01-08
> **dancer58 said:**
> I have been trying different things.
storage does have a setting fot SMB and FTP
This is what I have found so far:

I get two different errors, the first is a error box and the second is a segment fault

1.   Could not display "smb://storage-4444/public/".            (public is a folder with data in it)
     There is no application installed for this file type

2.   Jan  6 12:16:10 asus kernel: [  129.830075] gvfsd-smb[4409]: segfault at 0 ip b79285b3 sp b7387c8c error 4 in libc-2.9.so[b78b1000+15c000]
Jan  6 12:19:24 asus kernel: [  323.872778] gvfsd-smb[4482]: segfault at 0 ip b78425b3 sp b72a1c8c error 4 in libc-2.9.so[b77cb000+15c000]


also I have to try to mount 2 or 3 times to get a mount
If I look at properties it shows no files in folder "public"


I found that the problem is in Nautilus and put in a bug report
Samba will mount:
sudo mount -t smbfs //192.168.1.11/PUBLIC /mnt/PUBLIC -o nounix

---

