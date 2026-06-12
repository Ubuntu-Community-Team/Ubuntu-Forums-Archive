---
title: "Cannot edit/delete/change /etc/resolv.conf"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by DrHogie on 2009-07-13
I'm posting here after searching/giving up on fixing this for months.  I've installed Ubuntu Server 8.04 on an older Dell blade server and have it configured to a static IP.  I am running apache, bind, and dhcpd on it for local services.

I originally had the server IP hard-coded to 10.15.72.30, and pointed /etc/resolv.conf to this address for DNS purposes (using the local DNS server).  Since then, I had to change the address to another IP address . . . but now I cannot change /etc/resolv.conf.  I have sudo'd to the root account, and still cannot edit the file or delete it.

I was under the impression that root can edit/delete any file on the system . . . is there some different way I'm supposed to edit this information?  Or is there some secret process that's keeping me from editing this file?

Hopefully someone can help me with this -- I've been pulling my hair out for ages with this problem!

Thanks in advance,
Josh

EDIT:
Just to show some examples of my problem:

root@chtserver:/etc/network# sudo chmod 774 /etc/resolv.conf
chmod: changing permissions of `/etc/resolv.conf': Operation not permitted

root@chtserver:/etc# rm /etc/resolv.conf
rm: cannot remove `/etc/resolv.conf': Operation not permitted

EDIT2:
Aaaaaand I just solved my own problem . . . but I'm still a bit confused by it.  I've used Linux since the RH5.2 days, and I've never seen the "chattr" command.  I had to run "chattr -i /etc/resolv.conf", which then allowed me to edit the file.  WHy does Ubuntu block write access to this file, and what service does this?

---

### Post by ibutho on 2009-07-13
What are the permissions on the file? Check by running
```
ls -l /etc/resolv.conf
```
As the normal user, what happens if you do
```
sudo vim /etc/resolv.conf
```

---

