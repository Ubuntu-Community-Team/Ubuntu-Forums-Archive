---
title: "Mounting multiple drives on a single samba shared folder - possible?"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by cilbuper on 2013-01-11
I want to mount 5 drives, let's say 
/home/name/share/dev1
/home/name/share/dev2
/home/name/share/dev3
/home/name/share/dev4
/home/name/share/dev5
I name the samba share "share"

I create a samba share in smb.conf and share the /home/name/share directory.  In my FSTAB, I use UUID to persistently mount the drives to location: /home/name/share/dev1, /home/name/share/dev2, /home/name/share/dev3, /home/name/share/dev4, /home/name/share/dev5/

In windows, I map the drive to //linuxserver/share and then input the credentials that I use to log into the server, username and password.  This works for mounting each drive folder individually through samba and windows but I can't get it to map the "share" folder. When I map, it just keeps asking me for the credentials over and over.  What is strange is that it should be the same credenitals as the rest of the drives that I mount singularly but when I mount the base folder that contains all the drives, it just doesn't work.

I'm doing this because i'm running out of drive letters in Windows for mounting drives (I have A-Z mounting - They need to add numbers in with it like A1-A9, etc).

Can anyone give any advice on this?

Thanks in advance!

---

### Post by luvshines on 2013-01-11
How have the shares been defined ?

---

### Post by cilbuper on 2013-01-11
> **luvshines said:**
> How have the shares been defined ?

here is a copy of my smb.conf file:

#======================= Global Settings ===================================== 
[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = ubuntu
security = user
map to guest = bad user
dns proxy = no
#============================ Share Definitions ============================== 
[Michael]
path = /home/michael 
browsable =yes
writable = yes
guest ok = yes
read only = no
#============================ Share Definitions ============================== 
[2TB]
path = /home/michael/2TB 
browsable =yes
writable = yes
guest ok = yes
read only = no
#============================ Share Definitions ============================== 
[1TB_A]
path = /home/michael/sdb1
browsable =yes
writable = yes
guest ok = yes
read only = no
#============================ Share Definitions ============================== 
[500A]
path = /home/michael/sdd1
browsable =yes
writable = yes
guest ok = yes
read only = no
#============================ Share Definitions ============================== 
[500B]
path = /home/michael/sde1
browsable =yes
writable = yes
guest ok = yes
read only = no
#============================ Share Definitions ============================== 
[1TB_B]
path = /home/michael/sdf1
browsable =yes
writable = yes
guest ok = yes
read only = no

---

### Post by luvshines on 2013-01-11
So when you try to connect to Michael share, you experience issues and if you try to connect to the ones below, it works ?

---

