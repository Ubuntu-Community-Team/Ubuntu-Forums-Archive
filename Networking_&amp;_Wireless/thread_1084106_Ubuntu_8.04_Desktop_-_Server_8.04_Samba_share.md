---
title: "Ubuntu 8.04 Desktop - Server 8.04 Samba share"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by marlin9800 on 2009-03-01
Good evening all, I have resurrected an old desktop of mine, installed Ubuntu server 8.04 on it, threw on an USB HDD and setup Samba. My desktop is running Ubuntu 8.04 desktop and my wife has a PowerBook G4 running OS X 10.4.11.

I used the command sudo smbpasswd -a username (on the server) to create a login and password and that works great with the MAC but for some reason when ever I attempt to connect using my desktop, I get,

"Unable to mount location"
"Failed to mount Windows share"

I know it is authenticating because if I misspell the password on purpose or use a made up username it just asks again. The smb.conf is very simple,

```
[global]
        workgroup = workgroup
[Media]
        path = /mnt/external
        read only = no
        guest ok = yes
```

Any idea why? Thank you

---

### Post by Iowan on 2009-03-01
How are you trying to connect from the desktop? My Gutsy box (7.10) seems to work better if I use Places>Connect to Server.

---

### Post by marlin9800 on 2009-03-01
I was using the 'Network' link, then selecting the 'server' then the share folder. I tried using the 'Connect to Server' and entered all information in; it placed a shortcut on my desktop to the share folder, but when I try to access it, same message,

"Unable to mount location"
"Failed to mount Windows share"

*added note* My windows box can pull it up just fine also.

---

### Post by marlin9800 on 2009-03-14
*update* I am currently on a Live CD of another distro based off kubuntu and I was able to connect to the share no problem.

---

### Post by marlin9800 on 2009-03-28
Well, I figured it out on my own. I was mounting with 

```
-o uid=1000,gid=100,utf8,dmask=027,fmask=137
```

at the end of the mount command, when I removed that, my ubuntu box sees it no problem. Can anyone tell me why or what those commands mean?

---

### Post by marlin9800 on 2009-03-28
Ok, new problem. Mounting the drive minus the "-o uid=1000,gid=100,utf8,dmask=027,fmask=137" lets my ubuntu box see it, but now my wifes laptop and my box can not write to it.

A little reading tells me that dmask applies to the dir and fmask applies to the files permissions. But how do I know what vaule to make them to allow writing?

---

### Post by marlin9800 on 2009-03-28
Ok I give up... not sure what I did but now it is working. Since I am the only one posting here I will just leave it alone and walk away. Thanks for reading!

---

### Post by fmw on 2009-03-30
You're not the only one reading.  I have the same mounting problem.  I'm about ready to give up and trash Ubuntu.

---

### Post by marlin9800 on 2009-04-02
> **fmw said:**
> You're not the only one reading.  I have the same mounting problem.  I'm about ready to give up and trash Ubuntu.

That isn't the correct attitude, there is always an answer, and I think I might know what helped.

1st thing is I am using that same command to mount that I started with
```
sudo mount -t vfat /dev/sdb1 /mnt/external -o uid=1000,gid=100,utf8,dmask=027,fmask=137
```
and it works as long as I also did 
```
sudo chmod -R 766 external/
```
(as you can see from the first command external my mount destination) and added
```
force user = %username%
```
to my smb.conf file. Then restart samba (I am guessing). I had to reboot whole damn server, 1st I rebooted samba and got no change; but next day I had a power outage and when I booted it was working.



Incase you want to see it, here is my whole smb.conf file.
```

[global]
        workgroup = workgroup
        encrypt passwords = yes
[Media]
        path = /mnt/external
        read only = no
        force user = %username%
        guest ok = yes
```

---

