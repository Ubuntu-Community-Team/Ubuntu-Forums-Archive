---
title: "NFS mount on /home/user too Slow sometimes"
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by Valpskott on 2012-03-25
So, I bought a ReadyNAS and decided to mount it to my users home directory, this is done via NFS (in fstab) on boot.

More often than not, GDM and autologon finnishes before my home directory is mounted which messes things up. I made GDM wait 20 seconds before autologon, but it still messes up sometimes.

My guess is it's due to not getting an IP from my router in time. Anyways, is there a way to halt GDM and check for my NFS mount to be finnished before countinuing on with the startup of GDM?

---

### Post by agillator on 2012-03-25
Answer to your specific question: I don't know. However, a couple of thoughts for you. 

First, give your NAS a static ip. This can be done through you router, or should be able to be done in the NAS itself. In that case, be sure you assign an ip address outside the range of addresses you allow the router to assign.

Second, why NFS? And is that really how the NAS is set up? Mine is CIFS (NTFS). So I have an entry in my fstab: //xxx.xxx.xxx.xxx/dir /mnt/nas cifs owner,uid=xxxx,gid=xxxx,exec,sudo,user=xxxx,password=xxxx 0 0 and that seems to work for me. The password is obviously insecure, but we are not talking national security here.

---

### Post by Valpskott on 2012-03-25
All Computers + the NAS already has static ip's on my network.

I went with NFS mainly because I get about 10-15mb/s faster transfer than CIFS/SMB. Previus experience with CIFS/SMB has been unstable in my Ubuntu setups. But, I can't say NFS is all that stable right now. So, I'll try CIFS and see if it works any better, a lot has changed in my network, so, why not? :)

But I'd never go with NTFS since it's my home folder. To my knowledge the NTFS doesn't support Linux permissions.

---

### Post by Valpskott on 2012-03-26
So, I think I solved it myself by adding "bootwait" as an option on the mount line in fstab.

---

