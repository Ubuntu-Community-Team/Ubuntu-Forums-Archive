---
title: "connecting via samba to Windows share"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by rawlins02 on 2010-05-06
I'm able to connect to a networked Windows machine and its shares using the Places -> Network -> Windows network interface, but unable to do so using smbclient at terminal command line.  I can see the shares using:

smbclient -L //server -U username

But when issuing the command:

smbclient //server/service -U username

I get:

domain=[server] OS=[Windows Server 2003 R2 3790 Service Pack 2] Server=[Windows Server 2003 R2 5.2]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

The share name has spaces, like

lab raid root share

I use \040 to fill in the spaces. This problem must be something fairly simple if I can connect via the Places GUI but not through the command line.  Thanks in advance for suggestions.

---

### Post by Charlietje on 2010-05-06
Try using this command:

```
sudo mount -t cifs //netbiosname/share /path/to/mountpoint/ -o username=***,password=***
```

---

### Post by rawlins02 on 2010-05-06
I assume /path/to/mountpoint/  is /mnt/ntserver which I set up on my linux box?  So here's a depiction of attempt:

sudo mount -t cifs //netbiosname/share /mnt/ntserver -o username=username,password=xxxxxxx

and the result:

mount: wrong fs type, bad option, bad superblock on //netbiosname/share,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



> dmesg | tail 

CIFS VFS: cifs_mount failed w/return code = -22


But I WAS just successful in using smbclient after placing the share name is quotes. Now would like to mount the share like you suggest.

---

### Post by Charlietje on 2010-05-07
You need to install the packages smbfs.


```
sudo apt-get install smbfs
```

---

### Post by rawlins02 on 2010-05-07
Thanks. I've been able to execute smbmount after installing smbfs.  

Now need to figure out why I'm getting permission denied when attempting to scp files from my linux box to my share account on the Windows machine.  I'm assuming it's got to do with permissions set over on the Windows server and not anything to do with the linux side or smbmount, etc.

---

### Post by Charlietje on 2010-05-07
you cannot use scp with samba.
scp uses ssh to copy files

---

### Post by rawlins02 on 2010-05-07
cp does not work either.  But, after mounting the share through Places -> Network -> Windows Network GUI, I AM able to copy a file to my share account on the Windows machine.  I'd intended on backing up my linux box to my account on the Windows share. If rsync is out, is a cp command the best way? I'm assuming here that backing up my linux account to the Windows share is possible.

---

### Post by Charlietje on 2010-05-09
for samba sharing:
A little how to

**Installing**

```
apt-get install samba samba-common smbfs smbclient
```

**Configuration**
Config file: /etc/samba/smb.conf

```
[global] 
  workgroup = CARL 
  server string = %h server (Samba, Ubuntu) 
  dns proxy = no 
  log file = /var/log/samba/log.%m 
  max log size = 1000 
  syslog = 0 
  panic action = /usr/share/samba/panic-action %d 
  security = user 
  encrypt passwords = true 
  passdb backend = tdbsam 
  obey pam restrictions = yes 
  unix password sync = yes 
  passwd program = /usr/bin/passwd %u 
  passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdate\ssuccessfully* . 
  pam password change = yes 
  map to guest = bad user 
  usershare allow guests = yes

[homes] 
  comment = Home Directories 
  browseable = yes 
  writable = yes 
[data] 
  comment = Data Share 
  path = /data/ 
  browsable = yes 
  valid users = carl 
  read users = carl 
  write users = carl writable = yes 
  writable = yes 

```

**Add user to samba**
```
smbpasswd -a carl
```


**Mount share**
```
smbmount //192.168.1.2/homes /home/carl/Desktop/share -o username=carl
```


After you have done that,
Your share is mounted, and you can see it like a local folder.

Regards

---

### Post by dixcuxx on 2011-07-27
> **Charlietje said:**
> for samba sharing:
A little how to

**Installing**

```
apt-get install samba samba-common smbfs smbclient
```

**Configuration**
Config file: /etc/samba/smb.conf

```
[global] 
  workgroup = CARL 
  server string = %h server (Samba, Ubuntu) 
  dns proxy = no 
  log file = /var/log/samba/log.%m 
  max log size = 1000 
  syslog = 0 
  panic action = /usr/share/samba/panic-action %d 
  security = user 
  encrypt passwords = true 
  passdb backend = tdbsam 
  obey pam restrictions = yes 
  unix password sync = yes 
  passwd program = /usr/bin/passwd %u 
  passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdate\ssuccessfully* . 
  pam password change = yes 
  map to guest = bad user 
  usershare allow guests = yes

[homes] 
  comment = Home Directories 
  browseable = yes 
  writable = yes 
[data] 
  comment = Data Share 
  path = /data/ 
  browsable = yes 
  valid users = carl 
  read users = carl 
  write users = carl writable = yes 
  writable = yes 

```

**Add user to samba**
```
smbpasswd -a carl
```


**Mount share**
```
smbmount //192.168.1.2/homes /home/carl/Desktop/share -o username=carl
```


After you have done that,
Your share is mounted, and you can see it like a local folder.

Regards

Then I can enter password of the windows user when I try to open the share folder?

---

