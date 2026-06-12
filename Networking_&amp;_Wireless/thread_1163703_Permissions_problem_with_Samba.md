---
title: "Permissions problem with Samba"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by TideMan on 2009-05-19
I want to copy a file from my Ubuntu machine to BlueFront, an Xubuntu machine.  On the Ubuntu machine, I have a window open in the file browser pointing to: smb://bluefront/daisy/temp.  On BlueFront, I have done a chmod 777 on the temp directory, yet when I try to paste the file into the directory, I'm told I don't have permission.

Samba is working OK, the directory has all its permissions set to rwx.  I can see all the files in temp on BlueFront.  What have I missed?

---

### Post by dmizer on 2009-05-19
How did you configure file sharing on BlueFront?

---

### Post by TideMan on 2009-05-19
> **dmizer said:**
> How did you configure file sharing on BlueFront?

It's a good question.
I cannot remember.  I did it when I first set up Xubuntu and Samba.

---

### Post by dmizer on 2009-05-19
Well, let's start by posting the contents of this file: /etc/samba/smb.conf

---

### Post by TideMan on 2009-05-19
> **dmizer said:**
> Well, let's start by posting the contents of this file: /etc/samba/smb.conf

Uh, ohhhhh

> [daisy]
path = /home/daisy
available = yes
browsable = yes
public = yes
writable = no


I guess it needs to be writable= yes.
But how do I do that?
Do I just edit smb.conf?

---

### Post by dmizer on 2009-05-19
> **TideMan said:**
> I guess it needs to be writable= yes.
But how do I do that?
Do I just edit smb.conf?
Yup, just edit smb.conf like so:
```
gksudo mousepad /etc/samba/smb.conf
```
Make the change, save the file, and close mousepad.

Reboot your computer, or restart samba with the following command:
```
sudo /etc/init.d/samba restart
```

---

### Post by TideMan on 2009-05-19
OK, I've edited smb.conf and re-booted, but I am still cannot copy into BlueFront from the Ubuntu machine because of permissions.

What next?

---

### Post by dmizer on 2009-05-19
Add these lines to the top of your smb.conf file:
```
[global]
netbios name = BlueFront
workgroup = WORKGROUP
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
name resolve order = hosts wins bcast
```

Restart samba and test again.

If you still can't access, follow these steps on your Ubuntu computer: [http://ubuntuforums.org/showpost.php?p=7157868&postcount=12](http://ubuntuforums.org/showpost.php?p=7157868&postcount=12)

---

### Post by TideMan on 2009-05-19
You beauty!!! :p

That fixed it and I'm working now
Thanks very much.

---

