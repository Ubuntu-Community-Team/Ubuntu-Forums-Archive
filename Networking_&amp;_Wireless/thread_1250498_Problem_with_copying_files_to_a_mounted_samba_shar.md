---
title: "Problem with copying files to a mounted samba share"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by Witchlight on 2009-08-26
I have a weird issue with Ubuntu 9.0.4. I have a Debian box that acts as a  file server thats been running for years setup with samba shares. I've always mounted the shares in the fstab of whatever I'm running on my desktop. Like this.

//192.168.*.*/sharename  /media/sharename smbfs auto,username=*******,passwd=******,uid=1000,umask=000 0 0

(yes I know I can handle the passwords in a more secure manner thats not the point right now)

In every other ver of Ubuntu all I was missing was to install smbfs and it worked perfectly.

With 9.0.4 the shares still mount fine and I can play music from the server via the mounted share fine, I can copy files FROM the server to the 9.0.4 box fine. However every time I try to copy a file from my desktop to the mounted share one of 2 things happen..either all my networking crashes horribly or the file transfer goes at ridiculousness slow speeds. 

Its not the debian box because its config has not changed and works with every other system this is the only one that has problems. Ideas/help please.

---

### Post by alenis on 2009-08-26
I had the speed problem with my DLINK DNS323 NAS box. I discovered that the cause was the network adapter in the client, which was badly supported by the kernel. I don't remember which adapter was that, but installing a new ethernet card solved all problems.

---

### Post by Witchlight on 2009-08-26
Ya I don't know...I've always used the same card and never had a problem with it before. Only had this since 9.0.4. I got mad enuff at it I switched back to gentoo for awhile. It worked great on that.

I'll check the driver again. Maybe that will help.

---

### Post by zman58 on 2009-08-26
Instead of using smbfs you should be using cifs. They are not the same (alias). smbfs has been depricated and will present problems including performance and file size limitations.

You can try removing the fstab entry, then just use the Ubuntu desktop to attach "Places - Connect to Server".
You will probably notice a difference right off the bat.

I use a script which calls mount.cifs to attach to my server share. You can download this from my website for reference or use. just download the samba client scripts tar file from:
[http://home.roadrunner.com/~zahorec/gatekeeper.html](http://home.roadrunner.com/~zahorec/gatekeeper.html) 

!! also look here for fstab details with cifs.  Very good example:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by dmizer on 2009-08-26
Please see the 2nd link in my sig. It includes troubleshooting.

Also, it would be helpful to see the smb.conf file from the Debian server, not because I think it is wrong but because it will assist in troubleshooting the client.

---

### Post by Witchlight on 2009-08-26
I'm quite aware of the diff between cifs and sambafs. I'm not in the mood to rework something that works perfectly.

Alenis was on the right track. Switching Drivers has solved it. I needed a diff Mad-wifi driver.

Cheers.

---

### Post by zman58 on 2009-08-27
> **Witchlight said:**
> I'm quite aware of the diff between cifs and sambafs. I'm not in the mood to rework something that works perfectly.

Alenis was on the right track. Switching Drivers has solved it. I needed a diff Mad-wifi driver.

Cheers.

Glad to hear you have it running Witchlight and of course you can keep using smbfs, but....

Keep in mind that smbfs does not work particularly well as compared with cifs. I have experienced problems with smbfs when stressing the file system. When you copy large multi-GB files smbfs will fail because of a hard upper limit (i think 4 GB). Smbfs does not perform as well (not smooth and much slower at transfer) and it is no longer actively maintained. I have actually experienced hangs using smbfs, where cifs has worked flawlessly for me. This advice is consistent to recommendations by the samba team.

You should not have to change anything on your server to switch to cifs. Just attach to the shares using a cifs entry in fstab for the mount point on the client instead of the smbfs entry and you will see a noticeable improvement in resource utilization and throughput.

Have fun.

---

