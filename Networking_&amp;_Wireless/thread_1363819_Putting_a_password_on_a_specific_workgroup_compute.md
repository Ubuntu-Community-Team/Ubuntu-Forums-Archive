---
title: "Putting a password on a specific workgroup computer?"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by kloot on 2009-12-24
My friend keeps his shared files password protected (ie in Windows, when you go to the "View workgroup compuers" menu and you double click on his computer, it asks for a password), and I was wondering if there is a way to protect my linux computer aswell. I'm running Ubuntu 9.10.

Right now anyone can boot in windows, connect to the network, and delete/move my files at will. Quite depressing.

EDIT: I was able to disable access to my folders from "My Network Places" by doing "sudo smbpasswd -a ...", but people can still go to the list of workgroup computers, and open my files.
Sorry guys, im the ultimate ubuntunuub.

---

### Post by Iowan on 2009-12-25
Are your shares set up via Nautilus or are they configured through */etc/samba/smb.conf*?  The smb.conf lets you set "valid users=" option (dunno about the Nautilus way...).

---

### Post by Morbius1 on 2009-12-25
As the compliment to Iowan's post, if your using the nautilus share method, did you change the parameters?

Open **Terminal**
Type **net usershare info**

It should look something like this if you require authentication:
> path=/Data
comment=
usershare_acl=Everyone:F,
guest_ok=n
If the last line is: guest_ok=y , then you need to go back into Nautilus and disable the guest access box.

---

### Post by kloot on 2009-12-25
Iowan - I'm using Samba. The valid users line is "valid users = %S" I just change %S to whatever computer I want to have access to?
Morbius1 - I'm not using the nautilus share method. Thank you nevertheless. :)

EDIT: Sorry, another question :$ - I have set up two networks - how do I share files to one of the networks, without sharing it to the other one too.

---

### Post by Iowan on 2009-12-25
Where is the "valid users = %S" line? I found [this]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/131419") bug. I'm not really familiar with some of the variables, but [this]("http://www.rtr.com/winpak/Documentation/smb_conf.htm") page suggests %h is hostname... but username would seem to be more secure - otherwise, anyone logged onto a specific computer would have access.

---

### Post by Morbius1 on 2009-12-25
I'm fairly certain the "valid users" refers to user names ( the ones you set up using smbpasswd ) not computer names and unless you wanted it set as a global setting ( which you can certainly do ) it's usually set at the share level.

For example if you created a share in smb.conf then the "valid users" line would look like this:

> [myshare]
    comment =
    path = /path/to/share
    [COLOR=Blue]valid users = mary john[/COLOR]
    public = no
    writable = yes


---

### Post by 98cwitr on 2009-12-25
by default, at least for me, all samba shares are disabled in 9.10. When i run *net usershare info* I get "net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing"

---

### Post by ant2ne on 2009-12-25
What are the file system permissions for the directory where the files are shared?
In a terminal type
```
chmod validuser:validgroup -R /path/to/share
chown 751 -R /path/to/share
```

then, in the smb.conf, in the shares section you need a line like
```
create mask = 0751
```

this will give full control for validuser and read only for valudgroup and no access (well... maybe browse folder) for other users. Of course, you'll still need to set up these users. and groups

see signature

---

