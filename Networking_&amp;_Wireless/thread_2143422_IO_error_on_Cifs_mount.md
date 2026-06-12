---
title: "IO error on Cifs mount"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by msknight on 2013-05-09
Hi Folks,

Upgraded from 12.0 to 13.04 (via 12.10) - 64 bit AMD G-T56N 1.65Ghz. cifs-utils are installed.

Server is OpenIndiana publishing a CIF share. The wsize force is necessary to get around a packet incompatability.  

Since upgrading the client, I now get an IO error and I'm not sure how to proceed with this.

michelle@FitPC3:~$ sudo mount //192.168.0.2/mirror /home/michelle/Documents/mirror -o user=username,password=password,file_mode=0777,dir_mode=0777,wsize=65536
mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

---

### Post by wildmanne39 on 2013-05-09
Input/output error means it is having trouble reading the drive possibly because of corruption or failure.

---

### Post by tgalati4 on 2013-05-09
The wsize might be too big.  Check your cabling, try switching cables and ports on your router.  All it takes is one bad connection to mess up file shares.

---

### Post by msknight on 2013-05-09
No joy. 12.04 works fine. 13.04 doesn't want to know. Cables, etc. checked.

---

### Post by Metaluna on 2013-05-09
For what it's worth, I'm having the exact same problem mounting CIFS shares from an OpenIndiana server.  I'm using a clean install of 13.04 though.  12.10 worked fine.

---

### Post by msknight on 2013-05-14
So ... no one has any insight in to this?

---

### Post by redmk2 on 2013-05-14
> **msknight said:**
> So ... no one has any insight in to this?

It's unfortunate that the error is reported as an I/O error.  It's not really.  it's a mount error.  See the part in red```
[COLOR="#FF0000"]mount error(5)[/COLOR]: Input/output error
[COLOR="#FF0000"]Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)[/COLOR] 
```

This may be do to incompatibility in the Solaris version of CIFS.  They roll their own (It's not Samba at all).  Try a more basic mount command.

---

### Post by illegalname on 2013-06-04
Found a solution to this elsewhere -- which I then lost, and can't find it.  Found this thread, which is precisely my problem (Solaris-based CIFS server).  My mounts worked with 12.whatever, failed when I upgraded to 13. 

The solution is to add "sec=ntlm" to your list of options in the mount command.  I haven't looked into what's happening in detail, but presumably the Windows authentication default changed, and now we have to specify using ntlm.

---

### Post by jamesisin on 2013-06-23
I'm seeing this same error and the sec=ntlm is not helping any.

[http://ubuntuforums.org/showthread.php?t=2156972](http://ubuntuforums.org/showthread.php?t=2156972)

---

### Post by T.J. Crowder on 2014-05-22
Another way you can get this exact error is if the hostname you give in fstab isn't the same as the hostname of the server (e.g., you have an alias for it, an entry in /etc/hosts, whatever). For example, if the server's name is "foo" and you have an entry in it in /etc/hosts (for example) giving it the alias "bar", an attempt to mount //bar/share will fail while mounting //foo/share will succeed, even though the names resolve to the same machine.

-- T.J.

---

