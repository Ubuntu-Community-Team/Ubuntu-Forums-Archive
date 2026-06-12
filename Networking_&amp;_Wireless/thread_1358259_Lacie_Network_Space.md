---
title: "Lacie Network Space"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by PaulClarke on 2009-12-18
Hello

I am running KK and have purchased a Lacie Network Space 1tb HDD.

It works fine except for one problem.

If I mount folders from the drive via FSTAB the permissions are set for the root and I cannot save to them.  In a previous setup I used an old PC with a drive and had no problem mounbting folders from it.

The following is my FSTAB

proc            /proc           proc    defaults        0       0
UUID=ddcd8601-1fed-415a-9dc9-a5d12fedf45b /               ext3    relatime,errors=remount-ro 0       1
UUID=127f1060-b708-4991-ab2d-595fd53f4a95 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//192.168.0.112/openshare /home/paul/server cifs defaults,workgroup=workgroup,uid=000,auto,rw,password="",mode=0777 0 0
//192.168.0.112/openshare/moneydance /home/paul/moneydance cifs defaults,workgroup=workgroup,uid=000,auto,rw,password="",mode=0777 0 0
//192.168.0.112/openshare/genealogy /home/paul/genealogy cifs defaults,workgroup=workgroup,uid=000,auto,rw,password="",mode=0777 0 0

Ther Mode command is a new attempt to overcome this problem.

Regards

Paul

---

### Post by PaulClarke on 2009-12-21
Hello

worked this out.  UID should have been 1000

Funny how it always worked before upgrade to KK

Paul

---

### Post by rmotters on 2009-12-30
Paul, 

I have a LaCie NetowrkSpace drive and I have it automounting, using autofs.

This is how.

1) Install autofs, smbmount and winbind
```
sudo aptitude install autofs smbmount winbind
```
2) Allow WINS lookup by default, edit the file /etc/nsswitch.conf and change the line:
```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```
to
```
hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4
```
At this point you should be able to ping the networkspace by it's name.

3) Edit the /etc/auto.smb line to add mount options, change the line:
```
mountopts=""
```
to (in my case)
```
mountopts="-fstype=cifs,guest,rw,noperm"
```
4) Edit the auto.master file, to allow SMB file-system mounting, change the line:
```
#/smb      /etc/auto.smb
```
to:
```
/smb      /etc/auto.smb
``` 
N.B. You can change this mount point if you want, I have changed mine to /mnt/smb.

5) Restart autofs
```
sudo service autofs restart
```
At this point you should be able to get the drive automatically mounted by just typing:
```
ls -l /smb/networkspace/openshare
```
If this is successful then all you need to do is create symbolic links for your data. In your case this would be:
```
ln -s /smb/networkspace/openshare /home/paul/server
ln -s /smb/networkspace/openshare/moneydance /home/paul/moneydance
ln -s /smb/networkspace/openshare/genealogy /home/paul/genealogy

```
The only problem I found was that Ubuntu kept losing the networkspace, if the DHCP address changed. 

I solved this by nailing down the DHCP address in my router, you could also give it a permanent IP Address.

---

